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
| `.spatialDetails` | full-width div; font-size 12.16px = 0.76em at 16px root; line-height 1.3em; no floats |
| `.spatialDetails` tables (`table.green` / `table.blue`) | no borders, no backgrounds — plain small print. Locally, Barceloneta table chrome must be neutralized (transparent backgrounds, border 0, compact 2px 8px padding) to match |
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

Pending — integrator runs Phase 5.

### Verification update (2026-08-31)
spatial-applcc-boundary (gis-planning): .spatialDetails small-print label/value rows render borderless and compact, matching live; image un-floated as measured. No further deltas.
