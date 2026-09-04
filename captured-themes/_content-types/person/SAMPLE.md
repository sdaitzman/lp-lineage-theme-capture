# Person — sample pages (captured 2026-08-31)

Full instance list at capture time: 3129 persons (per `@search?portal_type=person`;
`content_review_links` lists only the first ~10). Distribution by sub-site:

| Sub-site | Count | Notes |
|---|---|---|
| `lp-parent-site` | 3129 | ALL instances live under `/Plone/Members/` |
| (other 14 sub-sites) | 0 | no person instances |

## Sampled pages

| Slug | Local | Live | Public on dev? |
|---|---|---|---|
| matt-marshall | `/Plone/Members/matt-marshall` | https://dev.landscapepartnership.org/Members/matt-marshall | no — behind login |

Local sample renders HTTP 200 (logged in as admin).

**Live access note:** `/Members/…` pages are not anonymously reachable on dev —
anonymous requests are redirected to an Expertise Search page that itself
returns 404 on `dev.landscapepartnership.org`, so there is currently no public
live counterpart to compare against. **Live reference screenshots are pending
credentials.** Until then, the styling contract is the rule set extracted from
the site-wide `ploneCustom.css` (see `css-notes.md`), not pixel comparison.

## Screenshots

The `screenshots/person-matt-marshall-live-{1440,390}.png` captures show what an
anonymous visit to the live URL actually renders: the Expertise Search redirect
target's "This page does not seem to exist" 404 (they document the access
behavior, NOT the person view). Real live reference captures of the person view
are **pending credentials** (see live access note above); recapture to the same
`<slug>-live-<width>.png` names once login is available. Local verification
screenshots go in the parent repo's `tmp/screenshots/` (gitignored),
`person-<slug>-local-*` — desktop captured at 1660 viewport to offset the 220px
admin toolbar (verification happens logged in).
