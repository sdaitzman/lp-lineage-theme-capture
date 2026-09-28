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

Re-checked 2026-09-09 after merging `main` (folder-view tooling) and re-running the new migrations: `getContentStats` TOTAL is still 9514 and every count above is unchanged.

**Custom types with no instances (not in scope until content exists).** `lp.content` defines 18 custom FTIs; the 7 above are the ones with content. The other 11 have zero instances locally and no importer, so there is nothing to style yet — they are listed so the omission is explicit, not accidental:

| Portal type | Default view | Why absent |
|---|---|---|
| `video` | `video_view` | importer creates nothing (FTI `global_allow=False`, workaround commented out) — known blocked issue |
| `audio` | `audio_view` | no importer |
| `biblio_reference` | `view` | no importer |
| `case_study` | `view` | no importer |
| `cbnrm_annotation` | `annotation_view` | no importer |
| `custom_link` | `custom_link_view` | no importer |
| `megamenu_detail` | `megamenu_detail_view` | no importer |
| `staff_spotlight` | `staff_spotlight_view` | no importer |
| `Document`, `Event`, `News Item` (lp.content overrides of stock FTIs) | stock | stock types — Barceloneta/theme scope, not this plan |

When one of these gains an importer, add it to the roster table and run the pipeline; the Layer 1 partial goes in the same `content-types/` folder.

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

### Two levels of display: object views vs. folder displays

Plone renders a URL with **two independent choices**, and the plan tracks them separately
because they are configured, migrated, and styled differently:

