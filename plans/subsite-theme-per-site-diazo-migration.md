# Migration plan: one-theme-per-sub-site via separate Diazo themes

Status: planning, not yet executed.
Authors: Claude + Sam Daitzman.
Context branch: `first-4-subsite-themes`.

All paths below are written **relative to the parent repo root** (`lp/`), consistent with the other plans in this directory.

---

## Branch scope

This plan, on the `first-4-subsite-themes` branch, ports **only the first 4 LP sub-site themes**:

- `anchor`
- `se-firemap`
- `western-landscapes`
- `wildland-fire`

The other 7 LP sub-sites — `aquatics`, `birdlocale`, `bobscapes`, `eastern-deciduous`, `grasslands`, `literature-gateway`, `wlfw` — are **out of scope for this branch** and will be ported in future branches following the same pattern. Their existing `_custom-<site>.scss` files stay in `theme/scss/` untouched.

---

## Goal

Split the current single Diazo theme (`src/plonetheme.lp/src/plonetheme/lp/theme/`) into **independent per-sub-site Diazo themes**. Use `lineage.themeselection` — already installed via `requirements.txt` and `docker-compose.yml` — to bind each child-site folder to its theme. The portal root keeps a neutral default theme (`lp-base`).

This is "option (a)" from the architectural conversation. Option (b) — one theme scoped by body class — was rejected because:

- `lineage.themeselection` is already a dependency and this is what it exists to do.
- Current `_custom-<site>.scss` files declare `:root` custom properties and bare `body` rules globally; compiling multiple of them together today causes last-import-wins collisions. Option (a) makes the files independent artifacts rather than requiring every file to be religiously scoped.
- Each sub-site visitor downloads only its own compiled CSS.
- Editor UX: sub-site theme is picked in the native Plone control panel per folder.

---

## All design decisions (locked in)

1. **Directory layout.** `themes/` (plural, sibling to nothing else under `plonetheme/lp/`). Replaces the current `theme/` directory.

2. **Shared SCSS strategy.** `themes/_shared/scss/` with `_base.scss` partial imported by each theme entry point. Each theme's `scss/theme.scss` does `@import "../../_shared/scss/base"; @import "custom";`.

3. **Shared `rules.xml` / `index.html`.** **Duplicate per theme.** Each theme directory holds its own `rules.xml` and `index.html`. Drift is acceptable — most sub-sites will diverge slightly in chrome over time anyway. Revisit only if maintenance pain becomes acute.

4. **Portal root theme.** **`lp-base`** — a minimal, neutrally-branded theme. Stripped chrome, no sub-site identity. Serves the `/Plone` root, login pages, admin views, and any pages outside child sites.

5. **Build pipeline.** A single `npm run watch` discovers all themes under `themes/` and watches/builds each one. Implemented via a Node orchestrator script at `themes/scripts/build-themes.mjs`. All Node tooling (`package.json`, `node_modules/`, `scripts/`) is **scoped inside `themes/`** — a single hoisted install shared by every theme, mirroring the current convention where Node lived under `theme/` rather than at the Python-package root. Per-theme variants (`npm run watch:anchor`) supported via a `--theme=<name>` flag. All npm commands run from `themes/`.

6. **`lineage.themeselection` wiring.** **Manual**, walked through by hand for v1. Step-by-step walkthrough lives in this plan (see "Manual `lineage.themeselection` configuration walkthrough" below) and gets ported into `CLAUDE.md` in Phase 5. Codifying the mapping via `registry.xml` is deferred to a possible Phase 6 once the folder layout is stable.

7. **Theme naming.** **Bare names**: `anchor`, `se-firemap`, `western-landscapes`, etc. No `l-p-` prefix. Matches the `themes/<site>/` directory names exactly. The Plone theming control panel and `lineage.themeselection` dropdowns will show these as-is.

8. **Aquatics canonical source.** *Deferred — out of scope on this branch.* When aquatics is later ported on a future branch, `theme/scss/_custom.scss` (the 1517-line "original") is the canonical source over `_custom-aquatics.scss` (the 1259-line "v1 agentic pass"). For now both stay untracked / under `theme/scss/`.

