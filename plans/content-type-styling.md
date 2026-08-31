# Content-Type Styling Plan

Repeatable process for styling pages **by content type** across all LP sub-sites, matching the live site's presentation while keeping the SCSS deduplicated: one shared base stylesheet per content type (applies to ALL sub-sites), overridden with per-sub-site theming only where sub-sites genuinely differ.

Companion plans: `subsite-theme-replication.md` (site chrome: header/footer/nav/hero, and the canonical sub-site roster) and `subsite-theme-per-site-diazo-migration.md`. This plan assumes the sub-site themes already exist and compile.

---

## Content-type roster

The source of record is the live report at **`http://localhost:8080/Plone/getContentStats`** (plain text: one section per portal type with the current instance count and sample page URLs, including stock Plone types, plus a TOTAL; it supersedes the older `content_review_links`, which still exists). Re-fetch it at the start of every run — counts and URLs change as importers run. Like its predecessor it truncates the URL list per type, so get full lists from `@search`. Counts below were captured 2026-08-31 (`getContentStats` TOTAL: 9514; stock types — Document 554, Folder 1251, Image 1295, File 1121, Link 634, Collection 356, Event 72, News Item 10 — are Barceloneta/theme scope, not this plan's; `video` is absent because the importer still creates nothing — known blocked issue).

| Portal type | Count | Default view | Rendered by | Importer |
|---|---|---|---|---|
| `product` | 50 | `product_view` | `lp.content` skin-layer template `6custom/product_view.pt` | `scripts/import_products.sh` |
| `project` | 192 | `project_view` | `6custom/project_view.pt` | `scripts/import_projects.sh` |
| `spatial_data` | 100 | `spatial_view` | `6custom/spatial_view.pt` | `scripts/import_spatial_data.sh` |
| `organization` | 668 | `organization_view` | `6custom/organization_view.pt` | `scripts/import_orgs.sh` |
| `person` | 3129 | `person_view` | `6custom/person_view.pt` (the `zen_person` skin layer adds related person templates) | `scripts/import_people.sh` |
| `google_doc` | 45 | `gdoc_view` | browser view `lp.content/browser/gdoc_view.pt` — a bare frameset; **N/A for styling** (see `captured-themes/_content-types/google_doc/css-notes.md`) | `scripts/import_googledocs.sh` |
| `story` | 36 | `story_view` | browser view `lp.content/browser/story_view.pt` (the old `6custom/story_view.pt` was deleted in `cd81771`) | `scripts/import_stories.sh` |

When this plan refers to `TYPE`, substitute the **Portal type** column. When it refers to `SITE`, substitute a slug from the sub-site roster in `subsite-theme-replication.md`.

**Scope note:** a `TYPE` run covers BOTH the individual object views above AND the container/listing displays that present instances of the type (e.g. `/resources/lp-products` for `product`) — see **Container & listing displays** below.

---

## Reference URLs: local ↔ live

Each URL in `content_review_links` maps to its live counterpart by swapping the origin:

```
http://localhost:8080/Plone/<path>   →   https://dev.landscapepartnership.org/<path>
```

**For this plan, `https://dev.landscapepartnership.org/` is the canonical styling reference for content-type pages** — it has content parity with the migration source. Note the deliberate difference from `subsite-theme-replication.md`, which forbids dev URLs: that rule applies to *site-chrome capture* (production hosts are canonical for header/footer/hero), not to content-type page cross-referencing.

Which sub-site a page belongs to is determined by its path prefix — match it against the Lineage child-site paths in the roster (e.g. anything under `networks/working-lands-for-wildlife/wildland-fire/` outside `se-firemap` is `wildland-fire`). Pages outside every child site belong to `lp-parent-site`.

---

## Architecture: two SCSS layers

### Layer 1 — shared per-type base (all sub-sites)

```
themes/_shared/scss/content-types/
├── _index.scss          # @import one line per type
├── _product.scss
├── _project.scss
├── _spatial-data.scss
├── _organization.scss
├── _person.scss
└── _google-doc.scss
```

`_shared/scss/_base.scss` imports `content-types/index` **after** the existing shared partials and — because every theme's `theme.scss` does `@import "../../_shared/scss/base"` before `@import "custom"` — the shared type styles automatically reach ALL 15 themes and are overridable per theme without `!important`.

Rules for Layer 1:
- Scope every rule under the type's body class, e.g. `body.portaltype-product { … }` (verify the exact normalized class on a live local page before first use — Plone lowercases and hyphenates spaces but keeps underscores, e.g. `portaltype-spatial_data`, not `portaltype-spatial-data`; also available: `body.template-<view>` e.g. `template-product_view`).
- Express all colors, fonts, and spacing through the existing CSS custom properties (`--variable-name`) defined by each theme. Most cross-sub-site variation (brand color, fonts) is then automatic with zero per-theme code.
- Structural/layout rules (grids, image placement, metadata blocks, download buttons) go here — they are the same everywhere on the live site.

### Layer 2 — per-sub-site overrides

Only where the live sub-sites genuinely differ for that type:

```
themes/<SITE>/scss/_content-types.scss    # created only when needed
```

imported from that theme's `theme.scss` **after** `custom`:

```scss
@import "../../_shared/scss/base";
@import "custom";
@import "content-types";   // only if the file exists for this theme
```

Keep the same `body.portaltype-*` scoping and internal organization (one commented section per type) so overrides are findable.

### Container & listing displays

Styling a type is not done when its object view matches — the folders (and old
Topics/Collections) that LIST instances of the type are part of the same run:

1. **Enumerate** them while bucketing URLs in Phase 1: the parent paths of the type's
   instances, plus any section landing pages that present the type. Record each in
   `SAMPLE.md` as `folder | live layout | local layout | renders locally?`.
2. **Identify the live layout** from the live page's `body.template-<name>` class.
   These are mostly custom Plone-4 section templates in `6custom/` (verified live:
   `/resources/lp-products` → `template-product_section`; wildland-fire
   `research/products` → `template-contents_full`; `research` → `template-grid_layout`
   on a `portaltype-topic`), NOT stock folder listings.
3. **Layout plumbing** (one-time prerequisites, flagged during the product pilot —
   these are `lp.content` changes, not theme changes, and need user sign-off):
   - Plone 6 FTIs have `default_view_fallback` enabled: a folder whose `layout` names
     a view method not registered in the FTI's `view_methods` silently falls back to
     the default (`listing_view`). The custom section layouts must be added to the
     Folder (and Topic/Collection) FTI `view_methods` via a GenericSetup `types/`
     profile in `lp.content` before any folder can use them.
   - Per-folder layout assignments were not migrated. Live-side
     `lp_scripts/export_folder_layouts_json.py` exists; an `import_folder_layouts`
     importer is still needed.
   - Each `6custom` section template must be render-tested on Plone 6 before styling
     (several Plone-4 templates are known-broken — cf. the `document_view.pt`
     shadowing incident).
4. **Style** listing displays with the same two-layer scheme, scoped under
   `body.template-<section_template>` (NOT `portaltype-folder`, which is too broad).
   Put the rules in the owning type's Layer 1 partial (e.g. `product_section` styles
   in `_product.scss`); lift selectors shared by several section templates (e.g. the
   `grid-container-*` family) into a `_listings.scss` partial when the second type
   needs them.
