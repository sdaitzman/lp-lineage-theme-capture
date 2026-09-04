# Product — sample pages (captured 2026-08-30)

Full instance list at capture time: 50 products (per `@search?portal_type=product`;
`content_review_links` lists only the first ~10). Distribution by sub-site:

| Sub-site | Count | Notes |
|---|---|---|
| `lp-parent-site` | 43 | all under `/resources/lp-products/` |
| `wildland-fire` | 6 | under `.../wildland-fire/resources/research/{products,projects}/` |
| `se-firemap` | 1 | a bare test item |
| (other 12 sub-sites) | 0 | no product instances |

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| natures-network | `/Plone/resources/lp-products/natures-network` | https://dev.landscapepartnership.org/resources/lp-products/natures-network | yes |
| index-eco-integrity | `/Plone/resources/lp-products/index-of-ecological-integrity` | https://dev.landscapepartnership.org/resources/lp-products/index-of-ecological-integrity | yes |
| bootjack | `.../wildland-fire/resources/research/products/bootjack-fire-station-water-storage-project` | same path on dev | yes |
| se-firemap-test | `.../se-firemap/resources/se-firemap-test-product` | same path on dev | yes (empty body) |

Rejected samples (redirect to `require_login` on dev — private):
`stream-temperature-inventory-and-mapper`, `connect-the-connecticut-landscape-conservation-design`,
`vernal-pool-mapper-and-database`, `north-atlantic-aquatic-connectivity-collaborative`,
`resilient-coastal-sites`. Roughly half of `/resources/lp-products/` is private on dev —
always curl-check for the `require_login` redirect before sampling.

Known-broken locally: `/Plone/resources/lp-products/beach-and-tidal-habitat-inventories`
returns HTTP 500 (content issue, predates styling work).

## Screenshots

`screenshots/<slug>-live-<width>.png` — full-page captures from dev at 1440 and 390.
Local verification screenshots live in the parent repo's `tmp/screenshots/` (gitignored),
`product-<slug>-local-*` — desktop captured at 1660 viewport to offset the 220px
admin toolbar (content is private locally, so verification happens logged in).