| | Object view (the item itself) | Folder display (a container listing its children) |
|---|---|---|
| What decides it | The item's FTI: `default_view`, or the item's own `layout` property if the editor picked another entry from the FTI's `view_methods` (the "Display" menu) | The container's `layout` property (also picked from **its** FTI's `view_methods`), **or** its `default_page` — a child shown *instead of* any listing |
| Who owns the template | `lp.content` — a `6custom/<view>.pt` skin template or a `browser:page` (product_view, story_view, …) | `lp.content` — `6custom/<layout>.pt` (grid_layout, folder_summary_view, …) or a `browser:page` (contents_full) |
| Body classes to scope CSS | `portaltype-<type>` + `template-<view>` (e.g. `portaltype-product template-product_view`) | `portaltype-folder` (or `-collection`) + `template-<layout>`. **Scope on `template-<layout>`**, never on `portaltype-folder` — the same folder type carries 20+ different layouts |
| What the CSS styles | One item's fields | Tiles/rows for items of **many** types at once; per-type tweaks hang off the tile's `contenttype-<type>` class |
| How it was migrated | Importers created the items; FTIs came with `lp.content`'s profile — object views work out of the box | Exported to `migration/lp_folder_layouts.tsv` (1263 folders: `layout_property` + `default_page`); applied by `scripts/assign_folder_views.sh` (`src/lp.content/scripts/assign_folder_views.py`) |
| Local URL while the plumbing is incomplete | `/Plone/<path>` | `/Plone/<folder>/<layout>` — skin templates and browser views render by **direct traversal** regardless of `view_methods`, and the body still gets `template-<layout>`, so listing CSS can be developed and verified before folders default to them |

Two Plone 6 rules that bite here: (a) `default_view_fallback` — a folder whose `layout` names something not in its FTI's `view_methods` silently renders `listing_view`; (b) `assign_folder_views.py` runs with `VALIDATE_LAYOUTS = True`, so it refuses to assign any layout not in `getAvailableLayouts()` and reports it under "Unavailable source layouts" instead. Both hinge on the same missing piece: **an `lp.content` GenericSetup `types/Folder.xml` (and `Collection.xml`) adding the legacy layouts to `view_methods`** (or `LAYOUT_MAP` entries mapping Plone-4 stock names to Plone-6 ones). That is an `lp.content` change and needs sign-off.

### Folder-display roster (from `migration/lp_folder_layouts.tsv`, 2026-09-09)

Explicit `layout_property` values on the 1263 exported folders, bucketed by sub-site path prefix. Live body class confirmed by curl where a public page exists. "Local" = what `/<folder>/<layout>` does on Plone 6 today (after the 2026-09-09 migrations).

| Layout (`template-*`) | Total | Where (top sub-sites) | Live body class | Local direct render | Plone 6 note |
|---|---|---|---|---|---|
| `folder_summary_view` | 620 | lp-parent 201, wlfw 184, aquatics 83, grasslands 49, edf 40, wildland-fire 24 | `template-folder_summary_view` (also what `folder_summary_alpha` renders as) | **500** `AttributeError: @@kss_field_decorator_view` — Plone-4 KSS reference in `6custom/folder_summary_view.pt` | closest stock: `summary_view` |
| `contents_full` | 440 | se-firemap 86, lp-parent 85, wlfw 66, wildland-fire 64, aquatics 51 | `template-contents_full` | **200** ✓ since 2026-09-10 (was 500 `usaid_text_sentence` until lp.content was uninstalled/reinstalled to pick up the `bl_scripts` skin layer) | browser view `@@contents_full` (FolderView/CollectionView) + `6custom/contents_full.pt`, both rewritten on main 2026-09-07 |
| `folder_full_view` | 56 | lp-parent 31 | `template-folder_full_view` | 404 — no template | Plone 4 stock → `full_view` (needs `LAYOUT_MAP`) |
| `grid_layout` | 48 | aquatics 13, wlfw 9, lp-parent 7, edf 5, grasslands 5, western 3, se-firemap 3 | `template-grid_layout` | **200** ✓ | `6custom/grid_layout.pt`, rewritten on main 2026-09-07 (raw catalog brains) |
| `folder_summary_alpha` | 25 | lp-parent 22, gis-planning 3 | `template-folder_summary_view` | 500 (same KSS error) | alphabetical variant of summary view |
| `galleryview` | 9 | lp-parent 6 | `template-galleryview` | 404 — no template | collective.plonetruegallery — not installed |
| `folder_listing` | 4 | | (private) | 200 `template-folder_listing` | Plone 4 stock → `listing_view` |
| `folder_tabular_view` | 4 | | `template-folder_tabular_view` | 404 | Plone 4 stock → `tabular_view` |
| `folder_contents_alpha` | 3 | | (private) | 404 | new `6custom/alphabetical.pt` (200, `template-alphabetical`) is the intended replacement — needs `LAYOUT_MAP`; verified structurally 2026-09-10 (no public live sample) |
| `chronological` | 3 | lp-parent (news/events) | `template-chronological` | **200** ✓ (`6custom/chronological.pt`, new on main) | stock dl/dt/dd listing on live |
| `staff_directory` | 2 | wlfw | (private) | untested | `6custom/staff_directory.pt` |
| section landing pages: `product_section` `/resources/lp-products`, `project_section` `/projects`, `research_section` `/research`, `resources_section` `/resources` | 1 each | lp-parent | `template-<name>` | `product_section` **503** `KeyError: 'getProjectVocabDict'`; the other three 200 | these are the type-listing pages the object-view runs deferred |
| sub-site homes: `wlfw_home`, `fire_home`, `bobscapes_home`, `equity_home`, `online_learning_en`, `people-search` | 1 each | | | untested | chrome — `subsite-theme-replication.md` scope |
| `folder_leadimage_view`, `atct_album_view` | 1 each | | | 404 | Plone 4 stock → `album_view` |

(36 rows have no `layout_property`; 24 exported folders do not exist locally; 649 rows carry a `default_page`.)

### Prerequisite status after the 2026-09-09 migration run

Run on the existing DB (no reset — no content importer changed since the last full run), backend stopped, in this order:

1. `scripts/import_catalog_schema.sh` — 45 indexes + 18 metadata columns created (getThreats, kwProductTypes*, featured, expertise, …); 27/29 already present; 2 type mismatches left as-is (`start`/`end`: Plone 4 DateIndex vs Plone 6 DateRecurringIndex). Two `plone.dexterity.schema` errors during reindex: behaviors `solr.fields` and `geolocatable` referenced by the `story` FTI are not installed.
2. `scripts/import_zmi_scripts_bl.sh` — 59 ZODB Script (Python) objects imported into `portal_skins/custom_scripts`; 16 have Python-2 compile errors (`print obj.absolute_url()` etc.). That ZODB folder is **not** on the skin path, and neither is the filesystem `bl_scripts` layer.
3. `scripts/assign_folder_views.sh` — **359 default pages set** (folders now show their default page as on live); **0 layouts assigned, 1203 skipped as unavailable** because Folder/Collection `view_methods` are still stock (`album_view full_view listing_view summary_view tabular_view event_listing fullcalendar-view`); 272 default pages skipped because the child does not exist locally; 24 folders missing.

**Update 2026-09-10:** lp.content was uninstalled and reinstalled through the Add-ons control panel (the uninstall profile only removes the browser layer, so content, FTIs and catalog survive). That applied `skins.xml`: `bl_scripts` is now on the skin path, `usaid_text_sentence` resolves, and `contents_full` renders. The three migration steps were re-run afterwards with identical results (indexes/columns already present, 359 default pages already correct, 1203 layouts still unavailable). Note the profile version is still 1001 with no upgrade step — any other existing database (including production) needs the same reinstall until one is added.

**Update 2026-09-14 — clean rebuild, no ZMI importers.** The database was backed up (`backups/plone-data-pre-reset-20260914.tgz`, gzip-verified, Data.fs + blobstorage), reset, and re-imported from scratch: add-ons installed fresh (so `bl_scripts` is on the skin path from the start), then the 22 content/config importers in order — users_groups → folder_tree → docs → googledocs → links → events → fix_events → newsitems → files → images → videos → orgs → people → stories → products → projects → spatial_data → collections → catalog_schema → assign_folder_views → map_portlets → enable_subsites — all exit 0, zero tracebacks, ~37 min. **None of the `import_zmi_*` importers were run** (they are one-off and must not be re-run; the earlier runs of `import_zmi_scripts_bl` on this branch were a mistake). Counts are identical to the pre-reset database (TOTAL 9514). `portal_skins/custom_scripts` and `4custom` no longer exist in the ZODB.

One page changed as a result: **`/projects/project_section` now returns 500** (`TypeError: queryProjects() got an unexpected keyword argument 'kwTaxon'`). `skins.xml` orders the layers `6custom → bl_scripts → lp_scripts`, and both `bl_scripts/queryProjects.py` (BL signature: kwThematicFocus, kwProjStatus, …) and `lp_scripts/queryProjects.py` (LP signature: kwTaxon, kwStressors, kwSystems, …) exist, so the BL copy shadows the LP one that `project_section.pt` calls. The ZMI-imported ZODB copy had been masking this collision. An lp.content decision: rename the BL script, reorder the layers, or make `bl_scripts` a lower layer than `lp_scripts`.

**Update 2026-09-27 — folder layouts assigned (local, PR #71 pending).** Root cause of the 0-assigned runs was two-fold and both fixes are on branch `fix/folder-view-methods` (PR #71, lp.content only): (1) a GenericSetup `types/Folder.xml` extending the Folder FTI `view_methods` with `contents_full grid_layout chronological alphabetical folder_summary_view folder_summary_alpha folder_full_view` (listed in `types.xml`; profile 1002 + upgrade step re-importing `typeinfo`); (2) `assign_folder_views.py` now calls `portal.setupCurrentSkin(app.REQUEST)` — under zconsole no skin is selected, so skin-layer templates were invisible to `getAvailableLayouts()` — and `LAYOUT_MAP` maps `folder_listing→listing_view`, `folder_tabular_view→tabular_view`, `atct_album_view`/`galleryview→album_view`, `folder_contents_alpha→alphabetical`. Result on the fresh DB: **1190 of 1203 layouts assigned** (13 left: per-site `*_home`/`*_section`, `staff_directory`, `folder_leadimage_view`), 359 default pages. Folders now render their layout at the **plain URL**; the `/<layout>` suffix is only needed for layouts a folder doesn't use. Also merged from main 2026-09-22: `folder_summary_view.pt` rewritten (KSS reference gone — renders 200), `folder_full_view.pt` (new), `atct_album_view`/`folder_tabular_view` alias scripts. `folder_contents_alpha` resolves to the folder-contents *management* screen, not a listing — hence the map to `alphabetical`.

So the listing half of every type is still blocked on `lp.content` work (sign-off needed, in priority order): (1) `view_methods` for Folder/Collection or `LAYOUT_MAP`; (2) ~~apply the `skins.xml` change~~ done locally by reinstall — an upgrade step is still the right fix; (3) `folder_summary_view.pt` KSS reference; (3a) `bl_scripts`/`lp_scripts` `queryProjects` name collision breaks `project_section`; (3b) `contents_full.pt` acquires the site root's front-page `text` when a folder has none, printing Plone's "Welcome!" boilerplate above every listing; (4) `product_section` needs `getProjectVocabDict`; (5) story `wide` image scale (object views, see story css-notes); (6) organization Archetypes accessors (see organization css-notes).

### Container & listing displays — how a listing run works

Styling a type is not done when its object view matches — the folders (and old
Topics/Collections) that LIST instances of the type are part of the same run. A
**listing run** takes a `LAYOUT` from the folder-display roster instead of a `TYPE`:

1. **Sample** from `migration/lp_folder_layouts.tsv` (filter `layout_property == LAYOUT`,
   skip rows with a `default_page` — those render the page, not the listing), bucket by
   sub-site, curl the live URL for the `require_login` redirect, and confirm the local
   direct render `/<folder>/<LAYOUT>` returns 200. Record in
   `captured-themes/_listings/<LAYOUT>/SAMPLE.md`.
2. **Capture** live at 1440/390 into `captured-themes/_listings/<LAYOUT>/screenshots/`;
   local at 1660/390 via the direct URL (body class is identical).
3. **Analyze** exactly as Phase 2: extract live `ploneCustom.css` + `base.css` rules for
   the layout's selectors (`.grid_layout`, `.tileItem`, `.tileHeadline`, …), measure
   computed styles, audit markup (live Plone 4 vs local Plone 6 template), write
   `css-notes.md`.
4. **Implement** in `_shared/scss/content-types/_listings.scss`, scoped
   `body.template-<LAYOUT>`. Tile rules shared by several layouts (`.tileItem` chrome,
   `.tileImage`, `.documentByLine`) live once under a grouped selector list; per-type
   tweaks inside a tile use `.contenttype-<type>`. Type-listing section templates
   (`product_section` etc.) stay in the owning type's partial.
5. **Verify** like object pages, including hover states and the ≤768px single-column
   collapse, then tick the listing checklist below.

Until the `view_methods` plumbing lands, the folders themselves still render
`listing_view` (or their newly-set default page) — the styling is real and verified, but
only visible at the direct URL.

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

1.1. Fetch `http://localhost:8080/Plone/getContentStats` for the per-type counts (it truncates the URL list per type). Get the **full** URL list from the catalog: `GET /Plone/@search?portal_type=<TYPE>&b_size=<count>` (admin:admin, `Accept: application/json`). For a listing run, sample from `migration/lp_folder_layouts.tsv` instead (see "how a listing run works").

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
| project | ☑ 2026-09-03 (object views only; via _detail-layout — lede, labels, captioned-image floats added on the parent-site run) | — | — | — | — | — | — | — | — | ✓ | — | — | — | ✓ | — | — |
| spatial_data | ☑ 2026-09-03 (object views only; lede + image-box + 0.8em details fixed on the se-firemap/parent run) | — | — | — | — | — | — | — | ✓ | ✓ | ✓ | — | — | — | — | — |
| organization | ☑ 2026-08-31 (object views only) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | — | — |
| person | ☑ 2026-08-31 (object views only; live visual ref pending — see css-notes) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | — | — |
| google_doc | N/A (frameset view — nothing to style) | | | | | | | | | | | | | | | |
| story | ☑ 2026-09-03 (object views only; hero blocked on missing `wide` image scale — see css-notes) | — | ✓ | — | — | — | — | — | — | — | — | — | — | | | ✓ |

### Listing-display checklist

One row per folder layout from the folder-display roster. `blocked` = the local template does not render (see Prerequisite status); `—` = no folders with that layout on the sub-site.

| LAYOUT | Layer 1 done | anchor | aquatics | birdlocale | bobscapes | e-d-forests | eco-risks | equity | gis-planning | lp-parent | se-firemap | lit-gateway | western | wildland-fire | wlfw | grasslands |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| grid_layout | ☑ 2026-09-09; **rewritten as CSS grid 2026-09-27** (issue #70 — theme `flex:1` overrides broke the 3-up; folders now render it at the plain URL) | | ✓ | — | — | ✓ | — | — | — | | | — | ✓ | ✓ (#70) | | ✓ (#70) |
| chronological | ☑ 2026-09-09 (no Layer 1 rules needed — stock listing on live and local) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | — | — |
| contents_full | ☑ 2026-09-10 (direct-URL renders; se-firemap Layer 2 for its 220px thumbnail) | — | | — | | ✓ | | | ✓ | | ✓ | | | ✓ | | ✓ |
| folder_summary_view (+ folder_summary_alpha) | ☑ 2026-09-27 (separators, 100px thumb frame, headline/byline/pill; thumbs blocked on template `image_thumb` accessor; duplicate h1/description hidden pending template fix) | | | — | ✓ | | | | ✓ (alpha) | | | — | | ✓ | | ✓ |
| product_section | blocked — `getProjectVocabDict` | | | | | | | | | | | | | | | |
| project_section / research_section / resources_section | not started (render 200) | | | | | | | | | | | | | | | |
| alphabetical (replacement for folder_contents_alpha) | ☑ 2026-09-10 structural only (stock listing markup; no public live sample — 3 source folders private) | — | — | — | — | — | — | — | — | ✓ | — | — | — | — | | — |
| folder_full_view | ☑ 2026-09-27 (Layer 1 over Barceloneta full_view_item: entry separators, headline, byline, orange DOWNLOAD; per-child h1 flagged) | — | | — | — | — | — | — | ✓ | | | — | — | — | | — |
| folder_tabular_view → tabular_view | ☑ 2026-09-27 (Plone 4 table.listing chrome over .table-striped; no live sample with rows) | | | | ✓ | | | | | | | | | | | |
| folder_listing → listing_view | stock Barceloneta, nothing to transfer | | | | | | | | | | | | | | | |
| atct_album_view / galleryview → album_view | no rules — live was plonetruegallery / polaroid album; Barceloneta card grid is the stand-in until a gallery add-on is chosen | | (card grid) | | | | | | | | | | | | | |
| galleryview | needs collective.plonetruegallery or a replacement — not installed | | | | | | | | | | | | | | | |
