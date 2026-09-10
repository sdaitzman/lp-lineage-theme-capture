# grid_layout (folder display) — sample pages (captured 2026-09-09)

`grid_layout` is a **folder display**, not a content type: a Folder whose `layout`
property is `grid_layout` renders `6custom/grid_layout.pt` (rewritten on main
2026-09-07 to use raw `portal_catalog` brains sorted by `getObjPositionInParent`).
Body classes on live: `template-grid_layout portaltype-folder`. Items inside are of
many types (Folder, Link, Document, Image …) and carry `contenttype-<type>` on the tile.

Source of the sample: `migration/lp_folder_layouts.tsv` (48 folders with
`layout_property == grid_layout`, minus rows that also set a `default_page`).
Distribution by sub-site: aquatics 13, working-lands-for-wildlife 9, lp-parent-site 7,
eastern-deciduous-forests 5, grasslands-and-savannas 5, western-landscapes 3,
se-firemap 3, wildland-fire 2, anchor 1.

**Local URL:** the Folder FTI's `view_methods` do not include `grid_layout` yet
(`assign_folder_views.py` skipped all 48 as "unavailable"), so the folders default to
`listing_view`. The template still renders by direct traversal at
`/Plone/<folder>/grid_layout` with the same `template-grid_layout` body class — that is
what was captured and verified.

## Sampled pages

| Slug | Sub-site | Local (direct) | Live | Public on dev? |
|---|---|---|---|---|
| grid-grasslands-training | grasslands-and-savannas | `.../grasslands-and-savannas/training/grid_layout` | https://dev.landscapepartnership.org/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/grasslands-and-savannas/training | yes — 4 tiles, 3-up |
| grid-aquatics-bogturtle-threats | aquatics | `.../aquatics/wildlife/bog-turtle/species-profile/threats/grid_layout` | same path on dev | yes — 3 tiles |
| grid-edf-gwwa-maps | eastern-deciduous-forests | `.../eastern-deciduous-forests/wildlife/golden-winged-warbler/information-materials/maps-and-data/maps/grid_layout` | same path on dev | yes — 2 tiles, left nav portlet |
| grid-western-training | western-landscapes | `.../western-landscapes/training/grid_layout` | same path on dev | yes |
| grid-wildlandfire-image-gallery | wildland-fire | `.../wildland-fire/image-gallery/grid_layout` | same path on dev | yes (image tiles; wildland-fire theme scrolls inside `#visual-portal-wrapper`, so the local full-page capture stops at the viewport) |

Rejected: both se-firemap grid folders redirect to login on dev; lp-parent `/site-images`
and `/resources/lp-images` are public but are asset dumps (hundreds of image tiles) —
usable for a stress check, not as a reference.

## Screenshots

`screenshots/grid-<slug>-live-{1440,390}.png` — full-page dev captures. Local
before/after verification shots (`grid-<slug>-{before,after}-{1660,390}.png`) live in
the parent repo's `tmp/screenshots/` (gitignored), captured logged in at 1660 to offset
the 220px admin toolbar.
