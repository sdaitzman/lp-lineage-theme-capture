# contents_full (folder display) — sample pages (captured 2026-09-10)

`contents_full` is the most common custom **folder display** after `folder_summary_view`:
440 folders in `migration/lp_folder_layouts.tsv` across 14 sub-sites (se-firemap 86,
lp-parent 85, working-lands-for-wildlife 66, wildland-fire 64, aquatics 51, grasslands 31,
edf 17, bobscapes 10, lit-gateway 7, western 7, gis-planning 7, eco-risks 3, equity 3,
birdlocale 1). Rendered by the browser view `@@contents_full` (FolderView/CollectionView,
`browser/templates/contents_full.pt`) and the skin twin `6custom/contents_full.pt`, both
rewritten on main 2026-09-07 (PR #60). Live body class: `template-contents_full portaltype-folder`.

**Prerequisite that was missing until 2026-09-10:** the templates call the `bl_scripts`
skin script `usaid_text_sentence`; the `bl_scripts` Filesystem Directory View from
`skins.xml` only reaches a database when the lp.content profile is (re)applied. Uninstalling
and reinstalling lp.content through the Add-ons control panel added the layer and the view
went from HTTP 500 to 200 with all content intact.

**Local URL:** `/Plone/<folder>/contents_full` (direct traversal — Folder `view_methods` are
still stock, so folders themselves default to `listing_view`).

## Sampled pages

| Slug | Sub-site | Local (direct) | Live | Public on dev? |
|---|---|---|---|---|
| cf-sefm-academic-publications | se-firemap | `.../se-firemap-documentation/sefm-academic-publications/contents_full` | https://dev.landscapepartnership.org/networks/working-lands-for-wildlife/wildland-fire/fire-mapping/regional-fire-mapping/se-firemap/resources/se-firemap-documentation/sefm-academic-publications | yes — 7 File tiles with portrait thumbnails |
| cf-sefm-webinars-workshops | se-firemap | `.../se-firemap-documentation/webinars-workshops/contents_full` | same path on dev | yes |
| cf-wildlandfire-research-products | wildland-fire | `.../wildland-fire/resources/research/products/contents_full` | same path on dev | yes — product tiles |
| cf-gis-partner-mapping-activity | gis-planning | `/maps-data/gis-planning/map-products/partner-gis-mapping-activity/contents_full` | same path on dev | yes — Link tiles (thumbnails are `imagex`, not imported locally) |
| cf-grasslands-quail-seminar-series | grasslands-and-savannas | `.../training/webinars-and-instructional-videos/bobwhite-quail-seminar-series/contents_full` | same path on dev | yes |
| cf-edf-wildlife | eastern-deciduous-forests | `.../eastern-deciduous-forests/wildlife/contents_full` | same path on dev | yes |

Rejected: every working-lands-for-wildlife, bobscapes, lit-gateway and eco-risks candidate
in the first eight rows redirects to login on dev.

## Screenshots

`screenshots/cf-<slug>-live-{1440,390}.png` — full-page dev captures. Local before/after
(`cf-<slug>-{before,after}-{1660,390}.png`) in the parent repo's `tmp/screenshots/`.
