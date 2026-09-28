# tabular_view — styling analysis (2026-09-27)

Live (Plone 4 `base.css` + ploneCustom `table.listing {font-size:95%}`):

| Selector | Live rule |
|---|---|
| `table.listing` | `border-collapse:collapse; border-left:1px solid #ddd; border-bottom:1px solid #ddd; font-size:95%` |
| `table.listing th` | `text-align:left; color:#666; background:#ddd; border:.1em solid #e7e7e7; border-style:solid solid none` |
| `table.listing td, th` | `padding:.5em 1em; vertical-align:top`; `td {border-right:1px solid #ddd}` |
| `table.listing tbody tr.odd td` | `background:#eee` |
| `table.listing a` | `border-bottom:none` (no underline) |

Shipped in `_listings.scss` under `body.template-tabular_view #content-core table.table`:
the same values applied over Bootstrap's `.table-striped` (whose stripes are painted
with `box-shadow` on the cells, so `box-shadow:none` + explicit odd/even backgrounds).

## Verification (2026-09-27)

bobscapes sightings reports (12 Files) at 1660 and 390: #ddd header band with #666
labels, #eee odd rows, #ddd vertical rules, 95% text, links without underline; at 390
the `.table-responsive` wrapper scrolls horizontally (Barceloneta stock, acceptable).
No live page with rows to compare pixel-for-pixel — rule-level parity only.
