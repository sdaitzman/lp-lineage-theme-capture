# folder_full_view — styling analysis (2026-09-27)

Live: `.item` blocks separated by whitespace, `h2.headline` in the theme heading style
(gis-planning: 28px light blue), 85% grey byline (`by … — last modified …`,
`Contributors: …`), description, then `.extra-info` (`margin-bottom:1em; overflow:hidden`
in ploneCustom) holding the child's body — for Files a `a.download-btn-orange`
("DOWNLOAD FILE", white on orange, uppercase) followed by the size in `.discreet`.

Local: Barceloneta `full_view_item` markup — `#content-core > .item` → `h1 > a.summary`,
`section#section-byline`, `p.lead`, `section#section-item.mb-5` containing the child's
own view (File: `.section-main` icon + filename + `.metadata` + Download button, then
`Contributors`). Implemented in `_listings.scss` under `body.template-folder_full_view`.

## Shared (Layer 1)

| Element | Live | Local before | Shipped |
|---|---|---|---|
| entry separation | ~2em whitespace | `section.mb-5` (3rem) only | `.item {border-top:1px #dedede; margin-top:1.5rem; padding-top:1.25rem}` (first entry without border); `#section-item {margin-bottom:1rem}` |
| headline | h2.headline, theme heading colour, no underline | h1 25.6px underlined green | `h1 {font-size:1.6rem; margin:0 0 .25rem}`, link no underline |
| byline | 85% #666 | 16px | `#section-byline {font-size:85%; color:#666; margin-bottom:.75rem}` |
| description | body size | `p.lead` 20px | `.lead {font-size:1rem; margin-bottom:.75rem}` |
| file block | left-aligned, orange uppercase button | Barceloneta centres `.section-main`; green theme button | `.section-main {text-align:left}`; `.btn` / `a.btn[href*="@@download"]` orange #f38b1a, white, uppercase, 600; hover #d9760f |

## Token-varying

Headline font/colour from the theme's heading style.

## Site-specific

None.

## Markup divergences (flagged to lp.content)

1. **One `h1` per child** — `full_view_item` promotes each child title to `h1`, so a
   folder with 5 files has 6 `h1`s. Live uses `h2.headline`. Heading-level change belongs
   in the template (or a `full_view_item` override in lp.content); CSS only sizes it.
2. **Description printed twice for Files** — `p.lead` from `full_view_item` plus the File
   view's own description. Live prints it twice as well (`.description` + `.extra-info
   .documentDescription`), so parity, but worth dropping one in the template.
3. The orange button label is "Download" locally vs "DOWNLOAD FILE" on live — text is
   template-owned; CSS uppercases it.

## Verification (2026-09-27)

gis-planning species list, local 1660 vs dev 1440 and 390 both sides: entries separated
by a 1px line with live-like rhythm; headline 25.6px theme colour, no underline; byline
85% grey; file block left-aligned with an orange uppercase DOWNLOAD button; contributors
under it. 390: single column, button full-width row. Deltas: the two template items above.
