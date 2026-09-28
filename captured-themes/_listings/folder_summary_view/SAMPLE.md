# folder_summary_view (+ folder_summary_alpha) — sample pages (captured 2026-09-27)

Folder display: `6custom/folder_summary_view.pt`. **620 folders on 12 sub-sites** carry
`layout_property == folder_summary_view` (the most common custom listing); another 25
carry `folder_summary_alpha`, an `lp_scripts` alias that sets `sort_on=sortable_title`
and renders the same template, so live and local body class are both
`template-folder_summary_view portaltype-folder`. One row per child: 100px framed
thumbnail floated left, headline, byline, description, "Read More…".

Since PR #71's Folder FTI change (applied locally 2026-09-27) folders render the
layout at their **plain URL** — no `/folder_summary_view` suffix. Local URLs below are
plain.

## Sampled pages

| Slug | Sub-site | Local | Live (dev, public) | Tiles |
|---|---|---|---|---|
| fsv-bobscapes-images | bobscapes | `/Plone/networks/working-lands-for-wildlife/bobscapes/bobscapes-images-1` | https://dev.landscapepartnership.org/networks/working-lands-for-wildlife/bobscapes/bobscapes-images-1 | 12 (Images) |
| fsv-grasslands-quail-maps | grasslands-and-savannas | `/Plone/…/grasslands-and-savannas/wildlife/quail/information-materials/maps` | same path on dev | 10 (Files/Folders), left nav portlet |
| fsv-wildlandfire-wildfire | wildland-fire | `/Plone/…/wildland-fire/resources/research/projects/wildfire` | same path on dev | 5 |
| fsv-gis-webinars-alpha | gis-planning (**folder_summary_alpha**) | `/Plone/maps-data/gis-planning/conservation-planning/conservation-planning-webinars` | same path on dev | 2 (Folder + video), thumbs 128×96 |
| (reference only) meeting-information-logistics | lp-parent | `/Plone/news/events/events-inbox/brook-trout-stream-temperature-workshop-information/advance-materials/meeting-information-logistics` | same path on dev | 4 |

Rejected: wildland-fire `/prescribed-burning/policy-and-regulations/laws-policies` is
public on dev but empty (0 tiles); the first gis-planning and ecosystem-risks candidates
render an empty listing too.

## Screenshots

`screenshots/fsv-<slug>-live-{1440,390}.png` — full-page dev captures (1440 for all
four; 390 for bobscapes). Local before/after (`fsv-<slug>-{before,after}-{1660,390}.png`)
are in the parent repo's `tmp/screenshots/` (gitignored).