9. **`manifest.cfg` cache-busting version.** Date-based **`YYYY.MM.DD`** format (e.g. `2026.04.27`). Bumped manually only when meaningful CSS or chrome changes ship — typo fixes don't need a bump. Append `.N` if multiple bumps happen the same day (`2026.04.27.2`). Rationale: human-readable in the control panel, no build-time mutation of committed files (which a git-SHA approach would require), discipline is light.

---

## Final directory layout

```
src/plonetheme.lp/src/plonetheme/lp/
└── themes/                                  # NEW — replaces `theme/`
    ├── package.json                         # Single Node manifest, hoisted (was theme/package.json)
    ├── node_modules/                        # Single install shared by every theme
    ├── scripts/
    │   └── build-themes.mjs                 # Discovery + sass + postcss + cleancss
    ├── _shared/                             # Shared chrome (underscore = "not a theme")
    │   ├── scss/
    │   │   ├── _base.scss                   # Imported by every theme's theme.scss
    │   │   ├── _variables.scss              # Was theme/scss/_variables.scss
    │   │   ├── _maps.scss                   # Was theme/scss/_maps.scss
    │   │   └── _print.scss                  # Was theme/scss/print.scss
    │   └── tinymce-templates/               # Was theme/tinymce-templates/
    ├── lp-base/                             # Default portal-root theme (decision 4)
    │   ├── manifest.cfg
    │   ├── rules.xml
    │   ├── index.html
    │   ├── scss/theme.scss
    │   └── styles/theme{.css,.css.map,.min.css,.min.css.map}
    ├── anchor/                              # Per-site theme — pattern repeats per site
    │   ├── manifest.cfg
    │   ├── rules.xml                        # Duplicated per decision 3
    │   ├── index.html                       # Duplicated per decision 3
    │   ├── scss/
    │   │   ├── theme.scss                   # @import _shared/_base; @import custom;
    │   │   └── _custom.scss                 # Was theme/scss/_custom-anchor.scss
    │   ├── styles/theme{.css,.css.map,.min.css,.min.css.map}
    │   └── theme_images/                    # Optional, only if site-specific images diverge
    ├── se-firemap/                          # Was theme/scss/_custom-se-firemap.scss
    ├── western-landscapes/                  # Was theme/scss/_custom-western-landscapes.scss
    └── wildland-fire/                       # Was theme/scss/_custom-wildland-fire.scss
```

The 7 deferred sub-sites (`aquatics`, `birdlocale`, `bobscapes`, `eastern-deciduous`, `grasslands`, `literature-gateway`, `wlfw`) keep their `_custom-<site>.scss` files in `theme/scss/` and will get their own `themes/<site>/` directories on future branches.

**No per-theme `package.json` or `node_modules/`.** One install at `themes/` is shared across every theme via the build orchestrator. Adding a new theme means dropping a directory under `themes/` — no new Node setup.

`themes/` is the cwd for every npm command (`cd themes/ && npm run watch`), matching the current convention from CLAUDE.md (which currently says to `cd theme/`).

The current `theme/` directory is fully removed at the end of Phase 5. During phases 1–3 it stays in place to avoid breaking the working setup.

---

## Build pipeline: one watcher for all themes

### Behavioural requirement

`npm run watch` (no theme argument) should:
- Discover every directory under `themes/` that doesn't start with `_` (i.e. exclude `_shared/`)
- For each, find `<theme>/scss/theme.scss` as the entry point
- Watch all entries in parallel
- On a change, recompile the affected theme

`npm run build` (no argument) should:
- Discover themes the same way
- Do a one-shot build of each (sass → postcss/autoprefixer → cleancss/minify)
- Exit

Per-theme variants:
- `npm run watch:anchor` — watch only the `anchor` theme.
- `npm run build:anchor` — one-shot build of `anchor` only.

### Implementation: `themes/scripts/build-themes.mjs`

