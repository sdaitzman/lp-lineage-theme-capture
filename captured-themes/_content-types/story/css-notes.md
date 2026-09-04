# Story — styling analysis (2026-08-31)

Live source of truth: site-wide `ploneCustom.css` on `dev.landscapepartnership.org`
(story styling is identical wherever the type appears). Rendered locally by the
**browser view** `lp.content/browser/story_view.pt` (the Plone-4 skin template
`6custom/story_view.pt` was deleted in cd81771).

**Important:** `story_view.pt` ships a large inline `<style>` block through
`style_slot`, and every theme's `rules.xml` copies content `head style` into the
theme head — so that block reaches the themed page and already provides most of
the view's presentation: the **white content card** (`.story-content-area`:
`background #fff; box-shadow 0 6px 14px #00000025; padding 30px 50px;
max-width 940px; top -140px` overlap onto the hero image, collapsing at ≤768px),
the `.layout-2col` / absolute `.sidebar` layout, the Merriweather `.description`
lede, blockquote treatment, `.stories-keywords` chips, `.story-sidebar-item`
links, and sidebar `h3` styling. None of that is duplicated in Layer 1 — the
shared partial carries only the live ploneCustom.css rules the inline block does
not.

Implemented in `themes/_shared/scss/content-types/_story.scss`, scoped under
`body.portaltype-story`.

## Shared

| Selector | Live rule (ploneCustom.css) |
|---|---|
| `.story-image` | position relative; width 100vw `!important`; margin-left -50vw `!important`; left 50%; padding 1em 0; text-align center. The two `!important`s are kept — live parity: the full-bleed breakout needs to beat container width (and, locally, the template's own inline `.story-image { width: 768px }` rule) |
| `.template-story_view .sidebar > nav` | background #fff; border-radius 5px; margin-left 1.5em; padding 0 10px 10px; box-shadow 4px 2px 7px 0 rgba(74, 74, 74, 0.2); border 1px solid #eee — rescoped under `body.portaltype-story .sidebar > nav` |
| `.sidebar h4` | font-weight 600; margin-top 1em; margin-bottom 5px; font-size 16px; text-transform uppercase — rescoped under the body scope |
| `.meta` | font-style italic — the template renders the byline/dateline (publication date) in `p.meta` as an italic meta line |
| `.story-image img` | **added 2026-09-03** — live computed (grasslands): background #fff; border 1px solid #ccc; padding 4px (the framed hero look; the inline block only sizes the img) |
| `.story-content-area` (≥769px) | **added 2026-09-03** — live computed top -120px on aquatics AND grasslands; the template's inline block says -140px, so ploneCustom.css overrides it. Body-scoped to win on specificity, and wrapped in a min-width query so the inline block's mobile `top: 0` stands |
| `.link-category` | **added 2026-09-03** — font-size 12px (live computed). Everything else about the threat chips — #ddd pill, .25em/.5em padding, .5em radius, .25em margin — already comes from the template's inline `.group a.link-category` rule and computes to live's 3px 6px / 3px at 12px |

White card: no "approximated from screenshot" rule was needed — the card on the
live aquatics story page corresponds to `.story-content-area`, which IS styled,
by the template's own inline block (see above), so Layer 1 does not restyle it.

## Token-varying

None — the card/nav surfaces are literal `#fff`/`#eee` everywhere; brand color
reaches the page through each theme's heading/link rules.

## Site-specific

None found (ploneCustom.css is site-wide; verify across sub-sites in Phase 5).

## Markup divergences (local Plone 6 browser view vs live Plone 4)

1. **Sidebar headings**: live ploneCustom.css targets `.sidebar h4`; the local
   template emits `h3` ("Landscapes", "Species"), styled by its inline block
   (`border-top 1px #e2e1dd; 1.15em; uppercase`). The rescoped `h4` rule ships
   for live parity but is inert against local markup.
2. **`.story-image img`** (template inline): `width: clamp(1280px, 50vw, 90%)`
   — clamp() with min > max resolves to ≥1280px, which looks unintended.
   Template-owned (`lp.content`), flagged, not changed (needs sign-off).
3. `.meta` italics are also produced structurally by the template's `<i
   class="byline">`/`<i class="dateline">` elements; the CSS rule matches live
   and is harmless.
4. `.publisher` / `.publication` / `.location` render inside `<i>` elements with
   no live stylesheet rule — left unstyled.

## Listing displays

Not enumerated in this pass; blocked on the same layout plumbing recorded in
`product/css-notes.md`. Listing styling for story is NOT yet implemented.

## Verification

### Verification update (2026-09-03) — grasslands-and-savannas

Phase 5 by integrator on grazing-study and woody-encroachment, local 1660 admin vs
dev 1440, plus 390 both sides. Computed-style spot checks: h1 Merriweather 44.8/600
brand-blue, `.description` Merriweather 20.8/#545454, card #fff + 0 6px 14px shadow +
30px/50px padding + 940px max, sidebar nav card #fff/#eee/shadow — all identical live
vs local. Deltas found and fixed in Layer 1: hero frame, card offset -120px, chip font
size (table above).

**Blocking content/template issue (lp.content, needs sign-off) — hero image 404 on
EVERY story:** `story_view.pt` requests `@@images/imageHome/wide`, but `wide` is not
in this site's `plone.allowed_sizes` (huge/great/larger/large/teaser/preview/mini/…).
The `<img>` 404s, `.story-image` collapses to its padding, and the card's negative
offset pulls it up over the byline/publisher line. This also affects the aquatics
sample verified on 2026-08-31 — that pass's "full-bleed .story-image verified"
note was wrong; the image was already 404 there. Remedy options: register a `wide`
scale in `plone.allowed_sizes` via an lp.content `registry.xml` (live's width is
1280 — the img computes to 1280px content width), or change the template to an
existing scale. The frame/offset rules were verified by swapping the img `src` to
`/imageHome/huge` in the browser (`tmp/screenshots/story-grazing-study-after-hugepreview-*.png`):
framed hero + card overlap then match live.

Other remaining deltas, classified:
- **Import gaps:** `themes`, `threats`, `subjects` are empty on the grasslands
  stories, so the sidebar Landscapes/Species card renders as an empty `<nav>`, no
  threat chips, and no "Filed under" row. Body images reference
  `resolveuid/<uid>` targets that do not exist locally (broken image icons).
- **Chrome (replication plan):** `#content` carries 32px horizontal padding at
  390 (Barceloneta) that live does not, and the parent-site/grasslands navigation
  portlet column narrows the story column at desktop; both shrink the card vs live.
- **Verification artifact:** logged-in captures at 390 include the 60px collapsed
  toolbar, which also offsets the 100vw `.story-image` breakout by 30px (scrollWidth
  420). Anonymous local access is not possible (private parents → `require_login`).
- Regression spot-check after the Layer 1 change: aquatics resource-compass unchanged
  apart from the (intended) frame/offset.

### Verification update (2026-08-31)
story-resource-compass (aquatics): white content card (template inline styles) + Layer 1 italic meta, sidebar nav card, full-bleed .story-image verified vs live at 1440. Template clamp() bug still flagged for lp.content sign-off.
