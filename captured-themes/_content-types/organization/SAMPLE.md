# Organization — sample pages (captured 2026-08-31)

Full instance list at capture time: 668 organizations (per `@search?portal_type=organization`;
`content_review_links` lists only the first ~10). Distribution by sub-site:

| Sub-site | Count | Notes |
|---|---|---|
| `lp-parent-site` | 668 | ALL under `/networks/organizations/` |
| (other 14 sub-sites) | 0 | no organization instances |

With every instance on the parent site, cross-sub-site divergence cannot be observed
directly — but live serves one site-wide `ploneCustom.css`, so the shared Layer 1
partial applies everywhere by construction.

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| dalton-state-college | `/Plone/networks/organizations/dalton-state-college` | https://dev.landscapepartnership.org/networks/organizations/dalton-state-college | yes |
| tangled-bank-conservation | `/Plone/networks/organizations/tangled-bank-conservation` | https://dev.landscapepartnership.org/networks/organizations/tangled-bank-conservation | yes |

Both sampled pages are public on live and return HTTP 200 locally.

## Listing displays

| Folder | Live layout | Local layout | Renders locally? |
|---|---|---|---|
| `/networks/organizations/` | not yet audited | falls back to `listing_view` | pending layout plumbing (see plan: Container & listing displays) |

## Screenshots

`screenshots/org-<slug>-live-<width>.png` — full-page captures from dev at 1440 and 390,
using shortened slugs: `org-dalton-live-{1440,390}.png`, `org-tangled-live-{1440,390}.png`.
Local verification screenshots go in the parent repo's `tmp/screenshots/` (gitignored),
`org-<slug>-local-*`, desktop captured at 1660 viewport to offset the 220px admin toolbar.