A Node orchestrator using sass's native multi-input + watch support (sass already accepts multiple `input:output` pairs in one invocation, including with `--watch`).

```js
#!/usr/bin/env node
// themes/scripts/build-themes.mjs
import { glob } from 'glob';
import path from 'node:path';
import { spawn } from 'node:child_process';
import { parseArgs } from 'node:util';

const { values: args } = parseArgs({
  options: {
    watch: { type: 'boolean', default: false },
    theme: { type: 'string' },
  },
});

// Script lives at themes/scripts/build-themes.mjs; themes are siblings.
const themesDir = path.resolve(import.meta.dirname, '..');
const allEntries = await glob(`${themesDir}/*/scss/theme.scss`);
const entries = allEntries.filter(p => {
  const themeName = path.basename(path.dirname(path.dirname(p)));
  return !themeName.startsWith('_') && (!args.theme || themeName === args.theme);
});

if (entries.length === 0) {
  console.error(`No theme entry points found${args.theme ? ` for --theme=${args.theme}` : ''}`);
  process.exit(1);
}

const sassPairs = entries.map(entry => {
  const themeDir = path.dirname(path.dirname(entry));
  const out = path.join(themeDir, 'styles', 'theme.css');
  return `${entry}:${out}`;
});

const sassArgs = [
  ...(args.watch ? ['--watch'] : []),
  '--load-path=node_modules',
  '--embed-sources',
  ...sassPairs,
];

console.log(`[build-themes] sass ${sassArgs.join(' ')}`);
const child = spawn('sass', sassArgs, { stdio: 'inherit' });
child.on('exit', code => process.exit(code ?? 0));
```

In **watch mode** the script only runs sass — it skips postcss/cleancss for speed. The minified `.min.css` only matters for production builds and `manifest.cfg` references it explicitly. CLAUDE.md already documents that production uses `theme.min.css` and dev uses `theme.css`.

In **build mode** (no `--watch`) we extend the script to chain postcss + cleancss after sass exits. Each theme's `theme.css` gets autoprefixed in place, then minified to `theme.min.css`. Implementation sketch:

```js
if (!args.watch) {
  child.on('exit', async code => {
    if (code !== 0) process.exit(code);
    for (const entry of entries) {
      const themeDir = path.dirname(path.dirname(entry));
      const cssGlob = path.join(themeDir, 'styles', 'theme.css');
      // Run postcss + cleancss for this theme
      await runStep('postcss', ['--config', 'postcss.config.js', '--replace', cssGlob]);
      await runStep('cleancss', [
        '-O1', '--format', 'breakWith=lf',
        '--with-rebase',
        '--source-map', '--source-map-inline-sources',
        '--output', path.join(themeDir, 'styles', 'theme.min.css'),
        path.join(themeDir, 'styles', 'theme.css'),
      ]);
    }
  });
}
```

### `package.json` scripts

The current scripts (`css-compile-main`, `css-prefix-main`, `css-minify-main`, `css-main`, `watch`) are replaced:

```json
{
  "scripts": {
    "watch": "node scripts/build-themes.mjs --watch",
    "watch:anchor":             "node scripts/build-themes.mjs --watch --theme=anchor",
    "watch:lp-base":            "node scripts/build-themes.mjs --watch --theme=lp-base",
    "watch:se-firemap":         "node scripts/build-themes.mjs --watch --theme=se-firemap",
    "watch:western-landscapes": "node scripts/build-themes.mjs --watch --theme=western-landscapes",
    "watch:wildland-fire":      "node scripts/build-themes.mjs --watch --theme=wildland-fire",
    "build": "node scripts/build-themes.mjs",
    "build:anchor":             "node scripts/build-themes.mjs --theme=anchor",
    "build:lp-base":            "node scripts/build-themes.mjs --theme=lp-base",
    "build:se-firemap":         "node scripts/build-themes.mjs --theme=se-firemap",
    "build:western-landscapes": "node scripts/build-themes.mjs --theme=western-landscapes",
    "build:wildland-fire":      "node scripts/build-themes.mjs --theme=wildland-fire"
  }
}
```

(Future branches that port additional sub-sites add their own `watch:<site>` and `build:<site>` entries.)

The per-theme `watch:` and `build:` scripts can be generated/regenerated by a small helper if maintenance becomes annoying, but enumerating them explicitly keeps `npm run` autocomplete useful.

### Dependencies to add to `package.json`

- `glob` — likely already present transitively; verify and add as direct dep if not.
- No new watcher needed — sass's `--watch` covers it.
- `postcss-cli`, `clean-css-cli` — already used by current pipeline, keep.

---

## Git-attributes: mark built artifacts as generated

Current `.gitattributes` (parent repo root) covers the single-theme paths:

```
src/plonetheme.lp/src/plonetheme/lp/theme/styles/theme.css        -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/theme/styles/theme.min.css    -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/theme/styles/theme.css.map    -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/theme/styles/theme.min.css.map -diff linguist-generated=true
```

Replace with glob patterns covering every theme:

```
src/plonetheme.lp/src/plonetheme/lp/themes/*/styles/theme.css        -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/themes/*/styles/theme.min.css    -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/themes/*/styles/theme.css.map    -diff linguist-generated=true
src/plonetheme.lp/src/plonetheme/lp/themes/*/styles/theme.min.css.map -diff linguist-generated=true
```

Effect: GitHub's PR preview collapses these diffs and shows "Load diff" instead of trying to render every line. Prevents the diff UI from timing out or becoming unusable on regenerated CSS.

The old `theme/` lines are removed in Phase 5 (cleanup) once those files are gone.

---

## Migration: existing `_custom-<site>.scss` → per-theme structure

Each of the current files under `src/plonetheme.lp/src/plonetheme/lp/theme/scss/_custom-<site>.scss` moves into its corresponding new theme directory and is renamed to `_custom.scss` (no need for the site prefix once it's scoped by directory).

| Current path | New path |
|---|---|
| `theme/scss/_custom-anchor.scss` | `themes/anchor/scss/_custom.scss` |
| `theme/scss/_custom-se-firemap.scss` | `themes/se-firemap/scss/_custom.scss` |
| `theme/scss/_custom-western-landscapes.scss` | `themes/western-landscapes/scss/_custom.scss` |
| `theme/scss/_custom-wildland-fire.scss` | `themes/wildland-fire/scss/_custom.scss` |

Out of scope on this branch (deferred to future branches): `_custom.scss`, `_custom-aquatics.scss`, `_custom-bobscapes.scss`, `_custom-birdlocale.scss`, `_custom-eastern-deciduous.scss`, `_custom-grasslands.scss`, `_custom-literature-gateway.scss`, `_custom-wlfw.scss`. They stay in `theme/scss/`.

Use `git mv` (not copy + delete) so history follows the files.

Each theme's `scss/theme.scss` becomes:

```scss
// themes/<site>/scss/theme.scss — entry point
@import "../../_shared/scss/base";
@import "custom";
```

The shared `_base.scss` absorbs what's currently in `theme/scss/theme.scss` (the Bootstrap + Barceloneta import chain, `_variables` overrides, `_maps` overrides, base print styles) **with the `@import "custom-*"` line removed**.

---

## Plone profile changes

### `profiles/default/theme.xml`

Currently registers/enables the single `l-p-theme`:

```xml
<theme>
  <name>l-p-theme</name>
  <enabled>true</enabled>
</theme>
```

After migration, only `lp-base` is enabled (all others are available but selected per-folder via `lineage.themeselection`):

```xml
<theme>
  <name>lp-base</name>
  <enabled>true</enabled>
</theme>
```

The other themes are discovered automatically by `plone.app.theming` via their `manifest.cfg` files in the package's resource directory — no per-theme registration needed in `theme.xml`.

### `profiles/default/metadata.xml`

Bump the profile version when this migration ships so existing Plone instances pick up the new theme registration on profile reinstall. An upgrade step in `upgrades/` may be needed if instances are already deployed. For local-only / fresh installs, just bumping `metadata.xml` from `1000` → `1001` is enough.

### Theme registration discoverability

Each `themes/<site>/` directory must include a `manifest.cfg`. Minimal example:

```ini
[theme]
title = Anchor
description = ANCHOR sub-site theme
rules = ./rules.xml
prefix = /++theme++anchor

[theme:parameters]
ajax_load = python: request.form.get('ajax_load')

[theme:overrides]
# Optional overrides go here

[manifest]
version = 2026.04.27
```

Each theme's `prefix` and `name` (in `theme.xml` if registered there) must match the directory name (`anchor`, `aquatics`, etc.) — that's how `plone.app.theming` resolves theme assets in HTML.

---

## Manual `lineage.themeselection` configuration walkthrough

Once Phase 3 is complete (all themes ported and discoverable), an editor walks through each sub-site folder and binds it to its theme. This is one-time setup per Plone site instance.

### Prerequisites

- `collective.lineage` is **installed** (Site Setup → Add-ons shows it as installed, not just available).
- `lineage.themeselection` is **installed** (same — installed status, not available).
- All themes from `themes/<site>/` appear in Site Setup → Theming → Available Themes.
- Sub-site folders exist at their target paths (typically `/Plone/<site>`). Create via Plone's content management UI if they don't.

### Per-folder steps

For each sub-site folder, repeat these steps:

1. Log in as admin: `http://localhost:8080/Plone/login`
2. Navigate to the folder: `http://localhost:8080/Plone/<site>` (e.g. `/Plone/aquatics`)
3. Click **Edit** in the toolbar (or append `/edit` to the URL)
4. Open the **Settings** tab in the edit form (some Plone versions label this "Behaviors")
5. Check **"Child Site"** — this enables the `collective.lineage` behavior on this folder
6. Click **Save**
7. Navigate back to the same folder's edit form (some versions require a re-load before the next field appears)
8. A new field added by `lineage.themeselection` is now visible — typically labeled **"Theme"** or **"Sub-site theme"**, often on a new tab or in the same Settings tab
9. Select the matching theme from the dropdown (e.g., `aquatics` for `/Plone/aquatics`)
10. Click **Save**
11. Open `http://localhost:8080/Plone/<site>` in a new tab — should render with the assigned theme
12. Open `http://localhost:8080/Plone/` (root) — should still render with `lp-base`

### Folder-to-theme mapping

| Folder | Theme |
|---|---|
| `/Plone/anchor` | `anchor` |
| `/Plone/se-firemap` | `se-firemap` |
| `/Plone/western-landscapes` | `western-landscapes` |
| `/Plone/wildland-fire` | `wildland-fire` |

Folder paths assume LP sub-sites live at the portal root with slugs matching theme names. Adjust if the actual site structure differs. The other 7 LP sub-sites are out of scope on this branch — see Branch scope at the top.

### Troubleshooting

- **A theme isn't in the dropdown.** Check Site Setup → Theming. If it's not listed there either, the package needs to be reinstalled (Site Setup → Add-ons → reinstall `plonetheme.lp`) or the theme's `manifest.cfg` is malformed. Check the Plone log for parse errors.
- **The theme dropdown is missing entirely.** `lineage.themeselection` isn't installed. Site Setup → Add-ons → install it.
- **The "Child Site" checkbox is missing.** `collective.lineage` isn't installed.
- **The folder renders the portal root theme even after assignment.** Cache. Restart the Plone container or hard-refresh the browser. Also verify the folder is actually marked as a child site (the `INavigationRoot` marker is set).
- **To unset a theme on a folder.** Edit, set the theme field back to `(default)` or empty. The portal default (`lp-base`) takes over.

This walkthrough is duplicated into `CLAUDE.md` (parent repo) in Phase 5 so it's discoverable from the main repo.

---

## Execution phases

### Phase 0 — Alignment (no code changes)

- [x] All design decisions resolved (above).
- [ ] Confirm first theme to migrate: **anchor** (active, verified rendering).
- [ ] Confirm sub-site folder layout in Plone matches the mapping table above (or adjust the mapping).

### Phase 1 — Scaffold + one theme (proof of concept)

- [ ] Create `src/plonetheme.lp/src/plonetheme/lp/themes/` directory.
- [ ] Create `themes/_shared/scss/_base.scss` from the current `theme/scss/theme.scss` minus the site-specific `@import` line.
- [ ] `git mv theme/scss/_variables.scss themes/_shared/scss/_variables.scss` (likewise `_maps.scss`, `print.scss`).
- [ ] Create `themes/anchor/manifest.cfg`, `themes/anchor/rules.xml` (copy of current `theme/rules.xml`), `themes/anchor/index.html` (copy of current).
- [ ] Create `themes/anchor/scss/theme.scss` with the two `@import` lines.
- [ ] `git mv theme/scss/_custom-anchor.scss themes/anchor/scss/_custom.scss`.
- [ ] `git mv src/plonetheme.lp/src/plonetheme/lp/theme/package.json src/plonetheme.lp/src/plonetheme/lp/themes/package.json`. Same for `package-lock.json` if present.
- [ ] Update the moved `themes/package.json` scripts to use the orchestrator (see "Build pipeline" section above).
- [ ] Create `src/plonetheme.lp/src/plonetheme/lp/themes/scripts/build-themes.mjs`.
- [ ] From `themes/`, run `npm install` to populate `themes/node_modules/`. Confirm `themes/node_modules/` is gitignored (it should already be — verify the existing `.gitignore` covers it via a top-level `node_modules` rule).
- [ ] Add `themes/*/styles/...` patterns to `.gitattributes`.
- [ ] Update `profiles/default/theme.xml` to register `anchor` as enabled (temporary — will switch to `lp-base` in Phase 4).
- [ ] Bump `profiles/default/metadata.xml` version.
- [ ] `./devbuild.sh` to rebuild Plone container.
- [ ] In Plone admin: Site Setup → Add-ons → reinstall `plonetheme.lp`.
- [ ] Site Setup → Theming → confirm `anchor` is available and activated.
- [ ] Verify render at `http://localhost:8080/Plone` matches current via Playwright (compare against pre-migration screenshot).
- [ ] **Checkpoint with Sam before continuing.**

