# tabular_view (folder_tabular_view alias) — sample pages (captured 2026-09-27)

`folder_tabular_view` (4 folders, Plone 4 stock) is mapped by `assign_folder_views.py`
`LAYOUT_MAP` (PR #71) to Barceloneta's stock `tabular_view`; the `lp_scripts` alias
also renders it by direct traversal. Live body class `template-folder_tabular_view`;
local `template-tabular_view`. Live markup is Plone 4 `table.listing`; local is
Bootstrap `table.table.table-striped` inside `.table-responsive`.

| Slug | Sub-site | Local (plain URL) | Live |
|---|---|---|---|
| tabular-bobscapes-sightings | bobscapes | `/Plone/networks/working-lands-for-wildlife/bobscapes/reports/2025/2025-sightings/sightings-reports` (12 Files) | private on dev |
| deliverables | lp-parent | `/Plone/projects/science-investments/final-narrative-stream_classification/aquatic-habitat-classification-group/workspace/deliverables` | public on dev but **empty** (0 rows) |

No public live sample with rows exists; the live look was taken from the Plone 4
`base.css` `table.listing` rules (in `captured-themes/lp-parent-site/css/`).
Local before/after screenshots in the parent repo's `tmp/screenshots/`.