5. **Verify** listing pages exactly like object pages (CRITICAL section): full-page,
   both widths, against the live folder URL — including the search/filter/sort
   controls these section templates carry.

Until the plumbing in (3) lands, listing displays render as stock `listing_view`
locally — style object views, record the listing gap in `css-notes.md`, and leave the
checklist's listing half unticked.

### Deduplication decision ladder

Before writing any rule, walk down:

1. Identical (or identical-modulo-color/font) on ≥ 2 sub-sites → **Layer 1**, parameterized with CSS custom properties.
2. Differs only in a themable value → **Layer 1** rule + a custom-property value in the theme's existing `_custom.scss` `:root` block.
3. Genuine structural divergence on one sub-site → **Layer 2** for that theme only.
4. **Never** paste the same block into two themes' files — lift it to Layer 1 instead. `grep` the other themes for your selector before committing.

---

## Prerequisites

1. Docker environment up (`./devbuild.sh`), site healthy at `http://localhost:8080/Plone`.
2. The importers for every `TYPE` in scope have been run (see roster table; run order and caveats are in the repo's importer notes — content must exist locally to style against).
3. `npm run watch` running from `src/plonetheme.lp/src/plonetheme/lp/themes/` (or `npm run watch:<SITE>` for a single-site pass).
4. Playwright available for screenshots and interaction testing (per the repo workflow: dev screenshots → `tmp/screenshots/`, committed reference screenshots → this submodule).

---

## CRITICAL: Visual comparison before every commit

**Never commit content-type styles without a side-by-side comparison of the local page against its live counterpart.** (Same rule as `subsite-theme-replication.md`, adapted to content-type pages.)

For every sampled page, before committing:

1. **Full-page screenshots only** — `page.screenshot({ fullPage: true })`, never a bare viewport capture. Keyword tables, contact fields, and below-the-fold content are exactly what this plan styles, and they are cut off in viewport shots. Scroll to the bottom and back to the top first to trigger lazy-loaded images.
2. **Both widths** — desktop 1440 and mobile 390. Local content is mostly private, so verification happens logged in: capture local desktop at a **1660 viewport** so the 220px admin toolbar doesn't shrink the content area below its live 1440 equivalent.
3. **Compare the content area** element by element against the live reference: grid/column layout, spacing, heading sizes and weights, text color, table chrome, image sizing, list rendering. Chrome (header/nav/hero/footer) belongs to `subsite-theme-replication.md` — note chrome deltas, don't chase them here.
4. **Spot-check computed styles** with `playwright-cli eval` on both live and local — at minimum `fontSize`, `fontWeight`, `color`, `lineHeight` of the type's key elements (field headings, table cells, lede). Record measured live values in `css-notes.md`; don't eyeball font sizes from screenshots.
5. **Test interactive states** the type's CSS defines (e.g. `table.simple` row hover) and the responsive collapse at ≤768px.
6. **Iterate until it matches; only then commit.** Local dev screenshots go to `tmp/screenshots/` (gitignored) with contextual names; only live reference captures are committed to this submodule.

---

## Scope selection — every run takes a subset

A run is defined by **TYPES × SITES**:

- `TYPES` — one or more portal types from the roster. The default and recommended unit of work is **one type across ALL sub-sites** (that is what makes Layer 1 trustworthy).
- `SITES` — defaults to all 15; restrict it when iterating on one theme's Layer 2 overrides.

Examples:
- *All products everywhere*: `TYPES=product`, `SITES=all` — full pipeline below.
- *Person pages on wildland-fire only*: `TYPES=person`, `SITES=wildland-fire` — skip Phase 1/2 if the shared partial already exists; run Phases 3–5 for that site only.
- *Everything on one new sub-site*: `TYPES=all`, `SITES=<SITE>` — Phase 3–5 per type, reusing all existing Layer 1 work.

Track progress in the checklist at the bottom of this file (one row per type; tick sub-sites as verified). A partial run must leave that table accurate.

---

## Subagent execution model

Multi-type runs parallelize across subagents, with one **integrator** session owning
everything shared. The split that avoids coordination failures:

- **One subagent per type (or small type pair)**, owning a DISJOINT file set: its
  `_<type>.scss` partial and its `captured-themes/_content-types/<type>/{SAMPLE.md,css-notes.md}`.
  Nothing else — and never shared files.
- Subagent prompts carry the extracted live CSS rules, the template path, the body-class
  scope, and the sample URLs, so agents don't re-derive (or invent) facts. Agents do NOT
  run the watcher/npm, git, docker, or browsers, and do NOT edit `_index.scss`,
  `_base.scss`, `_detail-layout.scss`, or this plan.
- The **integrator** owns: cross-type shared partials (`_detail-layout.scss`), the
  `_index.scss` import wiring, compiles, all Phase 5 visual verification, screenshots,
  the plan/checklist, and every commit.

**Validating subagent output (mandatory before compile):** read each returned partial
in full and check (a) every rule traces to the extracted live CSS or a clearly-commented
approximation; (b) scoping is exactly `body.portaltype-<type>`; (c) no shared-file edits
slipped in (`git status` the shared paths); (d) no `!important` beyond documented live
parity; (e) docs sections present. Fix small issues directly; send the agent back only
for structural problems. Then wire imports, compile all 15 themes, and run Phase 5
yourself — subagent-authored CSS gets the same visual verification as hand-written CSS,
and mistakes found there are corrected by the integrator (screenshots don't lie;
notes might).

---

## Pipeline (per TYPE)

### Phase 1: Sample & capture

1.1. Fetch `http://localhost:8080/Plone/content_review_links` for the per-type counts — but note it truncates to ~10 URLs per type. Get the **full** URL list from the catalog: `GET /Plone/@search?portal_type=<TYPE>&b_size=<count>` (admin:admin, `Accept: application/json`).

1.2. Bucket the URLs by sub-site (path-prefix match against the roster). Pick a sample: 2–3 pages per sub-site that has instances of `TYPE`, preferring pages with rich field usage (images, downloads, long metadata). **Verify each candidate's live counterpart is publicly reachable** — much of the live content is private and redirects to `require_login`; curl the live URL with `-L` and check the final URL before committing to a sample. Record the sample list — local and mapped live URL side by side, plus rejected private candidates — in `SAMPLE.md` (1.4).

1.3. For each sampled page, capture the **live** counterpart on `https://dev.landscapepartnership.org/` at desktop (1440) and mobile (390) widths — **full-page** captures per the CRITICAL section above, named `<slug>-live-<width>.png`.

1.4. Store captures in this submodule under:

```
captured-themes/_content-types/<TYPE>/
├── SAMPLE.md          # the sampled URL pairs + notes
├── screenshots/       # live-site reference screenshots (committed)
└── css-notes.md       # extracted styling facts (Phase 2)
```

(`_content-types/` is deliberately outside the per-`<slug>/` capture folders — it is cross-sub-site reference material.)

1.5. Commit the capture **in this submodule**, then bump the submodule pointer in the parent repo.

### Phase 2: Analyze — common vs. divergent

2.1. Extract the live CSS rules for the type's view. Fetch the live page's stylesheets (`ploneCustom.css` carries most custom rules; `base-*.css` the Plone 4 defaults) and pull every rule matching the view template's selectors — including the `@media` blocks around them. Where a value isn't in a stylesheet rule (inherited/computed), measure it with `playwright-cli eval` `getComputedStyle` on the live page.

2.2. **Markup parity audit** (the content-type analog of the replication plan's structural audit): the `6custom/*.pt` templates were rewritten during the Plone 6 migration, so local markup will NOT match live 1:1. Compare the live page's content-area HTML against the local page's, region by region (curl both; the local page needs admin auth). For each divergence record: what live emits, what local emits, and the remedy — reproduce live's look in CSS, accept the local improvement with normalized styling, or **flag an `lp.content` template change to the user** (template edits are outside theme scope and need sign-off). Missing content (broken relations, unimported fields) is an import issue — flag it, don't style around it.

2.3. Diff the live rendering across sub-sites that have instances: list what is identical, what differs only by brand token, and what is structurally different. (Live serves one site-wide `ploneCustom.css`, so expect most types to be fully identical across sub-sites — verify rather than assume.)

2.4. Write the findings to `css-notes.md` with these sections: **Shared**, **Token-varying**, **Site-specific (SITE: …)**, **Markup divergences (local vs live)**, and a **Verification** log (filled in during Phase 5, including measured computed-style values). This document is the contract for Phases 3–5.

2.5. While analyzing, systematically walk the style categories so nothing is missed (condensed from the replication plan §3.3): box model & layout (grids, widths, margins); color & background; typography (family/weight/size/line-height — computed, not guessed); content text elements the type's fields emit (paragraphs, `ul`/`ol`, `dl`, tables, image captions, labels); borders & decoration (radius, shadows); interactive states (`:hover`, `:focus`, transitions); responsive behavior (which breakpoints, what changes); print behavior (does the type need anything beyond the shared LP print tier?).

### Phase 3: Implement Layer 1

3.1. Create/extend `_shared/scss/content-types/_<type>.scss` from the **Shared** + **Token-varying** sections (on first run of any type: create the `content-types/` folder, `_index.scss`, and the single import line in `_base.scss`).

3.2. Ensure each theme defines the custom properties the partial consumes (add missing ones to that theme's `_custom.scss` `:root` with the live site's values).

3.3. Verify compilation across ALL themes, not just the one you're looking at — a Layer 1 change ships to every sub-site. Confirm the selector actually landed: `grep -l "portaltype-<type>" themes/*/styles/theme.min.css | wc -l` should equal 15.

> **Watcher gotcha:** `npm run watch` does NOT react to edits under `_shared/scss/` (dart-sass's watch list misses it in this setup, even though the import graph includes it). After any Layer 1 edit, force recompiles with `touch */scss/theme.scss` from the `themes/` directory — the watch picks those up and recompiles + re-minifies everything within a few seconds. Also beware stale watcher processes from earlier sessions (`ps aux | grep "sass --watch"`); kill duplicates.

### Phase 4: Implement Layer 2

4.1. For each entry in **Site-specific**, add the override to `themes/<SITE>/scss/_content-types.scss` (create file + `theme.scss` import on first use for that theme).

4.2. Re-check the decision ladder before writing — if the same override lands in a second theme, it is misfiled and must move to Layer 1.

### Phase 5: Verify & commit

5.1. Run the full **CRITICAL: Visual comparison** cycle (above) for every sampled page: log in (admin/admin), full-page screenshots at 1660 (≈1440 content) and 390 into `tmp/screenshots/` as `product-<slug>-local-<width>-full.png`-style names, side-by-side against the live reference, computed-style spot checks, interactive states, mobile collapse. Iterate on the SCSS until each page matches.

5.2. Record the outcome in `css-notes.md` → **Verification**: which pages/sub-sites were compared, the measured computed values, and every remaining delta with its classification (import gap, template divergence flagged to user, chrome item owned by the replication plan).

5.3. Fix regressions on OTHER types/sub-sites: spot-check one page of each previously-completed type on two sub-sites after any Layer 1 change.

5.4. Commit theme-repo changes as one commit per TYPE (or per TYPE × SITE for subset runs): `style <TYPE> pages: shared base + <SITE> overrides`. Commit submodule updates (screenshots, notes) inside the submodule first, then the pointer bump in the parent repo.

5.5. Update the checklist below.

---

## Status checklist

Tick a cell only after Phase 5 verification for that type on that sub-site — **object views AND listing displays** (until the listing-layout plumbing lands, annotate ticks as object-views-only). `—` = sub-site has no instances of the type.

| TYPE | Layer 1 done | anchor | aquatics | birdlocale | bobscapes | e-d-forests | eco-risks | equity | gis-planning | lp-parent | se-firemap | lit-gateway | western | wildland-fire | wlfw | grasslands |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| product | ☑ 2026-08-30 (object views only; listings blocked on layout plumbing) | — | — | — | — | — | — | — | — | ✓ | ✓ | — | — | ✓ | — | — |
| project | ☑ 2026-08-31 (object views only; via _detail-layout) | — | — | — | — | — | — | — | — | | | — | — | ✓ | — | — |
| spatial_data | ☑ 2026-08-31 (object views only) | — | — | — | — | — | — | — | ✓ | | — | — | — | — | — | — |
| organization | ☑ 2026-08-31 (object views only) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | — | — |
| person | ☑ 2026-08-31 (object views only; live visual ref pending — see css-notes) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | — | — |
| google_doc | N/A (frameset view — nothing to style) | | | | | | | | | | | | | | | |
| story | ☑ 2026-08-31 (object views only) | — | ✓ | — | — | — | — | — | — | | — | — | — | — | — | — |