### Phase 2 — Pattern validation with second theme

- [ ] Create `themes/se-firemap/` mirroring anchor's structure.
- [ ] `git mv theme/scss/_custom-se-firemap.scss themes/se-firemap/scss/_custom.scss`.
- [ ] Add `watch:se-firemap` / `build:se-firemap` to `package.json`.
- [ ] Verify the `npm run build` orchestrator handles two themes correctly.
- [ ] Manually configure `lineage.themeselection` for an `/se-firemap` test folder (per walkthrough above); verify `anchor` and `se-firemap` themes coexist (root → anchor, child site → se-firemap).
- [ ] **Checkpoint with Sam.**

### Phase 3 — Port the remaining 2 in-scope themes

For each of `western-landscapes`, `wildland-fire`:

- [ ] Create `themes/<site>/` with full structure (`manifest.cfg`, `rules.xml`, `index.html`, `scss/theme.scss`).
- [ ] `git mv theme/scss/_custom-<site>.scss themes/<site>/scss/_custom.scss`.
- [ ] Add `watch:<site>` / `build:<site>` to `package.json`, register in `configure.zcml`.
- [ ] `npm run build:<site>` to produce initial CSS artifacts.
- [ ] Smoke-test via Playwright against a child-site folder configured via the walkthrough.
- [ ] Commit per theme so reviews are bounded.

