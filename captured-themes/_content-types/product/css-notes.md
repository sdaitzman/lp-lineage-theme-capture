# Product — styling analysis (2026-08-30)

Live source of truth: `dev.landscapepartnership.org/portal_css/ploneCustom.css` (+ `base-*.css`).
**ploneCustom.css is served site-wide on live**, so product styling is identical on every
sub-site → everything below is **Shared (Layer 1)**; no Layer 2 override was needed.

Implemented in `themes/_shared/scss/content-types/_product.scss`, scoped under
`body.portaltype-product`.

## Shared

| Selector | Live rule (source) |
|---|---|
| `.grid-container-65-35` | grid; 65% / 1fr; column-gap 30px; margin 15px 0. ≤768px: block, width 95%, margin 1em |
| `.introtext` | 16px / 1.5em; weight 600; #444; margin 1em 0 |
| `.field` | clear both; margin-bottom 1em (base css) |
| `.field h4` | computed live: 16px / weight 500 / margin 0 (color+family from theme) |
| `.detail-block img` | width 100%; height auto |
| `table.simple` | bg #f9f9f9 (+ shadow.png top edge — omitted); border 1px #ccc; 10pt; letter-spacing .015em; margin 20px 0; max-width 400px |
| `table.simple th` | border-bottom 1px #bbb; padding 8px 12px; weight 700 (13.33px computed) |
| `table.simple td` | bg #fff; border-bottom/left 1px #bbb; padding 8px 12px |
| `table.simple tr/td:hover` | bg #E0F8FE |
| `.space10` / `.visualClear` | height 10px / clear both (Plone-4 helpers used by the template) |

## Token-varying

None found — colors above are literal on live for all sub-sites. (Heading color/family
land from each theme's own heading rules; theme custom-property prefixes are per-site,
e.g. `--lp-*` vs `--wlfw-*`, so no shared token exists to consume yet.)

## Site-specific

None.

## Markup divergences (local Plone 6 template vs live Plone 4)

`6custom/product_view.pt` was rewritten during migration; differences and remedies:

1. **Keyword lists**: live emits comma-joined plain text in `td`; local emits `ul > li`.
   Reproduced live look in CSS (`td ul` flattened inline with `, ` separators).
   *Nit:* source whitespace before `</li>` leaves a stray space before each comma
   ("Foo , Bar"). Clean fix is trimming whitespace in `product_view.pt` (lp.content) —
   flagged, not done (template changes need sign-off).
2. **Product Type(s) row** (with `h5` group headings — Foundation Information /
   Assessments and Research Results / Decision Support Tools): exists only locally;
   live's template never rendered it. Kept; `h5` normalized to live's plain h5
   (1em, #444).
3. **PROJECT PAGE: block** (`.product-box`): renders on live; locally empty/absent
   because the `projNALCC` relation didn't survive import. Content issue, not CSS.

## Verification (Phase 5, 2026-08-30)

Side-by-side full-page compare local↔live at desktop + 390: `natures-network`,
`index-eco-integrity` (lp-parent-site), `bootjack` (wildland-fire),
`se-firemap-test` (se-firemap). Computed-style spot checks: `.field h4`
16px/500 ✓, `th` 13.33px/700 ✓. Mobile: grid collapses to single column ✓.
Remaining deltas are the import gaps in "Markup divergences" and site-chrome
items owned by the theme-replication plan (e.g. hero banner missing locally).
