# folder_full_view — sample pages (captured 2026-09-27)

Folder display: `6custom/folder_full_view.pt` (new on main 2026-09-22). **56 folders**
(lp-parent 31, gis-planning, aquatics, se-firemap, wlfw). The Plone 6 template renders
every child through Barceloneta's `@@full_view_item`, so each entry is the child's own
view (File → file download block, Document → body text) under an `h1` headline.
Live (Plone 4 custom template): `div.item > h2.headline`, byline with contributors,
`.description`, `.extra-info` with an orange "DOWNLOAD FILE" button for Files.
Body class both sides: `template-folder_full_view portaltype-folder`.

## Sampled pages

| Slug | Sub-site | Local (plain URL) | Live (dev, public) | Children |
|---|---|---|---|---|
| ffv-gis-species-habitat | gis-planning | `/Plone/maps-data/gis-planning/data/species-habitat-association-list` | https://dev.landscapepartnership.org/maps-data/gis-planning/data/species-habitat-association-list | 5 Files (PDF) |
| ffv-ctr-core-team-2016-04-29 | lp-parent | `/Plone/projects/connecticut-river-watershed-pilot/connecticut-river-pilot-core-team/connecticut-river-pilot-core-team-meeting-04-29-2016` | same path on dev | 7 (Files/Documents) |

Most other folder_full_view folders are private on dev (workspace meeting folders).

## Screenshots

`screenshots/ffv-gis-species-habitat-live-{1440,390}.png`. Local before/after in the
parent repo's `tmp/screenshots/`.