The other 7 LP sub-sites (`aquatics`, `birdlocale`, `bobscapes`, `eastern-deciduous`, `grasslands`, `literature-gateway`, `wlfw`) are **out of scope on this branch** — see Branch scope at the top.

### Phase 4 — Portal default theme (`lp-base`)

- [ ] Create `themes/lp-base/` with minimal styling — Bootstrap + Barceloneta + LP-neutral palette (no sub-site colors, no sub-site fonts).
- [ ] Update `profiles/default/theme.xml` to enable `lp-base` instead of `anchor` (or whatever is enabled from earlier phases).
- [ ] Bump `profiles/default/metadata.xml`.
- [ ] Reinstall in Plone admin.
- [ ] Verify: `http://localhost:8080/Plone` renders `lp-base`; `/Plone/anchor` renders `anchor`; `/Plone/aquatics` renders `aquatics`; etc.

### Phase 5 — Cleanup

The legacy `theme/` directory **stays in place on this branch** because the 7 deferred sub-sites still have their `_custom-<site>.scss` partials there, awaiting future migration. Cleanup is scoped to artifacts that are fully replaced.

- [ ] Remove the `<plone:static>` registration of `theme` (l-p-theme) from `configure.zcml` — it's no longer the source of any active theme.
- [ ] Delete `theme/styles/` (compiled output for the legacy single-theme — no longer regenerated).
- [ ] Remove the `theme/styles/` patterns from `.gitattributes`.
- [ ] Delete `theme/manifest.cfg`, `theme/rules.xml`, `theme/index.html`, `theme/preview.png` (legacy single-theme chrome — superseded by per-theme copies under `themes/<site>/`).
- [ ] Keep `theme/scss/_custom-<deferred>.scss` files for the 7 deferred sub-sites; they migrate on their own future branches.
- [ ] Keep `theme/theme_images/` for now since deferred SCSS partials still reference its paths; future branches that port a deferred site move the relevant assets into `themes/<site>/theme_images/`.
- [ ] Update `CLAUDE.md` (parent repo):
  - Rewrite "Theme / Frontend" section: replace `cd src/plonetheme.lp/src/plonetheme/lp/theme/` with `cd src/plonetheme.lp/src/plonetheme/lp/themes/`. Update commands to reflect the orchestrator (`npm run watch`, `npm run watch:<site>`, `npm run build`).
  - Rewrite "Theme layout" section: per-theme directory structure under `themes/`, single hoisted `package.json` and `node_modules/`.
  - Note that `theme/scss/_custom-<deferred>.scss` partials remain as starting material for future per-sub-site migrations.
  - Add the manual `lineage.themeselection` walkthrough as a new section.
