# Spatial Data — styling analysis (2026-08-31)

Live source of truth: `dev.landscapepartnership.org` — but unlike product, **live
ploneCustom.css (and base-*.css) carry NO rules for this view's selectors**
(`.spatialDetails`, `table.green`, `table.blue`, `.mute-label`). Every value below
was **measured as a computed style** on the live page (gis-planning sub-site) with
`getComputedStyle`, not extracted from a stylesheet rule. The live page renders the
label/value tables as compact plain small print with no table chrome; do not invent
decoration.

Implemented in `themes/_shared/scss/content-types/_spatial-data.scss`, scoped under
`body.portaltype-spatial_data` (underscore preserved in the normalized body class).

## Shared

| Selector | Measured live computed style |
|---|---|
| `.spatialDetails` | full-width div; **0.8em of the body size, line-height 1.5, color #000** (re-measured 2026-09-03 on parent 16px body → 12.8/19.2px, se-firemap → 12.8/19.2px, gis-planning 15.2px body → 12.16/18.24px; the 2026-08-31 "0.76em" was gis-planning's smaller body font, not a smaller ratio); no floats |
| `.spatialDetails` tables (`table.green` / `table.blue`) | no borders, no backgrounds — plain small print. Locally, Barceloneta table chrome must be neutralized (transparent backgrounds, border 0). Live cells have **0 padding**, which runs label and value together ("Publication Date2025"); local keeps 2px 8px as a deliberate, documented legibility deviation |
| `p.documentDescription` (lede) | Montserrat 1.08em / 500 / #666 / lh 1.5 (17.28px on parent & se-firemap, 16.4px on gis-planning) — same site-wide lede rule as project; lives in `_detail-layout.scss` scoped to product/project/spatial_data (added 2026-09-03) |
| `.imgleft img` | live emits the Plone-4 `image_preview` scale = 400×400 box (309×400 for these portrait maps); the Plone 6 template emits `@@images/image/preview` = 400px wide, unbounded height (400×517). `max-height: 400px; width: auto` reproduces live (added 2026-09-03) |
| `.mute-label` td | color #000; font-weight 400; 12.16px — plain text, no emphasis |
| image (`.imgleft` wrapper) | NOT floated on live despite the class name — no float rule shipped |
| `.visualClear` | clear both (Plone-4 helper emitted by the template) |

## Token-varying

None — nothing here is colored or branded; the small-print rendering is identical
everywhere the type appears.

## Site-specific

None.

## Markup divergences (local Plone 6 template vs live Plone 4)

`6custom/spatial_view.pt` emits `.spatialDetails` containing a `table.green` (Links:
data download / DataBasin / ScienceBase / metadata XML / associated project &
products) and a `table.blue` (Data Info: dates, data type, resolution, status,
creator org, additional docs, revision log), then an `.imgleft`-wrapped preview
image and `.visualClear`. Live shows the same compact label/value content with no
table chrome and the image un-floated, so the Plone 6 markup is styled to that
measured rendering rather than to any live stylesheet rule. No template changes
flagged.

## Listing displays

Not enumerated in this pass; blocked on the same layout plumbing recorded in
`product/css-notes.md` (custom section layouts absent from FTI `view_methods`,
per-folder layouts unimported). Listing styling for spatial_data is NOT yet
implemented.

## Verification

### Verification update (2026-09-03) — se-firemap + lp-parent-site

Phase 5 by integrator on burned-area-rasters-2025 and fire-history-metrics-2024
(se-firemap) and forest-change-loss and probability-of-development (lp-parent),
local 1660 admin vs dev 1440, plus 390. Before: lede plain body text (se-firemap's
theme even rendered it in Merriweather), `.spatialDetails` 12.16px/1.3 in #444,
preview image 400×517. After: every measured value equals live — lede
Montserrat 17.28/500/#666, details 12.8/19.2/#000, th #000, image 309×400.
Regression spot-check: gis-planning applcc-boundary now 12.16/18.24 (= live's
ratio on its 15.2px body) with the Montserrat lede live also shows; unchanged
otherwise. Remaining deltas: "Metadata XML" link absent locally on the parent-site
pages (import gap — field not populated); link colour and h1 top margin are theme
chrome; the navigation portlet column is chrome (stacks below content at 390).

### Verification update (2026-08-31)
spatial-applcc-boundary (gis-planning): .spatialDetails small-print label/value rows render borderless and compact, matching live; image un-floated as measured. No further deltas.
