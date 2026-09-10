# Organization — styling analysis (2026-08-31)

Live source of truth: `dev.landscapepartnership.org/portal_css/ploneCustom.css` (+ `base-*.css`).
**ploneCustom.css is served site-wide on live**, so organization styling is identical on
every sub-site (all 668 instances are on `lp-parent-site` anyway) → everything below is
**Shared (Layer 1)**; no Layer 2 override needed.

Implemented in `themes/_shared/scss/content-types/_organization.scss`, scoped under
`body.portaltype-organization`.

## Shared

| Selector | Live rule (source) |
|---|---|
| `.flex-container` | display flex; align-items flex-start. ≤768px: flex-direction column |
| `.objectDetails-left` | color #333333; float left (inert inside flex — kept to match live); line-height 1.3em; margin-bottom 2em; margin-right 2em; min-width 350px |
| `.org-image img` | width 332px; height auto; margin-bottom 1em; border 1px solid #ccc; padding 0 |
| `.field` | clear both; margin-bottom 1em |
| `.field label` | live renders the `KEYWORDS:` label bold; bare `<label>` is not bold in Bootstrap/Barceloneta, so weight 700 is set in the partial (exact live size pending Phase 5 computed-style check) |
| `.space20` / `.visualClear` | height 20px / clear both (Plone-4 helpers used by the template) |
| `table.simple` (+ th/td/hover) | **NOT restated in `_organization.scss`** — the chrome (bg #f9f9f9, border 1px #ccc, 10pt, th/td #bbb borders + 8px 12px padding, hover #e0f8fe, max-width 400px) is lifted into the shared detail-layout partial covering product/project/organization. Here the table sits in the LEFT column (`.objectDetails-left`), not a right sidebar; max-width 400px still applies |

## Token-varying

None — colors above are literal on live for all sub-sites. (Heading color/family land
from each theme's own heading rules.)

## Site-specific

None. (All instances live on `lp-parent-site`; live CSS is site-wide regardless.)

## Markup divergences (local Plone 6 template vs live Plone 4)

`6custom/organization_view.pt` observations:

1. **No 65/35 grid**: unlike product, `.main-block` is used WITHOUT
   `.grid-container-65-35` — the template wraps `.objectDetails-left` +
   `.main-block` in `.flex-container`, and column sizing comes from flex plus
   `.objectDetails-left { min-width: 350px }`. `.main-block` itself gets no
   width rule; none exists on live for this view.
2. **Keywords render inline already**: the template emits
   `<span tal:repeat>` values with literal `", "` separator spans — NOT `ul/li`
   as in `product_view.pt` — so no CSS list-flattening is needed. *Nit:* the
   newline between the value span and the separator span leaves a stray space
   before each comma ("Foo , Bar"), same class of nit as product's. Clean fix
   is whitespace trimming in `organization_view.pt` (lp.content) — flagged,
   not done (template changes need sign-off).
3. **Description is a plain paragraph** (`p.normal`), not the `.introtext`
   lede treatment product uses; no live lede rule exists for this view, so
   none is shipped.
4. **Lead image** uses the `image_preview` scale via `image/tag`; live forces
   the rendered width to 332px in CSS (rule shipped), so scale-size deltas
   between Plone 4 and Plone 6 don't show.
5. **`float: left` on `.objectDetails-left`** is inert inside the flex
   container (floats are ignored in a flex formatting context); kept verbatim
   to match live.

## Listing displays (blocked on layout plumbing)

All 668 organizations live under `/networks/organizations/` (lp-parent-site). Its live
section layout has not been audited yet; locally the folder falls back to `listing_view`
(same `default_view_fallback` / unimported-layout gap as product — see the plan's
**Container & listing displays**). Listing styling for organization is NOT yet implemented.

## Verification

Pending — integrator runs Phase 5 (side-by-side full-page compare of
`dalton-state-college` and `tangled-bank-conservation` local↔live at 1660/390,
computed-style spot checks incl. the KEYWORDS label size, `table.simple` hover,
≤768px flex collapse).

### Verification update (2026-08-31)
org-dalton + org-tangled (lp-parent-site): flex 2-col layout, 332px bordered image rule, bold field labels, shared table.simple chrome all verified. Content gaps (not CSS): org lead images and most contact field values did not import, so table cells render empty.
