# The Motivation–Cognition Loop — `index.html`

A single-page, self-contained essay arguing that motivation and cognition are
not two theories but **one loop described at two magnifications**: cognition
supplies the *shape* of a single thought (one mismatch, resolved one of two
ways), motivation supplies the *rate* (how many such mismatches get run per
unit time).

`index.html` is the built, publishable artifact. Open it in a browser — no
server, no build step, no network required.

---

## What's in this folder

| File | Role |
| --- | --- |
| `index.html` | **The page.** Built output, ~900 KB, fully self-contained (both images inlined as base64 data URIs). This is the file you open or deploy. |
| `the-motivation-cognition-loop.src.html` | **The source template.** Same page, but with `{{HERO}}` and `{{DIAGRAM}}` placeholders where the images go. Edit this, never `index.html`. |
| `build_motivation_cognition_loop_page.py` | Build script: substitutes the two placeholders with inlined image data. |
| `motivation_force_hero.jpg` | Masthead illustration — drive as magnitude without heading. Inlined as-is (JPEG keeps its own encoding). |

The second plate, `motivation_cognition_loop_diagram.png`, is rendered by
`motivation_cognition_loop_diagram.py` (in the project root; its output lands in
`NEW FILES/`). The build script quantises it to 256 colours on the way in —
lossless for the flat fills the figure uses, and much smaller.


## How the page is built

- **No JavaScript at all.** Static HTML and CSS; everything you see is layout
  and type.
- **One reading column** of serif prose (`66ch`), with the figures breaking out
  onto a dark plate whose background matches the diagram's own exactly
  (`--plate: #0b0e16`), so the figure has no visible edge.
- **Light and dark themes** via CSS custom properties — `prefers-color-scheme`
  for automatic, plus a `data-theme="light"` / `data-theme="dark"` override hook
  on `:root`.
- **A five-colour semantic palette**, used consistently in both the prose and
  the diagram:

  | Token | Colour | Means |
  | --- | --- | --- |
  | `--rate` | gold | drive — the rate term; force and tempo, no direction; spent every cycle |
  | `--core` | violet | the loop itself — one mismatch, one resolution |
  | `--act` | blue | pursuit — resolving by acting; at volume, divergent generation |
  | `--learn` | green | learning — resolving by updating; the only thing that accumulates |
  | `--prune` | red | the gap, and the pruning the world does to trials |

- **Fonts** from Google Fonts: Archivo (display), Source Serif 4 (prose),
  IBM Plex Mono (labels and terms). These are the page's only external request —
  without the network it falls back to Georgia / Helvetica / Menlo and still
  reads correctly.

## Page outline

- Masthead, hero figure, and the colour legend
- **The whole thing in one minute** — the argument in five numbered claims
- **The unified figure** (`#figure`) — the single-panel plate
- **1 · Why these are one theory and not two**
- **2 · The unit — one gap, two moves**
- **3 · Drive is a scalar, and that is the whole argument**
- **4 · Pursuit at volume becomes a search** — broad-spectrum generation; the
  environment prunes
- **5 · Updating accumulated becomes a structure** — heuristic abstraction;
  higher-order synthesis
- **6 · The asymmetric ledger** — drive is rented, structure is owned
- **7 · The correspondence, term by term**
- **8 · The four settings of one machine** — thrash, stall, flat, compounding
- **9 · Checks you can actually run** (`#checks`)
- **Source theories**

## Source theories

The page is a merge of three documents from the wider research corpus:

- `MOTIVATION EXPLORATION.md` — motivation as action throughput rather than
  feeling, and the four-phase divergent-to-convergent cascade. *Supplies the
  rate term.*
- `CLAUDE MAIN/Human Operation Model. General Mechanism.md` — the three
  components (engine, selector, held pattern) and the single mismatch event.
  *Supplies the shape term, with the time axis left blank.*
- `motivation cogition loop.md` — the hinge document: the claim that the two
  above are one loop at two zoom levels, plus the term-by-term correspondence.
  *Supplies the merge.*

## Editing notes

- Content and styling changes go in `the-motivation-cognition-loop.src.html`,
  then rebuild. `index.html` has ~900 KB of base64 in it and is not meant to be
  hand-edited.
- Keep `--plate` identical to the diagram's background colour. If you re-render
  the figure with a different background, update the token to match or the plate
  will show a seam.
- The two anchors `#figure` and `#checks` are the page's only stable link
  targets; don't rename them if anything links in.
