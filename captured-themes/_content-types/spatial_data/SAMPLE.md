# Spatial Data — sample pages (captured 2026-08-31)

Full instance list at capture time: 100 spatial_data items (per
`@search?portal_type=spatial_data`; `content_review_links` lists only the first ~10).
Bucketed by sub-site on 2026-09-03:

| Sub-site | Count | Notes |
|---|---|---|
| `lp-parent-site` | 87 (7 published, 80 private) | `/maps-data/spatial-data-and-maps/north-atlantic-spatial-data/…` |
| `se-firemap` | 12 (all published) | `.../se-firemap/data-products/se-firemap-data-sharing/…` |
| `gis-planning` | 1 | `/maps-data/gis-planning/map-products/foundational-maps-1/…` |
| (other 12 sub-sites) | 0 | no spatial_data instances |

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| applcc-boundary | `/Plone/maps-data/gis-planning/map-products/foundational-maps-1/appalachian-lcc-boundary-file` | https://dev.landscapepartnership.org/maps-data/gis-planning/map-products/foundational-maps-1/appalachian-lcc-boundary-file | yes (local 200; sub-site `gis-planning`) |
| spatial-burned-area-rasters-2025 | `.../se-firemap/data-products/se-firemap-data-sharing/old-versions-se-firemap-data/se-firemap-data-2025-release-1994-2024/burned-area-rasters-2025-release` | same path on dev | yes (`se-firemap`; links + 2-row data info, no image) |
| spatial-fire-history-metrics-2024 | `.../se-firemap-data-2024-release/fire-history-metics-_aws` | same path on dev | yes (`se-firemap`) |
| spatial-forest-change-loss | `/Plone/maps-data/spatial-data-and-maps/north-atlantic-spatial-data/northatlantic-terrestrial/forest-change-loss-2000-2012-northeast` | same path on dev | yes (`lp-parent-site`; long lede, portrait preview image) |
| spatial-probability-of-development | `.../northatlantic-connect-the-connecticut/terrestrial-design-products/probability-of-development` | same path on dev | yes (`lp-parent-site`) |

Rejected 2026-09-03: `forest-above-ground-biomass-2012-northeast` (live redirects to login, local HTTP 500);
`southeast-firemap-landsat-annual-burned-area-products-1994-2025-polygons` (spring-2026 release; 404 on dev).

Rejected samples:
`maps-data/spatial-data-and-maps/north-atlantic-spatial-data/northatlantic-coastal-and-marine/marine-bird-mapping-and-assessment`
is PRIVATE on live (redirects to `require_login`) and returns HTTP 500 locally — a
pre-existing content issue, not a styling problem. As with product, curl-check live
candidates for the `require_login` redirect before sampling.

## Screenshots

`screenshots/spatial-<slug>-live-<width>.png` — full-page captures from dev at 1440
and 390 (applcc-boundary 2026-08-31; the four above 2026-09-03). Local verification screenshots live in the parent repo's
`tmp/screenshots/` (gitignored), captured logged-in at a 1660 desktop viewport to
offset the 220px admin toolbar.
