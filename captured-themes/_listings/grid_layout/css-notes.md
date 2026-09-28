# grid_layout — styling analysis (2026-09-09)

Live source of truth: site-wide `ploneCustom.css` (rules extracted below) plus Plone 4
`base.css` for the byline; identical on every sub-site (verified computed on grasslands
and aquatics — only the heading colour differs, and it comes from the theme).

Implemented in `themes/_shared/scss/content-types/_listings.scss`, scoped under
`body.template-grid_layout` (NOT `portaltype-folder` — the plan's listing-scope rule).

## Shared (Layer 1)

| Selector (live) | Live rule / computed | Local before | Shipped |
|---|---|---|---|
| `.grid_layout` | `display:flex; flex-wrap:wrap; justify-content:space-between; place-content:flex-start` — the `place-content` shorthand re-sets justify-content, so the **computed** value on every live page is `flex-start` (tiles pack left; measured edf 2-tile row xs 402/713, wildland-fire 3-up 138/500/861) | block (tiles stacked full-width) | `display:flex; flex-wrap:wrap; justify-content:flex-start; align-content:flex-start` (the effective value — a first pass shipped `space-between` and spread the 2-tile edf row to the edges) |
| `.grid_layout .tileItem` | `width: calc((90% - (3-1)*25px)/3 - 1px); margin: 0 30px 30px 0; padding-top:0; border:1px solid #ededed; box-shadow:0 0 0 0 #ededed; transition: box-shadow .3s linear` | no border, no width | same |
| `.grid_layout .tileItem:hover` | `box-shadow: 0 5px 10px 0 #ddd` | — | same (verified: hover → `rgb(221,221,221) 0 5px 10px`) |
| `.gridImage img` | `width:100%; height:220px; object-fit:cover` | — | same |
| `.tileHeadline` | ploneCustom `font-size:1.5em`; computed 22.4px / 600 / Merriweather / brand colour; `.grid_layout .tileHeadline {padding:15px 15px 5px}`; links no underline | theme h2: 28px, underlined | `font-size:1.4rem; padding:15px 15px 5px; a{text-decoration:none}` |
| `.documentByLine` | base.css `85% #666 block`; ploneCustom `margin: 0 20px 10px 0`; grid `padding: 0 1rem` | 16px body colour | same (85% of the local 16px = 13.6px vs live 10.88px on its 12.8px base — the base size is chrome) |
| `.grid_layout .tileBody` | `padding:0 15px; overflow-wrap:break-word` (text 17.6px/#3b3b3b already matches) | no padding | same |
| `.grid_layout .tileFooter` | `padding:0 15px` | — | same |
| `#content .tileFooter a` | `background:#fff; color:#1f5c90 !important; padding:6px; text-transform:uppercase; font-size:12px; font-weight:600; border-bottom:none`; hover `#f38b1a` | 17.6px theme-green underlined link | same without `!important` (scoped `body.template-grid_layout #content .tileFooter a` wins); hover verified → `rgb(243,139,26)` |
| `#content .grid_layout a:link` | `border-bottom:none` | — | same |
| `@media (max-width:768px) .grid_layout .tileItem` | `flex: 0 100%` | — | `flex:0 0 100%; width:100%; margin-right:0` |

Live also carries section-specific grid variants (`.section-people`, `.section-networks`,
`.subsection-aquacorridors-tool-suite` 4-up, `.content-partner-organizations-search-collection`
2-up, `.section-training-online-learning` hides description/footer). None of the sampled
folders are in those sections; they are candidates for Layer 2 or `body.section-*` rules
when those pages are run.

## Token-varying

Headline colour and font come from each theme's `h2` — grasslands blue-grey Merriweather,
aquatics teal, e-d-forests green — with zero grid-specific code. The read-more pill colour
`#1f5c90` is literal on live on every sub-site.

## Site-specific

None.

## Markup divergences (local Plone 6 template vs live Plone 4)

1. **No tile images locally.** Live tiles use `<img src=".../imagex_preview">` — a
   Plone-4 `imagex` field on Folders/Links. The local template supports `image`,
   `leadImage` and `imagex`, but the local Folder FTI has no image field and the folders
   carry none (`@types/Folder` lists no image property; REST `image` is null). **Import /
   schema gap** — the 220px image band cannot be verified against real images until
   folder lead images are migrated (checked visually on live only).
2. **Tile order differs** (local: Podcasts first; live: LPLN, WLFW, Webinars, Podcasts).
   The template sorts by `getObjPositionInParent`, so the folder positions were not
   preserved by the import. Import gap.
3. Live emits `<h1 class="hide-heading">` (shown anyway — no live rule hides it); the
   local page emits a plain `<h1>` plus a Barceloneta "last modified" byline. Chrome.
4. Local pages sit beside the navigation portlet column, narrowing `.grid_layout` to
   773px at 1660 (live 1325px at 1440) — the 3-up calc still holds; tiles are just
   narrower. Chrome (replication plan).

## Verification (2026-09-09)

Phase 5 by integrator, local 1660 admin vs dev 1440, and 390 both sides, on
grasslands/training (4 tiles) and e-d-forests/maps (2 tiles), spot-checked aquatics and
western. Computed after the change: `.tileItem` 1px #ededed, margin 0 30 30 0; headline
Merriweather 22.4/600 brand colour, no underline; byline 85% #666; body padding 0 15;
read-more 12px/600/#1f5c90/uppercase on #fff, hover #f38b1a; tile hover shadow
0 5px 10px #ddd — all equal to live. 390: one tile per row, full width. Remaining
deltas are the four markup/import items above; none is CSS.

## 2026-09-27 — issue #70 "Uneven grid layout display" (fixed, Layer 1 rewrite)

**Symptom.** Rows of 3, 4, 5 and 8 tiles on the same page (measured on wildland-fire
`/image-gallery` at 1660: row widths `208/253/208/270/208`, then `329/226/293/327`, then
eight tiles of 97–153px, then three of 402px). Tiles also overflowed their row.

**Root cause.** Two sub-site themes carried, verbatim from their live theme CSS,
`.grid_layout .tileItem { flex: 1 }` (`wildland-fire/scss/_custom.scss`,
`se-firemap/scss/_custom.scss`). `flex: 1` expands to `flex: 1 1 0%`: flex-basis 0 plus
grow, so the Layer 1 `width: calc((90% - 50px)/3 - 1px)` is ignored and each row packs
as many tiles as their *min-content* widths allow (flex items default `min-width:auto`),
then stretches them to fill. Confirmed by enumerating the loaded rules on the page:
`.grid_layout .tileItem {flex:1 1 0%}` from the theme bundle after the Layer 1 width.
On the other 13 sites the flex version held at 3-up only because nothing set `flex`.

**Fix.** `_shared/scss/content-types/_listings.scss` now lays the tiles out with CSS
grid instead of flex: `.grid_layout {display:grid; grid-template-columns:repeat(3,
minmax(0,1fr)); gap:30px; align-items:start}`, `.tileItem {width:auto; min-width:0;
margin:0}`. `flex` has no effect on grid items, so the two theme overrides became
harmless; they were reduced to their background colour, and their live `@media
(max-width:1130px)` single-column breakpoint was re-expressed as
`grid-template-columns: minmax(0,1fr)`. Layer 1 breakpoints: 2 columns ≤991px, 1 column
≤768px (live: 1 column ≤768px). `minmax(0,1fr)` + `overflow-wrap:anywhere` on the
headline stop long unbreakable titles/URLs from widening a column.

**Verified.** wildland-fire `/image-gallery` (20 tiles): `grid-template-columns` computed
`412px 412px 412px`, 7 rows, every tile 412px at x 0/442/884. grasslands `/training`
(4 tiles, portlet column): 3-up at 1660, single column at 390. Card chrome unchanged
(1px #ededed, hover shadow, 220px cover band, 1.4rem headline, read-more pill).
Folders now render the layout at their plain URL (the Folder FTI `view_methods` change
in PR #71 is applied to the local DB), so the `/grid_layout` suffix is no longer needed.