- [ ] Grep for any `theme/` path references in `configure.zcml`, tests, or docs — fix or remove the ones that refer to the legacy single theme; leave those that refer to deferred SCSS partials.
- [ ] Run `./devbuild.sh` from clean to confirm a fresh-install path works end-to-end with the 4 ported themes.

### Phase 6 (optional) — Codify child-site theme assignments

Defer until folder layout is stable.

- [ ] Define mapping: child-site folder path → theme name.
- [ ] Write `profiles/default/registry.xml` entries for `lineage.themeselection`, OR a Python upgrade step that walks content and applies the marker + theme.
- [ ] Test: fresh Plone install (`DELETE_EXISTING: true` in `docker-compose.yml`) produces correct per-sub-site theming without manual clicks.

### Phase 7 (optional, cosmetic) — Generate per-site preview screenshots

Each theme's `manifest.cfg` references `preview.png`, which is shown as a thumbnail in Plone's theming control panel and `lineage.themeselection`'s per-child-site control panel. During Phases 1–3 every theme inherits a copy of the original generic Plone/Barceloneta demo screenshot — accurate for the workflow, misleading for the picker UX.

This phase replaces those placeholders with real captures of each rendered theme. It's a one-pass sweep done after every theme is wired up and themeselection-bound to its child site, so each capture reflects the actual chrome the editor will see.

