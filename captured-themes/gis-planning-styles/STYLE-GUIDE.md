# GIS & Conservation Planning Toolkit — Style Guide

**Source URL:** https://landscapepartnership.org/maps-data/gis-planning
**Sub-site CSS file:** `gis.css` (4,086 bytes — small per-site override)
**Inherited site CSS:** `ploneCustom.css` (~131 KB, sitewide LP overrides)
**Body class (typical):** `site-gis-planning section-gis-landing`
**Site identifier:** `data-portal-url="https://landscapepartnership.org"` with the gis-planning section.
**Engine:** Plone Classic UI (legacy template, ID-driven layout: `#portal-top`, `#portal-header`, `#portal-globalnav`, `#portal-columns`, `#portal-footer`).

> The GIS & Conservation Planning Toolkit is a small static archive sub-site within the Landscape Partnership portal. It uses LP's shared header/footer/globalnav chrome, then layers a distinctive light-blue (`#5DA7E5`) GIS palette on top. The body wears a tiled "gis-back.png" topographic map background image — a key visual signature.

---

## Page Inventory

All URLs live under `https://landscapepartnership.org/maps-data/gis-planning`.

| #  | Page | URL Path (relative to base) | File |
|----|------|----------------------------|------|
| 01 | Home (GIS & Conservation Planning Toolkit) | `/` | `html/01-home.html` |
| 02 | Conservation Planning (section landing) | `/conservation-planning` | `html/02-conservation-planning.html` |
| 03 | Conservation Planning Process | `/conservation-planning/conservation-planning-process` | `html/03-conservation-planning-process.html` |
| 04 | Conservation Planning Literature | `/conservation-planning/conservation-planning-literature` | `html/04-conservation-planning-literature.html` |
| 05 | Conservation Planning Webinars | `/conservation-planning/conservation-planning-webinars` | `html/05-conservation-planning-webinars.html` |
| 06 | Landscape-scale Conservation Planning (webinar) | `/conservation-planning/conservation-planning-webinars/landscape-scale-conservation-planning` | `html/06-landscape-scale-conservation-planning.html` |
| 07 | Conservation Planning Software | `/conservation-planning/conservation-planning-software` | `html/07-conservation-planning-software.html` |
| 08 | Tools & Resources (section landing) | `/gis-tools-resources` | `html/08-tools-resources.html` |
| 09 | Assessing Future Energy Development | `/gis-tools-resources/assessing-future-energy-development-1` | `html/09-assessing-future-energy-development.html` |
| 10 | Products and Tools for Energy Modelling | `/gis-tools-resources/assessing-future-energy-development-1/copy_of_products-and-tools` | `html/10-products-and-tools-energy.html` |
| 11 | Foundational Research | `/gis-tools-resources/assessing-future-energy-development-1/copy_of_foundational-research` | `html/11-foundational-research.html` |
| 12 | Awareness and Outreach | `/gis-tools-resources/assessing-future-energy-development-1/copy_of_awareness-and-outreach` | `html/12-awareness-and-outreach.html` |
| 13 | Data Access | `/gis-tools-resources/assessing-future-energy-development-1/data-access` | `html/13-data-access.html` |
| 14 | Fact Sheet: Assessing Future Energy | `/gis-tools-resources/assessing-future-energy-development-1/fact-sheet-assessing-future-energy` | `html/14-fact-sheet-assessing-future-energy.html` |
| 15 | Riparian Restoration Decision Support Tool | `/gis-tools-resources/riparian-restoration-decision-support-tool-1` | `html/15-riparian-restoration-decision-support-tool.html` |
| 16 | Riparian Prioritization Report (long-title leaf) | `/gis-tools-resources/riparian-restoration-decision-support-tool-1/riparian-prioritization-assess-cc-resilience-coldwater-stream-habitats-app-ne-regions` | `html/16-riparian-prioritization-report.html` |
| 17 | Canopy Cover Statistics | `/gis-tools-resources/riparian-restoration-decision-support-tool-1/canopy-cover-statistics` | `html/17-canopy-cover-statistics.html` |
| 18 | Riparian Restoration Fact Sheet | `/gis-tools-resources/riparian-restoration-decision-support-tool-1/riparian-restoration-decision-support-tool-fact-sheet` | `html/18-riparian-restoration-fact-sheet.html` |
| 19 | Decision Support & Web Map Viewers | `/gis-tools-resources/web-map-viewers` | `html/19-decision-support-web-map-viewers.html` |
| 20 | Energy Forecast Model (offsite redirect placeholder) | `/gis-tools-resources/web-map-viewers/energy%20forcast%20model` | `html/20-energy-forecast-model.html` |
| 21 | Extensions and Other Tools | `/gis-tools-resources/extensions-other-tools` | `html/21-extensions-other-tools.html` |
| 22 | Data Needs Assessment Foundational Research | `/gis-tools-resources/data-needs-assessment-foundational-research` | `html/22-data-needs-assessment.html` |
| 23 | Planning In Practice (section landing) | `/map-products` | `html/23-planning-in-practice.html` |
| 24 | Funded Project Maps | `/map-products/funded-project-maps-1` | `html/24-funded-project-maps.html` |
| 25 | Map Gallery (folder listing) | `/map-products/map-gallery` | `html/25-map-gallery.html` |
| 26 | Map: All Biomass | `/map-products/map-gallery/all-biomass/view` | `html/26-map-all-biomass.html` |
| 27 | Map: Bailey Ecoregion | `/map-products/map-gallery/bailey-ecoregion/view` | `html/27-map-bailey-ecoregion.html` |
| 28 | Map: base — color | `/map-products/map-gallery/base-color/view` | `html/28-map-base-color.html` |
| 29 | Map: Biomass Crops | `/map-products/map-gallery/biomass-crops/view` | `html/29-map-biomass-crops.html` |
| 30 | Map: Biomass Forest | `/map-products/map-gallery/biomass-forest/view` | `html/30-map-biomass-forest.html` |
| 31 | Map: Biomass Manure | `/map-products/map-gallery/biomass-manure/view` | `html/31-map-biomass-manure.html` |
| 32 | Map: Coal | `/map-products/map-gallery/coal/view` | `html/32-map-coal.html` |
| 33 | Map: Ecoregions | `/map-products/map-gallery/ecoregions/view` | `html/33-map-ecoregions.html` |
| 34 | Map: Glacial Extent | `/map-products/map-gallery/glacial-extent/view` | `html/34-map-glacial-extent.html` |
| 35 | Map: Karst | `/map-products/map-gallery/karst/view` | `html/35-map-karst.html` |
| 36 | Map: NLCD | `/map-products/map-gallery/nlcd/view` | `html/36-map-nlcd.html` |
| 37 | Map: public lands | `/map-products/map-gallery/public-lands/view` | `html/37-map-public-lands.html` |
| 38 | Map: Recreation | `/map-products/map-gallery/recreation/view` | `html/38-map-recreation.html` |
| 39 | Map: Shale | `/map-products/map-gallery/shale/view` | `html/39-map-shale.html` |
| 40 | Map: States | `/map-products/map-gallery/states/view` | `html/40-map-states.html` |
| 41 | Community GIS Mapping Activity | `/map-products/partner-gis-mapping-activity` | `html/41-community-gis-mapping.html` |
| 42 | Conservation Planning Projects | `/map-products/conservation-planning-projects` | `html/42-conservation-planning-projects.html` |
| 43 | Data (section landing) | `/data` | `html/43-data.html` |
| 44 | Share LP and Partner Spatial Data | `/data/share-landscape-partnership-and-partner-spatial-data` | `html/44-share-spatial-data.html` |
| 45 | Public Data Repositories | `/data/data-repositories` | `html/45-public-data-repositories.html` |
| 46 | Species & Habitat Association List | `/data/species-habitat-association-list` | `html/46-species-habitat-association-list.html` |
| 47 | Amphibians | `/data/species-habitat-association-list/amphibians` | `html/47-amphibians.html` |
| 48 | Bivalves | `/data/species-habitat-association-list/bivalves` | `html/48-bivalves.html` |
| 49 | Birds | `/data/species-habitat-association-list/birds` | `html/49-birds.html` |
| 50 | Mammals | `/data/species-habitat-association-list/mammals` | `html/50-mammals.html` |
| 51 | Reptiles | `/data/species-habitat-association-list/reptiles` | `html/51-reptiles.html` |
| 52 | Sitemap (footer link) | `/sitemap` | `html/52-sitemap.html` |
| 53 | Accessibility (footer link) | `/accessibility-info` | `html/53-accessibility.html` |
| 54 | Contact (footer link) | `/contact-info` | `html/54-contact.html` |
| 55 | Conditions of Membership (footer link → /resources/help-1/how-to-participate/) | `/resources/help-1/how-to-participate/conditions-of-membership` | `html/55-conditions-of-membership.html` |

