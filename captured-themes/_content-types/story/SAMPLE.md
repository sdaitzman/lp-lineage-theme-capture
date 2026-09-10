# Story — sample pages (captured 2026-08-31)

Full instance list at capture time: 36 stories (per `@search?portal_type=story`;
`content_review_links` lists only the first ~10). Bucketed by sub-site on 2026-09-03:

| Sub-site | Count | Notes |
|---|---|---|
| `grasslands-and-savannas` | 22 | `.../grasslands-and-savannas/stories/` — all published |
| `aquatics` | 12 | `.../aquatics/news-and-stories/stories/` |
| `wildland-fire` | 1 | `.../wildland-fire/news-and-events/putting-fire-on-the-ground-in-illinois` — 404 on dev |
| `working-lands-for-wildlife` | 1 | `.../wlfw-news/stories/u-s-department-of-agriculture-…` — 404 on dev |
| (other 11 sub-sites) | 0 | no story instances |

The two single-instance sub-sites have no live counterpart to compare against
(their dev URLs 404), so their checklist cells stay blank.

Note: `story_view` is a **browser view** (`lp.content/browser/story_view.pt`,
registered in `browser/configure.zcml`) — the old Plone-4 skin template
`6custom/story_view.pt` was deleted in cd81771.

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| resource-compass | `/Plone/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/aquatics/news-and-stories/stories/aquatics-resource-compass` | https://dev.landscapepartnership.org/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/aquatics/news-and-stories/stories/aquatics-resource-compass | yes (local 200; sub-site `aquatics`) |
| story-grazing-study | `.../grasslands-and-savannas/stories/grazing-study-brings-new-insights-for-bobwhite-quail-management` | same path on dev | yes (`grasslands-and-savannas`; byline, publisher, sidebar Landscapes/Species on live) |
| story-woody-encroachment | `.../grasslands-and-savannas/stories/three-ways-to-combat-woody-encroachment` | same path on dev | yes (`grasslands-and-savannas`; threat chips, h3 sections, inline body images) |

Local story pages are NOT anonymously reachable (parent folders are private locally;
anonymous requests 302 to `require_login`), so local verification is always logged in.
Rejected: `the-best-of-both-worlds` (grasslands) — 404 on dev.

## Screenshots

`screenshots/story-<slug>-live-<width>.png` — full-page captures from dev at 1440
and 390 (resource-compass 2026-08-31; grazing-study, woody-encroachment 2026-09-03). Local verification screenshots live in the parent repo's
`tmp/screenshots/` (gitignored), captured logged-in at a 1660 desktop viewport to
offset the 220px admin toolbar.
