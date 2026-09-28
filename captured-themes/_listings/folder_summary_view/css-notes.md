# folder_summary_view / folder_summary_alpha — styling analysis (2026-09-27)

Live source of truth: site-wide `ploneCustom.css` + Plone 4 `base.css`; computed
values measured on dev bobscapes `/bobscapes-images-1` at 1440. Identical on every
sub-site apart from the heading font/colour (theme). Implemented in
`themes/_shared/scss/content-types/_listings.scss` under `body.template-folder_summary_view`;
the summary view was also added to the grouped selector that carries the shared tile
parts (headline link, byline, read-more pill) with grid_layout and contents_full.

## Shared (Layer 1)

| Selector (live) | Live rule / computed | Local before | Shipped |
|---|---|---|---|
| `.tileItem` | `border-top:1px solid #dedede; margin-top:20px; padding-top:20px` | no separator | same + `overflow:hidden` (contains the float) |
| `.tileImage` | `float:left; margin-right:1.5em; margin-bottom:1em; border:1px solid #ccc; padding:4px` (computed 19.2/12.8px) | — (no thumbs, see divergences) | same, `display:block; background:#fff` |
| `.template-folder_summary_view .tileImage img` | `width:100px; height:auto` (computed 100×129) | — | same, `display:block` |
| `.tileHeadline` | `font-size:1.5em` → computed 19.2px / 500 / Montserrat / brand; live `margin-bottom:0` but the byline adds 10px | theme h2 28px, underlined green | `font-size:1.2rem` (=19.2px); `margin:0 0 10px`; link `text-decoration:none` (shared block) |
| `.documentByLine` | 85% (10.88px) #666, `margin:0 20px 10px 0` | — | shared block (85% of the 16px local base = 13.6px; base size is chrome) |
| `.tileBody` | 16px #444, `margin-bottom:16px` | 16px | `margin:0 0 10px` |
| `#content .tileFooter a` | #fff bg, #1f5c90, 12px/600, uppercase, 6px padding, hover #f38b1a | 17.6px underlined | shared block |
| `@media (max-width:768px) .tileHeadline` | `font-size:1.3em; display:block; clear:both; line-height:1.3em; margin-bottom:10px` | — | `clear:both; font-size:1.1rem; line-height:1.3` |

## Token-varying

Headline colour/font come from each theme's `h2` (bobscapes green Montserrat,
grasslands Merriweather blue-grey, gis-planning light blue). No layout-specific code.

## Site-specific

None. (Live's `.section-people .tileImage img {width:150px}` and
`.section-landscapes-wildlife .tileImage img {width:300px}` are section rules for pages
not in this sample; candidates for `body.section-*` rules later.)

## Markup divergences (local Plone 6 template vs live Plone 4)

1. **No thumbnails locally — template bug.** `6custom/folder_summary_view.pt` emits the
   `.tileImage` only when `exists:obj/aq_explicit/image_thumb` (or `imagex_thumb`) —
   Archetypes image-scale accessors that Dexterity objects never have, so the frame is
   never rendered (0 `.tileImage` on 12 Image children). Live shows a 100px thumb on
   every Image/File-with-image child. **lp.content fix:** use
   `obj/@@images/image/thumb` (plone.namedfile scales) with the `image` field, and the
   `imagex` fallback only where that field exists. The frame CSS is in place and was
   verified against the live computed values; it will apply as soon as the template
   emits the markup.
2. **Folder title and description printed twice.** The template prints its own
   `<h1 class="documentFirstHeading">` and `<p class="documentDescription">` (Plone-4
   habit) on top of the ones Plone 6 `main_template` renders. **lp.content fix:** drop
   both from the template. Interim: hidden via
   `#content-core > h1.documentFirstHeading, #content-core > p.documentDescription
   {display:none}` — remove that rule when the template is fixed.
3. **Byline.** Local tiles have no `.documentByLine` for Image/File children (live emits
   an empty one). No visible difference.
4. **Tile order** differs from live (alphabetical locally, folder order on live) — the
   import did not preserve `getObjPositionInParent`. Import gap (already logged for
   grid_layout).

## Verification (2026-09-27)

Local 1660 admin vs dev 1440, and 390 both sides, on bobscapes images (12 tiles);
desktop spot-checks on grasslands quail maps (10, with portlet column), wildland-fire
wildfire (5) and gis-planning webinars (alpha, 2). Computed after the change (bobscapes):
`.tileItem` 1px rgb(222,222,222) top border, margin-top 20, padding-top 20 (= live);
headline 19.2px / 600 / theme colour, no underline (live 19.2 / 500 — weight comes
from the theme's h2); read-more 12px/600/#1f5c90/uppercase on #fff (= live); one
visible h1 (the duplicate hidden). 390: single column, headline clears, separators and
pill intact. Remaining deltas are the four items above — the missing thumbnails are the
only visible one, and they are a template fix, not CSS.
