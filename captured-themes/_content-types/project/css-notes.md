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
768px collapse).

## Token-varying / Site-specific

None.

## Markup divergences (local vs live)

Same family as product: keyword td lists are ul/li locally vs comma text live
(flattened in CSS, stray-space nit inherited); .product-box PROJECT PAGE block
depends on relations that did not import.

### Verification update (2026-08-31)

Phase 5 run by integrator: full-page compare local (1660, admin) vs live reference at 1440.
- project-arizona (wildland-fire): 65/35 grid, field h4 treatment, table.simple chrome + flattened keyword lists all render via _detail-layout.scss; matches live product-family layout. Remaining deltas: none type-specific.
