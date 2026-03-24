# lp-lineage-theme-capture

Archived LP lineage site theme captures, and tooling/instructions to transfer them into the `plonetheme.lp` Plone 6 theme.

## Structure

```
lp-lineage-theme-capture/
├── captured-themes/          # Per-sub-site crawled assets
│   ├── aquatics-styles/      # HTML, CSS, screenshots, STYLE-GUIDE.md
│   ├── wlfw-styles/
│   └── ...
└── plans/                    # Repeatable workflow documents
    └── subsite-theme-replication.md
```

## Usage

This repo is used as a **git submodule** within the [plonetheme.lp](https://github.com/sdaitzman/lp) theme codebase. It keeps large reference assets (crawled HTML, CSS, screenshots) and detailed process documentation out of the theme code repo.

### From the parent repo

```bash
# Clone with submodule
git clone --recurse-submodules https://github.com/sdaitzman/lp.git

# Or init after cloning
git submodule update --init
```

### Committing changes

Always commit inside the submodule first, then update the parent:

```bash
cd lp-lineage-theme-capture
git add .
git commit -m "Your change description"
cd ..
git add lp-lineage-theme-capture
git commit -m "Update theme capture submodule"
```

## Contents

Each directory under `captured-themes/` contains reference material for one LP sub-site:

- **`STYLE-GUIDE.md`** — Color palette, typography, layout, navigation, buttons, responsive breakpoints
- **`css/`** — Extracted stylesheets from the original site
- **`html/`** — Captured page HTML and local Plone markup snapshots
- **`images/`** — Header logos, banners, and other design images
- **`screenshots/`** — Desktop and mobile reference screenshots, plus a `testing/` subfolder for development test screenshots

See `plans/subsite-theme-replication.md` for the full capture-to-implementation workflow.
