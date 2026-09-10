# Project — sample pages (captured 2026-08-31)

192 instances (per `@search?portal_type=project` / `getContentStats`). The 2026-08-31
capture only looked at the `wildland-fire` tree; a full bucketing on 2026-09-03 gives:

| Sub-site | Count | Notes |
|---|---|---|
| `lp-parent-site` | 163 (123 published) | `/projects/{sarp,ebtjv,...}/`, `/resources/w2b/`, `/research/` |
| `wildland-fire` | 29 (all published) | `.../wildland-fire/resources/research/projects/` |
| (other 13 sub-sites) | 0 | no project instances |

Roughly a quarter of the parent-site projects are private on dev — curl-check for the
`require_login` redirect before sampling.

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| project-arizona | `.../wildland-fire/resources/research/projects/fire-community-infrastructure/arizona-catalina-rincon-restoration-and-fuels-mitigation` | same path on dev | yes |
| project-kentucky-bayou | `/Plone/projects/sarp/kentucky-bayou-de-chien-jackson-creek-tributary-restoration-project` | same path on dev | yes (`lp-parent-site`; sparse fields, sidebar table only) |
| project-green-river | `/Plone/resources/w2b/green-river-wildlife-management-area-enhancement` | same path on dev | yes (`lp-parent-site`; rich body: labels, h2/h4, floated captioned images, contact list) |
| project-wetland-classification | `/Plone/research/critically-evaluating-terrestrial-wetland-habitat-classification-mapping-climate-sensitive-systems` | same path on dev | yes (`lp-parent-site`; lead image + 5-row sidebar table with URL/dates/leader) |

## Screenshots

`screenshots/project-<slug>-live-{1440,390}.png` — full-page dev captures for all
four sampled pages (arizona 2026-08-31; kentucky-bayou, green-river,
wetland-classification 2026-09-03).
Local before/after verification shots in the parent repo's `tmp/screenshots/`
(`before-project-arizona-1660.png`, `after-project-arizona-1660.png`).

## Listing displays

| Folder | Live layout | Local layout | Renders locally? |
|---|---|---|---|
| `/projects/` and its `sarp/`, `ebtjv/` … children | not yet audited | falls back to `listing_view` | pending layout plumbing (see plan: Container & listing displays) |
| `/resources/w2b/` | not yet audited | `listing_view` | pending layout plumbing |
| `/research/` | `template-grid_layout` on a `portaltype-topic` (per plan) | `listing_view` | pending layout plumbing |