**Total: 55 pages.** All pages have desktop (1280×fullPage) and mobile (375×fullPage) screenshots in `screenshots/`.

### Pages enumerated from sidebar nav (sub-nav tree)

The captured sidebar enumerates all pages under the four main sections — Conservation Planning (#02–#07), Tools & Resources (#08–#22), Planning In Practice (#23–#42, including the entire Map Gallery #26–#40), and Data (#43–#51). Per §1.1 of the plan, every individually linked page is captured rather than sampled, because the Map Gallery items in particular are distinct content even if the layout is uniform.

### Pages enumerated from top nav

The captured production sub-site renders only the **sidebar nav**; there is no separate horizontal top-level nav within the gis-planning sub-site (the parent `#portal-globalnav` is shared with the LP root site and not enumerated here, as it is parent chrome rather than sub-site nav). The "Sections" sidebar list under the masthead is the canonical sub-site navigation.

### Pages enumerated from footer

`#portal-footer` contains:
- Five visible link lists (Learn, Browse, Contact). All point to LP root paths (`/about`, `/networks`, `/people`, `/key-issues`, `/help`, `/projects`, `/plan-design`, `/news`, `/resources`, `/training-online-learning`, `/contact-info`) — these are LP root chrome and not part of the gis-planning sub-site itself.
- A bottom rule with: **Site Map** → captured as #52, **Accessibility** → #53, **Contact** → #54, and **Conditions of Membership** → #55.

The footer also contains:
- A "Navigate the Landscape Partnership" `<select>` jump menu — purely external/parent navigation; not captured as pages.
- Partner logos: WLFW, USDA-NRCS, EBTJV, SARP, LP. (Captured as images, see §Images.)

---

## Color Palette

The gis-planning sub-site is unusual in that it has **no `:root` CSS custom properties** — `gis.css` uses hardcoded hex values directly. Below is the inferred semantic palette.

### Primary GIS palette (`gis.css`)

| Hex | Role | Selector(s) |
|-----|------|-------------|
| `#5DA7E5` | **Primary brand color (sky blue).** All headings (`h1, h2, h3`); nav-link hover background. | `h1, h2, h3 { color: #5da7e5 !important }`; `#portal-globalnav a:hover` |
| `#0E1D1C` | Main nav background — near-black with a green tint. | `#portal-globalnav { background-color: #0E1D1C }`; nav link bg |
| `#000000` | Globalnav wrapper background. | `#globalnav-wrapper { background-color: #000000 }` |
| `#FFFFFF` | Body fallback color, top/columns wrapper background, nav text, dividers. | `body { background: ... #FFFFFF }`; `#portal-top { background-color: #FFFFFF }`; nav link text |
| `#44687E` | **Footer background** (slate blue-grey). | `#portal-footer { background: ... #44687E }` |
| `#B7CCDA` | Footer body text color (cool grey-blue). | `#portal-footer { color: #B7CCDA }` |
| `#A9D8FD` | Footer rss/help link colors (pale blue). | `#portal-footer .rss`, `.help > a` |
| `#666` | Searchbox label color (medium grey). | `#portal-searchbox label { color: #666 }` |
| `#888` | `#searchGadget` placeholder text. | — |
| `#ccc` | `#searchGadget` border. | — |
| `#eb801f` | **Search button (orange).** | `.searchButton { background: #eb801f }` |
| `tomato` (`#FF6347`) | Search button hover. | — |

### Background image

| Asset | Use |
|-------|-----|
| `gis-back.png` (~262 KB tiled topographic map) | `body { background: url("gis-back.png") repeat fixed center top #FFFFFF !important }` — fixed, repeating across the entire viewport. The `#portal-top` and `#portal-columns` are white panels stacked over this map background, with a heavy drop shadow (`box-shadow: 0px 9px 18px rgba(50, 50, 50, 0.7)`) framing the white content card. This is the strongest visual signature of the GIS sub-site. |

### Inherited LP-wide globalnav palette (`ploneCustom.css`, may be visible in absence of gis.css overrides)

| Hex | Role |
|-----|------|
| `#657F9E` | Default `#portal-globalnav` bg (overridden to `#0E1D1C` by gis.css) |
| `#4C6C8C` | Default nav link hover bg (overridden to `#5DA7E5` by gis.css) |
| `#95A664` | Default selected nav tab bg (still active for selected tab) |
| `#efefef` | Submenu background |
| `#7d9cc0` | Submenu hover background |
| `#205C90` | Breadcrumb link color |
| `#2e76a0` | Default `#portal-footer` bg (overridden to `#44687E` by gis.css) |

### Inherited typography color (`ploneCustom.css`)

| Hex | Role |
|-----|------|
| `#8E6747` | Default heading color (overridden by gis.css `#5DA7E5 !important`) |
| `#444` | Body paragraph color (`p { color: #444 }`) |
| `#676767` | `.intro` color |
| `#666` | `.discreet` and bullets |

---

## Typography

### Fonts loaded (from `<link>` tags in HTML head)

```html
<link href="//maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet" />
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600|Source+Sans+Pro:400,700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Merriweather:400,400i,700|Montserrat:400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap" rel="stylesheet">
```

Loaded families: **Open Sans**, **Source Sans Pro**, **Merriweather**, **Montserrat**, **Material Icons**, **Nunito Sans**, **Public Sans**, plus Font Awesome 4.2.

> The gis-planning sub-site loads the same superset of fonts as every other LP sub-site (the link tags are sitewide chrome) but mostly references **Myriad Pro** (a non-web-loaded font) in `gis.css`. Browsers without Myriad Pro fall through to Helvetica → Arial → sans-serif, which is what most visitors see in practice.

### Font stacks by element

| Element | Font Family | Weight | Size | Color | Notes |
|---------|-------------|--------|------|-------|-------|
| `body` (global) | `'Open Sans', sans-serif` | 400 | ~95% (15.2px) | inherits | Set in `ploneCustom.css`; gis.css adds `font-size: 95%` |
| `h1, h2, h3` (gis override) | `"myriad-pro", helvetica, arial, sans-serif` | 500 | per heading | `#5DA7E5 !important` | `letter-spacing: -0.025em; line-height: 1.2em` |
| `h1.documentFirstHeading` (ploneCustom default, but color override applies) | `'Montserrat', sans-serif` | 500 | 36px | `#5DA7E5` | `margin: 1em 0 0.5em` |
| `h2` | (Myriad Pro stack via gis.css) | 500 | 30px | `#5DA7E5` | from ploneCustom |
| `h3` | (Myriad Pro stack via gis.css) | 500 | 24px | `#5DA7E5` | `margin-bottom: .5em; margin-top: 1em` |
| `p` | (inherits Open Sans) | 400 | 16px | `#444` | `line-height: 1.6em` (ploneCustom) |
| `#portal-globalnav li a` | `"myriad-pro", arial, sans-serif` | 600 | 1.2em (~19px) | `#fff` | `padding: 0.7em 0.9em; min-width: 2.5em; border-right: 0.1em solid white` |
| `#searchGadget` | inherits | — | inherit | `#888` placeholder | `border: 1px solid #ccc; border-radius: 4px; padding: 8px 10px; width: 17em` |
| `.searchButton` | inherits | — | — | `#fff` | `background: #eb801f; border-radius: 3px; padding: 7px 3px; margin-left: 5px` |
| `#portal-footer .rss`, `.help` | inherits | 700 (`bold`) | 15px | `#A9D8FD` | `letter-spacing: -0.05em` |
| `#portal-footer h3` (LP-wide) | inherits Montserrat from ploneCustom | — | 20px | `#aae2fd` | `text-transform: uppercase; margin: 17px 0 10px` |
| `.intro` (gis override) | inherits | — | 125% (~20px) | inherits | from gis.css |
| `#content li, dl.portlet li` (gis override) | inherits | — | inherits | inherits | `display: list-item; line-height: 1.5em; margin-bottom: 1em` |

### Inherited from ploneCustom

| Element | Font Family | Notes |
|---------|-------------|-------|
| `body` (LP-wide) | `'Open Sans', sans-serif` | with `background-image: url(blue-top-bar.png) repeat-x top` (gis.css then overrides with `gis-back.png`) |
| `#content .documentDescription, #content #description` | `'Montserrat', sans-serif`, weight 500 | `font-size: 1.35em; line-height: 1.5em` |
| Default heading (no gis override) | `'Montserrat', sans-serif`, weight 500 | `letter-spacing: -0.0125em; line-height: 1.5em; color: #8E6747` |

---

## Layout & Structure

### Page wrapper widths

| Element | Value | Source |
|---------|-------|--------|
| `#visual-portal-wrapper` max-width | `1170px` (centered, `margin: 0 auto`) | ploneCustom |
| `#portal-header` width | `1170px` (centered) | ploneCustom |
| `.narrow` (content wrapper) | `1170px` (centered) | ploneCustom |
| `.nest-nav-inner` (gis override) | `1140px` | gis.css |
| Mobile (≤1170px) | full-width (`width: 100%`) | ploneCustom |
| Mobile (≤768px) | full-width with `padding: 0 1rem` | ploneCustom |

### Header/banner heights

| Element | Value | Source |
|---------|-------|--------|
| `#portal-top` height | `260px` with `background-image: none` | gis.css (overrides default `blue-top-bar.png` chrome) |
| `#portal-banner` | `display: none` | gis.css (no banner photo on this sub-site — the visual identity is the tiled topo background, not a hero image) |
| `#portal-header` mobile height | `185px` (≤768px) | ploneCustom |
| `#portal-logo` | `display: inline-block; margin: 20px 20px 5px` | gis.css |

The home-page logo is a flat PNG (`gis-and-planning-logo.png`, 450×70) of the words "GIS & Conservation Planning" in light-blue serif/script lettering, placed inside `#portal-logo`. There is no background photo.

### Content region

| Element | Value | Source |
|---------|-------|--------|
| `#content` | `margin: 1em 2em !important` | gis.css |
| `#portal-column-two` | `padding-top: 2em` | gis.css |
| `#portal-top, #portal-columns` | `background-color: #FFFFFF` with `box-shadow: 0px 9px 18px rgba(50, 50, 50, 0.7)` | gis.css — these create the white content "card" floating over the tiled background |
| `#portal-breadcrumbs` | `padding-top: 10px` | gis.css |

### Footer layout

| Element | Value |
|---------|-------|
| `#portal-footer` | `background: #44687E; color: #B7CCDA; font-size: 75%; line-height: 2em; padding: 2em 1em; text-align: center` (gis.css). The deeper LP-shared structure (`.lp-footer`, `.grid-container-5col`, partner logos, link lists) inherits from ploneCustom. |
| `.grid-container-5col` (LP-wide) | `display: grid; grid-template-columns: repeat(5, 1fr); grid-gap: 20px` (collapses to single column ≤767px) |
| `.footer-left` (gis override) | `margin-left: 63px` desktop, `margin: 10px auto` ≤768px |

---

## Navigation

### Top-level globalnav (parent LP chrome — not gis-specific)

The gis-planning sub-site renders the parent `#portal-globalnav` from LP, but **gis.css disables several tabs**:

```scss
#portaltab-the-cooperative,
#portaltab-research,
#portaltab-projects,
#portaltab-home {
  display: none !important;
}
li#portaltab-child-home ul.submenu {
  display: none;
}
```

The visible globalnav looks slate-black with white serif/myriad text and an orange-on-blue hover; the captured snapshot shows the navbar is absent in screenshots — the styling targets the LP root nav, but on this sub-site the nav element is hidden because the captured pages enumerate sidebar items instead.

### Sidebar (`#portal-column-one` portlet `Sections`)

This is the canonical sub-site nav. Rendered as a Plone navigation portlet with three or four levels of nesting:

- Home → /maps-data/gis-planning
- Conservation Planning (5 children incl. Conservation Planning Webinars (1 grandchild))
- Tools & Resources (6 children, 2 with grandchildren and one with 6 great-grandchildren under Assessing Future Energy Development)
- Planning In Practice (3 children incl. Map Gallery with 15 grandchildren)
- Data (3 children incl. Public Data Repositories with 9 grandchildren and Species & Habitat Association List with 5 grandchildren)

### Nav link styling (gis.css)

| State | Properties |
|-------|------------|
| Default | `background: #0e1d1c`; `border-right: 0.1em solid white`; `font-family: "myriad-pro", arial, sans-serif`; `font-size: 1.2em`; `font-weight: 600`; `min-width: 2.5em`; `padding: 0.7em 0.9em`; color: white (inherited) |
| Hover | `background: #5DA7E5`; `color: White` |
| Selected | `background: #95A664` (LP default — not overridden by gis) |
| Submenu | `background: #efefef`; color `#333` |
| Submenu hover | `background: #7d9cc0 !important; color: #fff !important` |

### Search box (`#portal-searchbox`)

Placed absolutely at `right: 20px; top: 40px` (gis.css), with the search button branded orange (`#eb801f`, hover `tomato`).

### Personal tools

`#portal-personaltools-wrapper { right: 0; top: 210px }` (gis.css).

---

## Buttons

There are no dedicated button variants (`.btn-orange`, `.cta-button`, etc.) defined in `gis.css`. Buttons inherit LP-wide ploneCustom styles. The only sub-site-specific button-like control is the search button.

| Button | Background | Color | Other |
|--------|-----------|-------|-------|
| `.searchButton` (gis.css) | `#eb801f` | `#fff` | `border-radius: 3px; padding: 7px 3px; margin-left: 5px; border: medium none` |
| `.searchButton:hover` | `tomato` | `#fff` | — |
| `input.searchPage` | inherit | inherit | `font-size: 130% !important; margin-bottom: 15px; padding: 10px` |

Inherited LP-wide buttons (`.button`, `.featurebox .readmore a`, etc.) appear when content uses those classes; see `ploneCustom.css` for full styles.

---

## Content blocks

This sub-site's content pages are predominantly **plain bulleted/numbered lists with descriptive paragraphs** — there are no decorative content blocks, info cards, or hero panels in the captured HTML. The structural pattern is:

1. Breadcrumb (`#portal-breadcrumbs`).
2. `#content > article` containing:
   - `h1.documentFirstHeading` — page title.
   - `.documentByLine` — author + last-modified.
   - Body text with bullet lists, occasional `<table class="listing">`, occasional inline images.
3. Bottom: `.addthis_toolbox` (LP-wide social share).

The home page (#01) has a small intro paragraph ("The GIS & Conservation Planning Toolkit was designed by …") followed by three bullet lists each linking to a section landing.

---

## Footer

### Outer footer (`#portal-footer`, gis.css)

| Property | Value |
|----------|-------|
| Background | `#44687E` (slate blue) |
| Text color | `#B7CCDA` |
| Font size | `75%` |
| Line height | `2em` |
| Padding | `2em 1em` |
| Alignment | `text-align: center` |

Within `#portal-footer-inner` lives the LP-wide `.lp-footer` block (5-column partner logos + 3 link lists + dropdown jump menu), inherited unchanged from ploneCustom — see Layout above.

### Footer link colors

- `.rss`, `.help > a:link` → `#A9D8FD` (pale blue)
- `.help > a:hover` → `#5DA7E5` (the GIS primary)
- Footer headings (`h3`) → `#aae2fd` (LP-wide) `text-transform: uppercase; font-size: 20px`

### Bottom rule (LP-wide)

`<ul>` of: Site Map, Accessibility, Contact, Conditions of Membership — small font, white-on-slate.

---

## Responsive Breakpoints

The gis-planning sub-site stacks LP's breakpoints. Captured `@media` queries:

| Source | Breakpoint | Effect |
|--------|------------|--------|
| `gis.css` | `(max-width: 768px)` | `.footer-left { margin: 10px auto }` |
| `mobile.css` (legacy `handheld, screen and (max-device-width: 480px)`) | ≤480px | Hides `#portal-logo`; shrinks `#portal-globalnav` link padding; centers `#portal-searchbox`; stacks `#portal-column-one`, `#portal-column-two`, `#portal-column-content`; bumps form font sizes; widens `.overlay-iframe` |
| `ploneCustom.css` | `(max-width: 600px)` | `#content h1.documentFirstHeading, #content h1` → `font-size: 30px; line-height: 1.2em; margin-top: 0` |
| `ploneCustom.css` | `(max-width: 767px)` | `.grid-container-5col` collapses to block; many `.bg-*` hero blocks drop min-height; `#portal-footer .sitecredit` → `margin: 15px auto`; many decorative blocks reduce padding |
| `ploneCustom.css` | `(max-width: 768px)` | `.narrow { max-width: 100%; padding: 0 1rem }`; `#portal-top { background-image: none }`; `#portal-header { width: 100% }`; `#globalnav-wrapper { margin: 150px 0 0 }`; `#portal-header { height: 185px }`; many grid containers collapse to single column |
| `ploneCustom.css` | `(max-width: 979px)` | various `.right-portlet-partners` adjustments |
| `ploneCustom.css` | `(max-width: 1170px)` | `#portal-header, .narrow { width: 100% }` |

The LP standard responsive ladder is **480 / 600 / 767–768 / 979 / 1170**.

---

## Google Fonts

Loaded via `<link>` (full URLs above):

- **Open Sans** — 400, 400 italic, 600. Body text default.
- **Source Sans Pro** — 400, 700. Used by other sub-sites for nav/buttons (not heavily here).
- **Merriweather** — 400, 400 italic, 700. Used elsewhere for paragraph text — not active in gis sub-site (gis uses Open Sans for body).
- **Montserrat** — 400, 500, 600. Used by ploneCustom for headings (overridden by gis.css to Myriad Pro stack).
- **Material Icons** — for the icon system used in other sub-sites (not visible on gis pages).
- **Nunito Sans** — 400, 700, 400 italic.
- **Public Sans** — 300, 400, 700, 300 italic, 400 italic.
- **Font Awesome 4.2** — via maxcdn.

Effective for gis-planning: **Open Sans (body)** + **Myriad Pro stack (headings & nav, fallback to Helvetica/Arial)** + **Montserrat (description, byline)**.

---

## Print styles

`print.css` is loaded sitewide and contains a comprehensive `@media print` block. The gis-planning sub-site does **not** add any sub-site-specific print overrides.

Behaviors covered by sitewide `print.css`:

- Body sets `font-family: "Helvetica Neue", Arial, FreeSans, sans-serif`.
- Headings (`h1–h6`) bold, 125% line-height, `page-break-inside: avoid; page-break-after: avoid`. `h1, h2 { letter-spacing: -0.05em }`.
- Links: black, no underline, `border-bottom: 0.1em solid gray`.
- `.documentDescription` bold.
- `pre` 8pt with dotted black border.
- `table.listing` collapsed 1pt black borders, 6px cell padding.
- `div.pageBreak { page-break-before: always }`.
- `#portal-column-content { width: 95% / 100% (with overflow: hidden) }`; chrome elements hidden:
  ```
  div.top, #portal-logo, #portal-siteactions, .hiddenStructure, #portal-searchbox,
  #portal-globalnav, #portal-personaltools, #portal-breadcrumbs, #edit-bar,
  #portal-column-one, #portal-column-two, #portal-languageselector,
  .contentViews, .contentActions, .help, .legend, .portalMessage, .documentActions,
  .netscape4, #viewlet-below-content .reply, #viewlet-below-content .discussion,
  #kss-spinner, #review-history, #content-history, .listingBar, #portal-footer,
  #portal-colophon, .skipnav, .link-presentation, input.standalone, .overlay,
  .managePortletsFallback, .close, .link-parent, .draggingHook,
  #foldercontents-order-column, input.context, .visualNoPrint,
  .addthis_toolbox, #partnerSiteSelection
  { display: none }
  ```
- `.image-left`, `.image-right`, `.image-inline` get small black borders and floats.
- `dl.captioned { padding: 0.8em }`.
- `#content ul { list-style-image: url('bullet.gif'); list-style-type: square; margin-left: 2em; padding: 0 }`.
- No `@page` rule (page size and margins use browser defaults).

**Phase 3 implication:** the LP base `_print.scss` already covers the sitewide hides, link treatments, and content adjustments. The gis-planning sub-site has **no unique print elements** (no biome switcher, timeline, or custom hero), so `_custom-gis-planning.scss` should end with:

```scss
// Print styles: base _print.scss covers all needs for this sub-site.
```

---

## CSS files captured

| File | Bytes | Source URL | Notes |
|------|-------|-----------|-------|
| `reset.css` | 479 | `/portal_css/reset-cachekey-….css` | Tiny CSS reset |
| `base.css` | 69,987 | `/portal_css/base-cachekey-….css` | Plone Classic base list/heading/jQuery-UI styles |
| `tinymce.css` | 854 | `/portal_css/resourcetinymce.stylesheets…` | Editor styles |
| `print.css` | 2,486 | `/portal_css/print.css` | Sitewide print rules |
| `mobile.css` | 1,103 | `/portal_css/mobile-cachekey-….css` | Legacy ≤480px overrides |
| `contentleadimage.css` | 304 | `/portal_css/resourcecontentleadimage-….css` | Lead-image floats |
| `ploneCustom.css` | 131,733 | `/portal_css/ploneCustom.css` | **Sitewide LP brand layer** (every sub-site inherits this) |
| `gis.css` | 4,086 | `/maps-data/gis-planning/gis.css` | **Per-sub-site GIS overrides** |

---

## Images captured

| File | Source path | Use |
|------|------------|-----|
| `gis-and-planning-logo.png` | `/maps-data/gis-planning/gis-and-planning-logo.png` | Header `#portal-logo > img` (`<img alt="" src="gis-and-planning-logo.png" height="70" width="450">`). 450×70 light-blue wordmark "GIS & Conservation Planning". |
| `gis-back.png` | `/maps-data/gis-planning/gis-back.png` | `body { background: url("gis-back.png") repeat fixed center top #FFFFFF !important }`. Tiled topographic-map background pattern — the strongest visual identity element. |
| `working-lands-logo.png` | `/maps-data/gis-planning/working-lands/working-lands-logo.png` | Footer first column, partner logo (80px). |
| `nrcs-white-lockup.svg` | `/maps-data/gis-planning/nrcs-white-lockup.svg` | Footer first column, partner logo (340px). |
| `ebtjv-footer.png` | `/maps-data/gis-planning/ebtjv-footer.png` | Footer second column, partner logo (100px). |
| `sarp-logo-footer.png` | `/maps-data/gis-planning/sarp-logo-footer.png` | Footer second column, partner logo (110px). |
| `lp-logo-white.svg` | `/maps-data/gis-planning/landscape-images/lp-logo-white.svg` | Footer Contact column logo (230px). |

The captured images here are the seven that are unique or essential to the gis-planning sub-site identity. The footer also references many additional partner logos (e.g. `bobscapes-images/...`, `fire-images/...`, `birdlocale-images/...`, `literature-images/...`, etc.) but these belong to other LP sub-sites' footers and are present in markup conditionally — they are not part of the gis-planning visual identity and are captured under their respective sub-sites.

---

## Capture notes

- All 55 enumerated pages were reachable anonymously on production. No login walls encountered.
- **Page #20 (Energy Forecast Model)** is technically not a Plone document — its URL (`/web-map-viewers/energy%20forcast%20model`, with the typo "forcast") returns a 12-line HTML redirect placeholder pointing to `https://tnc-ps-web.s3.amazonaws.com/DevByDesign/lcc/lcc.html`. The HTML is captured as is, the screenshot shows the "If your browser doesn't automatically redirect…" fallback page (~14 KB). For replication, this is best handled as an external link rather than a styled Plone page.
- **Page #06 (Landscape-scale Conservation Planning)** is a sub-page under "Conservation Planning Webinars" — captured because it is the only enumerated sidebar entry under that branch.
- **Page #20's URL** uses a percent-encoded space (`/energy%20forcast%20model`) and a misspelling ("forcast" not "forecast") that's preserved in the production CMS. This is captured verbatim.
- The "Decision Support & Web Map Viewers" sub-tree (entries #19+) lists many entries that are external links (Data Basin, National Map, USGS pages, etc.) — those are external destinations, not gis-planning pages, and were not captured (per §1.1: external links are not part of sub-site nav for capture purposes).
- The "Public Data Repositories" sub-tree similarly lists external destinations (USGS, NOAA, etc.) — not captured as gis-planning pages.
- "Extensions and Other Tools" sub-tree (OpenLayers, MapServer) — external; not captured.
- The footer's partner-link list (Learn / Browse / Contact columns) points exclusively to LP-root paths (`/about`, `/networks`, etc.), not to gis-planning pages; these are not captured here.
- The home-page logo is a flat raster `gis-and-planning-logo.png` with no background. The site's branding "feel" comes almost entirely from `gis-back.png` (tiled topo) + the `#5DA7E5` light-blue heading color + the deep box-shadow framing the white content card.
- **No `:root` CSS custom properties exist** in `gis.css` — when scaffolding `_custom-gis-planning.scss` in Phase 2.3, the new theme should define semantic vars (`--gis-blue`, `--gis-nav-bg`, `--gis-footer-bg`, `--gis-search-orange`, etc.) since the source uses raw hex literals.
- Body has a heading typeface of `"myriad-pro"`, which is **not loaded** as a webfont — it falls through to Helvetica → Arial. The replication can either (a) accept that fallback, (b) substitute Source Sans Pro / Open Sans / Montserrat to keep the LP-wide font load, or (c) add a Myriad-Pro alternative. Recommend (b): use `'Source Sans Pro', sans-serif` or `'Montserrat', sans-serif` to match the LP shared font load.
- No errors were encountered during capture. All 55 desktop screenshots and 55 mobile screenshots are full-page captures (`fullPage: true`), with bottom-then-top scroll trigger before capture to fire any lazy-load images.

---
