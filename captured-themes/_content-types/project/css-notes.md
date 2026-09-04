# Project — styling analysis (2026-08-31)

Live source of truth: dev's site-wide `ploneCustom.css` — identical on every
sub-site, so everything is **Shared (Layer 1)** and no Layer 2 override exists.

project_view.pt shares the product detail structure (.grid-container-65-35,
.main-block fields, .detail-block, table.simple, .product-box, .space10,
.visualClear) plus a .documentDescription lede (Barceloneta default treatment
matches live). All shared rules live in `_detail-layout.scss` (grouped
product/project/organization selectors); `_project.scss` is an intentionally
empty placeholder.

## Shared

Identical rule set to product — see `../product/css-notes.md` (grid, .introtext,
.field h4 16px/500, table.simple chrome, flattened td ul keyword lists,
768px collapse) — plus the rules below, found during the 2026-09-03 parent-site
run and added to `_detail-layout.scss` (product/project block). All measured with
`getComputedStyle` on dev at 1440:

| Element | Live computed | Barceloneta/local before | Rule added |
|---|---|---|---|
| `p.documentDescription` (lede) | Montserrat 17.28px / 500 / #666 / lh 25.92 / mb 17.28 | Open Sans 16px / 400 / #444 | `.documentDescription { font: 500 1.08em/1.5 Montserrat; color:#666; margin:0 0 1em }` |
| `.field label` ("Abstract:", "Project Status:", …) | 15px / 700 / inline | 16px / 400 / inline-block (Bootstrap reboot) | `.field label { display:inline; font-size:15px; font-weight:700 }` |
| `dl.captioned.image-left` | float left, 12.8px, margin 6.4px 12.8px 12.8px 0, width 400 (inline style) | centered (`mx-auto`; Barceloneta 6 only floats `picture-variant-*`) | `dl.captioned { font-size:.8em } .image-left { float:left; margin:.5em 1em 1em 0 }` |
| `dl.captioned.image-right` | float right, margin 6.4px 6.4px 12.8px | centered | `.image-right { float:right; margin:.5em .5em 1em }` |
| `dl.captioned dd` (caption) | 10.88px / #666 / width 360 of 400 | 16px / #444 | `dd { margin:0; padding:0 20px; font-size:85%; color:#666 }` |
| `table.simple th, td` | color #000 | #444 (theme body colour) | `table.simple { color:#000 }` |
| ≤768px: `dl.captioned` | un-floated, fills column (live 390 capture) | 400px float overflowing the 390 viewport | media block: `float:none; max-width:100%; margin:.5em 0 1em; img { max-width:100% }` |

The captioned-image rules are Plone-4 TinyMCE markup that also appears in stock
Document bodies site-wide; they sit in `_detail-layout.scss` for now and are the
first candidate to lift into `_shared/scss/_base.scss` when a non-detail type needs them.

## Token-varying / Site-specific

None.

## Markup divergences (local vs live)

Same family as product: keyword td lists are ul/li locally vs comma text live
(flattened in CSS, stray-space nit inherited); .product-box PROJECT PAGE block
depends on relations that did not import.

### Verification update (2026-09-03) — lp-parent-site

Phase 5 by integrator, three parent-site pages (kentucky-bayou, green-river,
wetland-classification) local 1660 admin vs dev 1440, plus 390 both sides:
- Before: lede, labels and captioned images were the only type-specific deltas
  (table above). After the `_detail-layout.scss` additions every measured value
  matches live exactly (`.documentDescription` 17.28/500/#666 Montserrat;
  `.field label` 15/700; `dl.image-left` float left 6.4/12.8/12.8/0;
  `dl.image-right` float right 6.4/6.4/12.8; caption 10.88/#666; td #000).
- 390: floated images un-float and fill the column, captions below — matches
  live 390 capture.
- Regression spot-check after the Layer 1 change: product natures-network
  (lp-parent) unchanged; project-arizona (wildland-fire) labels now bold like
  live, rest unchanged.
- Remaining deltas, all classified:
  - **Template divergence (lp.content sign-off):** sidebar table renders the raw
    `projectURL` as link text (live: "link"), so long URLs wrap the `th` column
    onto two lines; `startDate`/`endDate` render as "Jan 01, 2012 05:00 AM"
    (live: "January 01, 2012"); Organization/Project Leader cells are plain links
    (live: `ul li` with square bullet — flattened by design).
  - **Chrome (replication plan):** keywords viewlet renders Bootstrap outline
    buttons (live: grey "Filed under:" pills, centred); parent-site navigation
    portlet occupies a left column that live does not show on these pages;
    rich-text `ul li` bullets (live: square orange, 15.36px, 10px gap) are the
    site-wide list treatment, not project-specific.
  - **Capture note:** the wildland-fire theme scrolls inside
    `#visual-portal-wrapper`, so `fullPage` screenshots there stop at the
    viewport; scroll that element and take viewport shots instead.

### Verification update (2026-08-31)

Phase 5 run by integrator: full-page compare local (1660, admin) vs live reference at 1440.
- project-arizona (wildland-fire): 65/35 grid, field h4 treatment, table.simple chrome + flattened keyword lists all render via _detail-layout.scss; matches live product-family layout. Remaining deltas: none type-specific.
