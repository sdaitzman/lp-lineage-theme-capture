# Content-Type Styling Plan

Repeatable process for styling pages **by content type** across all LP sub-sites, matching the live site's presentation while keeping the SCSS deduplicated: one shared base stylesheet per content type (applies to ALL sub-sites), overridden with per-sub-site theming only where sub-sites genuinely differ.

Companion plans: `subsite-theme-replication.md` (site chrome: header/footer/nav/hero, and the canonical sub-site roster) and `subsite-theme-per-site-diazo-migration.md`. This plan assumes the sub-site themes already exist and compile.

---

## Content-type roster

The source of record is the live report at **`http://localhost:8080/Plone/content_review_links`** (plain text: one section per portal type with the current instance count and page URLs). Re-fetch it at the start of every run — counts and URLs change as importers run. Counts below were captured 2026-08-30.

| Portal type | Count | Default view | Rendered by | Importer |
|---|---|---|---|---|
| `product` | 50 | `product_view` | `lp.content` skin `6custom/product_view.pt` | `scripts/import_products.sh` |
| `project` | 192 | `project_view` | `6custom/project_view.pt` | `scripts/import_projects.sh` |
| `spatial_data` | 100 | `spatial_view` | `6custom/spatial_view.pt` | `scripts/import_spatial_data.sh` |
| `organization` | 668 | `organization_view` | `6custom/organization_view.pt` | `scripts/import_orgs.sh` |
| `person` | 3129 | `person_view` | `6custom/person_view.pt` + `zen_person` layer | `scripts/import_people.sh` |
| `google_doc` | 45 | `gdoc_view` | browser view `lp.content/browser/templates/gdoc_view.pt` | `scripts/import_googledocs.sh` |

When this plan refers to `TYPE`, substitute the **Portal type** column. When it refers to `SITE`, substitute a slug from the sub-site roster in `subsite-theme-replication.md`.

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
- Scope every rule under the type's body class, e.g. `body.portaltype-product { … }` (verify the exact normalized class on a live local page before first use — Plone lowercases and may hyphenate, e.g. `portaltype-spatial_data` vs `portaltype-spatial-data`; also available: `body.template-<view>` e.g. `template-product_view`).
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

## Pipeline (per TYPE)

### Phase 1: Sample & capture

1.1. Fetch `http://localhost:8080/Plone/content_review_links`; extract the URLs for `TYPE`.

1.2. Bucket the URLs by sub-site (path-prefix match against the roster). Pick a sample: 2–3 pages per sub-site that has instances of `TYPE`, preferring pages with rich field usage (images, downloads, long metadata). Record the sample list — local and mapped live URL side by side — in the capture folder (1.4).

1.3. For each sampled page, screenshot the **live** counterpart on `https://dev.landscapepartnership.org/` at desktop (1440) and mobile (390) widths.

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

2.1. Diff the live screenshots (and live-page CSS via devtools/curl where needed) across sub-sites: list what is identical, what differs only by brand token, and what is structurally different.

2.2. Write the findings to `css-notes.md` as three sections: **Shared**, **Token-varying**, **Site-specific (SITE: …)**. This document is the contract for Phases 3–4.

### Phase 3: Implement Layer 1

3.1. Create/extend `_shared/scss/content-types/_<type>.scss` from the **Shared** + **Token-varying** sections (on first run of any type: create the `content-types/` folder, `_index.scss`, and the single import line in `_base.scss`).

3.2. Ensure each theme defines the custom properties the partial consumes (add missing ones to that theme's `_custom.scss` `:root` with the live site's values).

3.3. Verify compilation across ALL themes (`npm run build` once at the end of the phase, or watch output for each), not just the one you're looking at — a Layer 1 change ships to every sub-site.

### Phase 4: Implement Layer 2

4.1. For each entry in **Site-specific**, add the override to `themes/<SITE>/scss/_content-types.scss` (create file + `theme.scss` import on first use for that theme).

4.2. Re-check the decision ladder before writing — if the same override lands in a second theme, it is misfiled and must move to Layer 1.

### Phase 5: Verify & commit

5.1. With Playwright, open each sampled local page and compare against the live reference screenshot: layout, spacing, typography, colors, hover/active states, mobile width. Dev screenshots go to `tmp/screenshots/` with contextual names (never into the submodule or project root).

5.2. Fix regressions on OTHER types/sub-sites: spot-check one page of each previously-completed type on two sub-sites after any Layer 1 change.

5.3. Commit theme-repo changes as one commit per TYPE (or per TYPE × SITE for subset runs): `style <TYPE> pages: shared base + <SITE> overrides`. Commit submodule updates (screenshots, notes) inside the submodule first, then the pointer bump in the parent repo.

5.4. Update the checklist below.

---

## Status checklist

Tick a cell only after Phase 5 verification for that type on that sub-site. `—` = sub-site has no instances of the type.

| TYPE | Layer 1 done | anchor | aquatics | birdlocale | bobscapes | e-d-forests | eco-risks | equity | gis-planning | lp-parent | se-firemap | lit-gateway | western | wildland-fire | wlfw | grasslands |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| product | ☐ | | | | | | | | | | | | | | | |
| project | ☐ | | | | | | | | | | | | | | | |
| spatial_data | ☐ | | | | | | | | | | | | | | | |
| organization | ☐ | | | | | | | | | | | | | | | |
| person | ☐ | | | | | | | | | | | | | | | |
| google_doc | ☐ | | | | | | | | | | | | | | | |
