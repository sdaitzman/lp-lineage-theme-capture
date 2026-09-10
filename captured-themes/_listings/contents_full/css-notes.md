# contents_full — styling analysis (2026-09-10)

Live source of truth: site-wide `ploneCustom.css` (+ Plone 4 `base.css`); computed on dev at
1440 on se-firemap (sefm-academic-publications), wildland-fire (research/products) and
gis-planning (partner-gis-mapping-activity), and at 390 on se-firemap.

Implemented in `themes/_shared/scss/content-types/_listings.scss`, scoped
`body.template-contents_full`, with the tile parts shared with `grid_layout` (headline
underline, byline, read-more pill) lifted into a grouped `body.template-grid_layout,
body.template-contents_full` block (dedup ladder step 1).

## Shared (Layer 1)

| Selector (live) | Live rule / computed | Local before | Shipped |
|---|---|---|---|
| `.tileItem` | global `border-top:1px solid #dedede; margin-top:20px; padding-top:20px` + `.template-contents_full .tileItem {display:flex; gap:20px}` | block, no rule | same |
| `.tileImage` | `float:left; margin:0 1.5em 1em 0 (19.2/12.8px); border:1px solid #ccc; padding:4px`; frame measures img + 10px | unframed inline span | `flex:0 0 260px; width:260px; align-self:flex-start; border; padding; margin 0 19px 13px 0` — sized on the **frame**, see note |
| `.tileImage img` | `width:250px; height:auto` (gis-planning 250×106, wildland-fire 250) | 220px, theme rule | `width:100%; max-width:none; height:auto` inside the 260px frame → 250px |
| `.item-content` | flex child taking the rest | — | `flex:1 1 auto; min-width:0` |
| `.tileHeadline` | `font-size:1.5em` on the 12.8px base = 19.2px / 600 / theme font; margin 0 0 10px; link not underlined | theme h2 24px underlined | `font-size:1.2rem; margin:0 0 10px` + shared `a {text-decoration:none}` |
| `.documentByLine` | base.css 85% #666 block; ploneCustom margin 0 20px 10px 0 | 16px body colour | shared block |
| `#content .tileFooter a` | #fff / #1f5c90 / 12px / 600 / uppercase / 6px; hover #f38b1a | 16px theme link | shared block (verified 12px/600/#1f5c90/uppercase/#fff) |
| `@media (max-width:767px) .tileItem` | `flex-direction: column` | — | same; frame keeps its width above the text (`flex-basis:auto; max-width:100%`) |

**Frame-sizing note.** A first pass set `width:250px` on the `<img>` and left the frame
auto-width. Barceloneta's `img { max-width:100% }` then resolved cyclically against the
auto-width flex item and the picture shrank (169px on se-firemap, 139px on wildland-fire;
the se-firemap and wildland-fire themes also carry an older `.tileImage img` rule from the
chrome replication). Sizing the frame (`260px` = 250 + 4px padding + 1px border per side)
and letting the image fill it is deterministic.

## Token-varying

Headline font/colour from the theme (Montserrat orange on se-firemap, myriad blue on
gis-planning); tile body text is the theme's `p` (Merriweather #666 on se-firemap /
wildland-fire, Open Sans #444 on gis-planning) — nothing restated.

## Site-specific (Layer 2)

**se-firemap:** its live theme renders the thumbnail at **220px** (frame 230) where every
other measured sub-site uses 250. Shipped in `themes/se-firemap/scss/_content-types.scss`
(`.tileImage {flex-basis:230px; width:230px}`), imported from `se-firemap/scss/theme.scss`
after `custom` — the first Layer 2 file in the project.

## Markup divergences (local Plone 6 view vs live Plone 4)

1. Local emits an extra `.documentByLine` with `span.item-date · span.item-type`
   ("Jun 15, 2025 · File"); live's byline is empty. Accepted local improvement; styled by the
   shared byline rule.
2. Live thumbnails come from the Plone-4 `imagex_preview` scale; local uses
   `@@images/image/preview` (Files/Products with an `image` field render; Links and
   Folders with only `imagex` on live have no thumbnail locally — import gap, as for
   grid_layout).
3. Local "Read More" link class is `.more` (live `.readmore`); the shared rule targets
   `.tileFooter a`, so both match.
4. Item order follows the catalog (creation/position not migrated) — import gap.
5. **Template bug (lp.content, flag):** every local contents_full page prints the Plone
   site's default front-page rich text ("Welcome! … If you're seeing this text instead of
   the web site you were expecting …") between the folder description and the tiles. The
   view's `text` lookup (`getattr(context, 'text', None)` / `legacy_text` in
   `browser/templates/contents_full.pt`) acquires the Plone site root's `text` field when
   the folder has none. Live shows only the folder's own body text. Not a CSS matter; the
   tiles below it are what was verified.

## Verification (2026-09-10)

Local 1660 admin vs dev 1440, and 390 both sides. Computed after: `.tileItem` flex/gap 20,
border-top #dedede, 20px top spacing; frame 260×(img+10) with 250px image (wildland-fire
250×188), se-firemap 230/220×285 via Layer 2; headline 19.2/600 no underline; byline 13.6px
(85% of the local 16px base — live's 10.88px sits on its 12.8px chrome base) #666; pill
12/600/#1f5c90/uppercase on #fff. 390: tile stacks image-over-text with the frame at its
natural width, matching live's column layout. Regression: grid_layout grasslands/training
unchanged after the shared-block refactor.