- [ ] For each in-scope theme on this branch (`anchor`, `se-firemap`, `western-landscapes`, `wildland-fire`, plus `lp-base` for the portal root), navigate Playwright to the URL where its theme is active.
- [ ] Capture a screenshot at a representative viewport size (e.g. 1280×720) and save to `themes/<site>/preview.png`, overwriting the placeholder.
- [ ] Bump each theme's `manifest.cfg` version (decision 9) so Plone's resource cache picks up the new preview.
- [ ] Commit per theme or in one bundled commit — they're cosmetic, low risk, easy to review together.

Defer if the theming-control-panel UX is not a priority; the placeholder is harmless beyond the picker thumbnail.

---

## What stays unchanged

- One Python package (`plonetheme.lp`). No split into multiple addons.
- One `pyproject.toml`, one GenericSetup profile.
- `requirements.txt` and `docker-compose.yml` — lineage pins already in place.
- `src/lp.content/` package — content types live separately.
- `lp-lineage-theme-capture/` submodule structure.
- Tests (probably — verify in Phase 1).

---

## Risks / things to watch

- **`rules.xml` divergence over time.** Decision 3 (duplicate per theme) accepts that the 11 copies will drift. If a site-wide chrome change becomes necessary later (e.g., Plone toolbar handling), we'll be making the same edit 11 times. That's tolerated — the alternative is fighting Diazo includes.
- **`index.html` asset paths.** Currently references `styles/theme.min.css` relatively. Stays fine per-theme. Verify no absolute `/++theme++l-p-theme/` references sneak through.
- **Compiled CSS duplication on disk.** Each theme bundles Bootstrap + Barceloneta (~150KB pre-gzip per theme). On this branch with 4 in-scope themes plus `lp-base`, that's ~750KB of compiled CSS on-disk and in-git. Per-request unchanged — visitor downloads one. Worth naming in commit messages to set expectations.
- **TinyMCE templates path move.** If editors have customized templates under `theme/tinymce-templates/`, moving to `themes/_shared/tinymce-templates/` should be transparent (Plone resolves by name), but verify in Phase 2.
- **Tests in `src/plonetheme.lp/tests/`.** May assert on the single-theme layout. Phase 1 should grep for `theme/` path references before moving files.
- **`lineage.themeselection` must be explicitly installed** in the Plone site — `ADDONS:` in docker-compose makes it available, not installed. Walkthrough's prerequisites cover this.
- **Profile upgrade step.** When `theme.xml` changes which theme is enabled, existing Plone instances need a profile reinstall to pick it up. For local dev with `DELETE_EXISTING: true` available, this is not a problem.
- **`manifest.cfg` version discipline.** Per decision 9, dates only get bumped on meaningful changes. There's no mechanical enforcement — easy to forget. Consider a pre-commit hook or build-time check in a future iteration if it becomes a problem.

