# Spatial Data — sample pages (captured 2026-08-31)

Full instance list at capture time: 100 spatial_data items (per
`@search?portal_type=spatial_data`; `content_review_links` lists only the first ~10).
Instances live under `/maps-data/…`; the sampled page sits inside the `gis-planning`
sub-site path prefix.

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| applcc-boundary | `/Plone/maps-data/gis-planning/map-products/foundational-maps-1/appalachian-lcc-boundary-file` | https://dev.landscapepartnership.org/maps-data/gis-planning/map-products/foundational-maps-1/appalachian-lcc-boundary-file | yes (local 200; sub-site `gis-planning`) |

Rejected samples:
`maps-data/spatial-data-and-maps/north-atlantic-spatial-data/northatlantic-coastal-and-marine/marine-bird-mapping-and-assessment`
is PRIVATE on live (redirects to `require_login`) and returns HTTP 500 locally — a
pre-existing content issue, not a styling problem. As with product, curl-check live
candidates for the `require_login` redirect before sampling.

## Screenshots

`screenshots/spatial-applcc-boundary-live-<width>.png` — full-page captures from dev
at 1440 and 390. Local verification screenshots live in the parent repo's
`tmp/screenshots/` (gitignored), captured logged-in at a 1660 desktop viewport to
offset the 220px admin toolbar.
