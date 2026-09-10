# Person — styling analysis (2026-08-31)

Live source of truth: `dev.landscapepartnership.org/portal_css/ploneCustom.css`.
**ploneCustom.css is served site-wide on live**, so person styling is identical on
every sub-site → everything below is **Shared (Layer 1)**; no Layer 2 override
needed. (Moot in practice anyway: all 3129 person instances sit under
`/Plone/Members/`, i.e. lp-parent-site — see `SAMPLE.md`.)

Implemented in `themes/_shared/scss/content-types/_person.scss`, scoped under
`body.portaltype-person`.

## Shared

| Selector | Live rule (source: ploneCustom.css, site-wide) |
|---|---|
| `#leftcolumn320` | float left; width 320px; margin-top 10px; text-align center |
| `#rightcolumn` | width 700px; float right; margin 10px 10px 15px 15px; position relative |
| `.bio-photo img` | max-width 100%; height auto (box padding 3px / margin 10px auto are inline in the template) |
| `.objectDetails2` | color #333333; font-size 85%; line-height 1.3em |
| `.expertise-2 span` | border-right 1px solid #DAD8D3; color #333333; padding 0 10px 0 5px; white-space wrap (nonstandard-but-live; older browsers treat as normal); display inline-block |
| `table.metadata` | width 100% |
| `table.metadata th` | background #C3D1D6; padding 6px 8px |
| `table.metadata tr` | border-bottom 1px solid #fff |
| `table.metadata td` | background #DDE6ED; overflow-wrap anywhere |
| `table.metadata tr:hover th/td` | background #DDEBC2 (row hover) |
| `#content table.metadata ul` | list-style-type none; margin-left 0 — live uses `!important` on both; ported WITHOUT `!important` (the `body.portaltype-person` scope supplies the specificity) |
| `.vertical.metadata li` | list-style none outside none |
| `.visualClear` | clear both (Plone-4 helper used by the template) |
| ≤768px | **APPROXIMATION, not extracted**: `#leftcolumn320`/`#rightcolumn` → float none, width auto. Live handles mobile in a separate `mobile.css` that was not captured; this stacks the columns at the shared 768px breakpoint. |

## Token-varying

None found — colors above are literal on live for all sub-sites. (Heading
color/family — `h1.documentFirstHeading`, `#rightcolumn h2/h3/h4` — land from
each theme's own heading rules.)

## Site-specific

None. (All instances are on lp-parent-site anyway.)

## Markup divergences (local Plone 6 template vs live Plone 4)

Local view is `6custom/person_view.pt` in `lp.content`. Skin-layer note: the
`zen_person` skin layer carries related person templates (contact form etc.)
and its own person view, but **6custom's `person_view.pt` wins by skin-path
order** — 6custom sits earlier in the skin path, so it is the rendered template.

1. **`#kssPortalMessage` relic**: the template still emits a Plone-4 KSS-era
   `dl.portalMessage.info` ("You have not yet entered your expertise regions"),
   shown only to a member viewing their own profile. Plone 6 status messages
   use different (alert div) markup, so this dl gets no stock chrome. Left
   unstyled in Layer 1 — owner-only, low stakes; flag for an eventual
   `lp.content` template modernization (needs sign-off).
2. **No `ul` in the metadata table**: the live rule `#content table.metadata ul`
   is retained for parity, but the current template renders multi-value fields
   (Organization relations, US Eco Regions) as comma-joined inline links/spans,
   not `ul > li` — the rule is presently inert on person pages.
3. **Inline styles in the template**: `.bio-photo` carries
   `style="padding: 3px; margin: 10px auto;"` and the user-content date `th`
   carries `style="white-space: nowrap"`. Both live in the template, so they
   are not duplicated in the partial.
4. **Address row disabled**: the Address `tr` has `tal:condition="nothing"` —
   permanently off in the migrated template.
5. **Spacing via `<br /><br />`** between Profile and Expertise — Plone-4-era
   markup spacing, kept as-is (styling around it, not fighting it).
6. **Two `table.vertical.metadata` tables share the chrome**: contact details
   (left column) and "Latest content created by this user" (right column) both
   get the th/td background + hover treatment, matching live.

## Listing displays

Person listing/search surfaces (Members roster, Expertise Search) were not part
of this pass — live's anonymous `/Members/` redirect targets an Expertise
Search page that 404s on dev, so there is no live reference yet. Record status
here when the listing-layout plumbing and credentials land.

## Verification

Pending — integrator runs Phase 5.

### Verification update (2026-08-31)
person-matt-marshall (lp-parent-site): metadata table colors (th #c3d1d6 / td #dde6ed / hover), objectDetails2, column floats verified structurally at 1660+390. NO live visual reference exists yet (page private on live; form + basic-auth attempts with migration creds failed) — rules match ploneCustom.css extraction; visual parity check deferred until credentials/path are resolved. Profile/Expertise sections render empty pending profile-field import.
