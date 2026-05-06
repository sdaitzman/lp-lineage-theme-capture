# Captured Themes

Each subdirectory contains crawled reference material for one Landscape Partnership sub-site. These assets are used during theme replication (see `../plans/subsite-theme-replication.md`).

The canonical list of sub-sites — full names, slugs, and production URLs — lives in the **Sub-site roster** section of `../plans/subsite-theme-replication.md`. Each top-level directory under `captured-themes/` matches a slug from that roster exactly (no suffix).

## Per-site directory structure

```
<slug>/
├── STYLE-GUIDE.md              # Colors, typography, layout, nav, buttons, breakpoints
├── css/                        # Extracted stylesheets from the live site
├── html/                       # Captured page HTML + local Plone markup snapshots
├── images/                     # Logos, banners, background images from the original
└── screenshots/
    ├── 01-home.png             # Desktop reference (1280px, full-height)
    └── 01-home-mobile.png      # Mobile reference (375px, full-height)
```

## Captured sites

The 15 production captures correspond 1:1 with the roster slugs:

`anchor/`, `western-landscapes/`, `wildland-fire/`, `se-firemap/`, `lp-parent-site/`, `working-lands-for-wildlife/`, `aquatics/`, `eastern-deciduous-forests/`, `grasslands-and-savannas/`, `birdlocale/`, `bobscapes/`, `the-literature-gateway/`, `ecosystem-risks-benefits/`, `equity-inclusion/`, `gis-planning/`.

## Archive

`_archive/` holds historical or out-of-scope captures that are **not** valid replication reference material. Currently this includes the dev-sourced `aquatics-dev-styles/` capture (superseded by the production `aquatics/` capture). Material under `_archive/` is kept for traceability only — never use it as the source of truth for theme work.