---

## Rough sizing

T-shirt sizes reflect relative complexity and risk (XS = trivial, mechanical; XL = substantial, novel work with significant unknowns). They are deliberately not time-based — this plan can be executed by humans, AI agents, or a mix, and absolute time estimates don't translate across those contexts.

| Phase | Size | Notes |
|---|---|---|
| 0 — alignment | done | All decisions resolved above. |
| 1 — scaffold + anchor | **M** | New directory structure, new build pipeline, first theme migration, end-to-end verification. Sets the pattern for everything else. |
| 2 — second theme + pattern validation | **S** | Reuses Phase 1's pattern; validates the orchestrator handles >1 theme and the manual themeselection walkthrough is correct. |
| 3 — port the remaining 2 in-scope themes (`western-landscapes`, `wildland-fire`) | **S** per theme | Mechanical once the pattern is set. |
| 4 — `lp-base` default theme | **S** | Minimal styling; mostly Bootstrap + Barceloneta unmodified. |
| 5 — cleanup + docs | **S** | File deletes, gitattributes pruning, CLAUDE.md updates. |
| 6 — codified assignments (optional, deferred) | **M** | Real Plone profile work — `registry.xml` or upgrade step + fresh-install testing. Higher novelty than Phases 3–5. |
| 7 — preview screenshot sweep (optional, cosmetic) | **S** | Playwright loop over every theme's child site URL, save to `themes/<site>/preview.png`. Mostly mechanical. |
