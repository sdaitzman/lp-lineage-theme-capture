# alphabetical (folder display) — sample pages (captured 2026-09-10)

`6custom/alphabetical.pt` (new on main 2026-09-07, PR #61) lists children via the
`lp_scripts/getFolderContentsAlpha` skin script; it is the intended Plone 6 replacement for
the Plone-4 `folder_contents_alpha` layout (3 folders in `lp_folder_layouts.tsv`: one on
working-lands-for-wildlife, two under `/news/events/` on lp-parent) — a `LAYOUT_MAP` entry
`folder_contents_alpha → alphabetical` is still needed in `assign_folder_views.py`.

**No public live reference exists**: all three source folders redirect to login on dev, and
live `folder_summary_alpha` (25 folders) renders as `template-folder_summary_view`, a
different template. Verification is therefore structural, as for `chronological`.

| Slug | Local (direct) | Live | Public on dev? |
|---|---|---|---|
| alpha-wheeler-meeting | `/Plone/news/events/wheeler-nwr-partners-meeting/alphabetical` | private | no |
| alpha-wheeler-meeting-3 | `/Plone/news/events/wheeler-nwr-partners-meeting-3/alphabetical` | private | no |

Local before shots in the parent repo's `tmp/screenshots/`. No live screenshots.
