# MinervA4

**One HTML file that turns Markdown — or a Word document — into a branded A4 PDF.**
No install, no build step, no server, no account. Double-click it and it works offline.

[Español](LEEME.md) · [User guide (EN)](playground/documents/template_guide_a4.en.md)

---

## Try it

1. Open **`MinervA4.html`** in your browser and press **See an example**.
2. Under **Brand**, load `style-guides/acme-corporativo-style.yaml`. Swap in
   `acme-editorial-style.yaml` and the whole document changes — headings,
   tables, footers and diagrams — without touching a single character of the
   Markdown.

Then try the real demo, which is what `playground/` is for:

1. Drop `playground/documents/template_guide_a4.en.md` on the window.
2. Add `playground/data/en/figures-Q3-2026.json`. The last chapters of the
   guide fill themselves in with those figures.
3. Point **Add an image folder** at `playground/images/`.
4. Now the interesting part: load `playground/data/en/figures-Q4-2026.json`.
   **Without editing a word of the text**, the figures change, so do the
   colours of the callout boxes, the verdict on the quarter and the
   recommendations at the end. Q3 met its target and Q4 did not, and the
   document knows it.

## What it does

- **Content comes in three ways.** A `.md` file, a **Word document** (text,
  headings, lists, tables and images come across; the styling comes from the
  brand), or pasted straight into the editor.
- **The brand lives in a YAML file.** Colours, typography, margins, cover,
  table of contents and footer — plus page orientation, presentation mode and
  the page background. The same text ships under one brand today and another
  tomorrow. With no YAML loaded, the tool uses its default values.
- **Figures are cited, not copied.** Load an `.xlsx`, `.csv` or `.json` and the
  document references the values. Drop in next quarter's file and everything
  rebuilds. A field picker walks the whole tree and writes the placeholders for
  you, including conditional sections and blocks repeated per row. Several
  sources can be loaded at once.
- **Page control from the text.** Page breaks, landscape turns, justification,
  callout boxes and multi-column blocks — each with a button in the editor
  toolbar.
- **Mermaid diagrams and KaTeX formulas**, recoloured to the brand palette with
  the contrast of each box checked.
- **Image size is declared where the image is used**: `{width=60%}`,
  `{width=320px}`, `{width=80mm height=40mm}`.
- **Six interface languages**: Spanish, English, French, German, Italian and
  Polish. The language of the interface and the language of the document are
  set separately, and the number format follows the document.

## What's in here

| Path | What it is |
|---|---|
| `MinervA4.html` | The tool. The only file you actually need. |
| `index.html` | A one-line redirect, so the folder opens on the tool. |
| `style-guides/` | Two example brand guides in YAML. |
| `logos/` | An example logo for the **Brand** panel. |
| `playground/documents/` | The user guide in three languages, plus loose examples. |
| `playground/images/` | Ten images, each in a different format. |
| `playground/data/` | The same figures as `.json`, `.csv` and `.xlsx`, in `es`, `en` and `de`. |

**Everything here is invented**: the brand is ACME, and there is not one figure,
name or address belonging to a real company.

### The guides

`playground/documents/template_guide_a4.{es,en,de}.md` are the single
demonstration document: each one explains the tool and, in its last two
chapters, demonstrates it live — figures wired to the data file, conditions, a
loop over rows, tables that fill themselves in, currency, and images at their
declared size. Open one with the tool itself: it was written to be read laid
out.

The three carry the same figures. Only the prose changes, so they can be read
side by side and you can watch the number format follow the language of the
document: `4.310.000` in Spanish and German, `4,310,000` in English, with
nobody configuring anything.

### The data

Each language and quarter ships in the three formats the tool reads:

| | what it demonstrates |
|---|---|
| `.json` | the whole book, with its three sets of data |
| `.csv` | what a spreadsheet exports: one table and that's it |
| `.xlsx` | a three-tab workbook, for the set picker |

Field names are **not translated** — `revenue`, `margin`, `on_time`: they are
the name of the datum, and the canonical syntax is English. What gets
translated is the values, which is what you read on the page.

### The images

Ten, and each one puts a different part of the layout engine to the test: that
a vector scales without pixelating, that a PNG with transparency lets the
background through, that a small seal is not stretched, that a large BMP does
not blow up the file, that AVIF — the newest format — gets in.

## Printing

Use **Print to PDF**, with margins set to *None*, scale 100 % and **background
graphics on**. The margins of the page come from the brand guide, not from the
browser.

## Privacy

Nothing leaves the machine. There is no network call, no analytics and no
account: the file reads what you give it in the browser and renders it there.
That is also why it weighs about 5 MB — Mermaid, KaTeX, the spreadsheet reader
and the fonts are all embedded.

## Your own brand

The style guides here use an invented brand. Copy either one and change the
colours and typefaces. Keep your company's real guide on your own machine:
`.gitignore` ignores `style-guides/private-*` and `logos/private-*`, so you can
work with it in this folder without publishing it by accident.

## Licence

MIT — see [LICENSE](LICENSE).
