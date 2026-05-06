# Equity & Inclusion — Style Guide

**Capture date:** 2026-05-05
**Source:** Wayback Machine archives (2023) — production site (`https://landscapepartnership.org/key-issues/equity-inclusion/`) is currently access-restricted (HTTP 401/Zope Unauthorized). All captured material is from publicly accessible Wayback Machine snapshots, mostly from June–December 2023.

---

## 1. Page Inventory

All 23 pages were captured successfully. HTML is in `html/`, desktop screenshots in `screenshots/NN-slug.png`, mobile screenshots in `screenshots/NN-slug-mobile.png`.

| # | Slug | Path | Display Name |
|---|------|------|--------------|
| 01 | `01-home` | `/` | Home |
| 02 | `02-about` | `/about` | About |
| 03 | `03-resources` | `/resources` | Resources |
| 04 | `04-resources-background` | `/resources/background` | Resources — Background |
| 05 | `05-resources-assistance` | `/resources/assistance` | Resources — Assistance |
| 06 | `06-resources-definitions` | `/resources/definitions` | Resources — Definitions |
| 07 | `07-resources-working-with-communities` | `/resources/working-with-communities` | Resources — Working with Communities |
| 08 | `08-community-hub` | `/community-hub` | Community Hub |
| 09 | `09-community-hub-collaborative` | `/community-hub/collaborative-initiatives` | Community Hub — Collaborative Initiatives |
| 10 | `10-community-hub-orgs` | `/community-hub/community-based-organizations` | Community Hub — Community Based Organizations |
| 11 | `11-training-webinars` | `/training-webinars` | Training & Webinars |
| 12 | `12-training-professional-dev` | `/training-webinars/professional-development` | Training — Professional Development |
| 13 | `13-training-online` | `/training-webinars/online-trainings` | Training — Online Trainings |
| 14 | `14-training-webinars-list` | `/training-webinars/online-trainings/webinars` | Training — Webinars List |
| 15 | `15-training-webinar-intro` | `/training-webinars/online-trainings/webinars/intro-to-ted-takeaways` | Training — Intro to TED Takeaways |
| 16 | `16-training-podcasts` | `/training-webinars/online-trainings/podcasts` | Training — Podcasts |
| 17 | `17-training-podcast-1` | `/training-webinars/online-trainings/podcasts/ted-takeaways-podcast-1-empathy-building-inclusive-teams` | Podcast 1 — Empathy |
| 18 | `18-training-podcast-2` | `/training-webinars/online-trainings/podcasts/ted-takeaways-podcast-2-working-with-diverse-communities` | Podcast 2 — Diverse Communities |
| 19 | `19-contact-info` | `/contact-info` | Contact Info |
| 20 | `20-sitemap` | `/sitemap` | Sitemap |
| 21 | `21-webinar-env-justice-history` | `/resources/background/webinar-environmental-justice-lessons-from-history-and-a-look-to-the-future` | Webinar — Environmental Justice History |
| 22 | `22-resources-resources` | `/resources/resources` | Resources — Resources |
| 23 | `23-training-programs` | `/training-webinars/training-programs` | Training Programs |

---

## 2. Color Palette

All colors sourced from `css/equity.css` (the sub-site-specific stylesheet) and `css/ploneCustom.css` (the shared LP site CSS).

### Primary Brand Colors (equity.css)

| Name | Hex | Usage |
|------|-----|-------|
| Brown/Rust (headings) | `#A26623` | H1–H6 heading color; primary brand accent |
| Dark Navy (nav bg) | `#0E1D1C` | Global nav background; nav link background |
| Olive Green (nest nav bar) | `#788A3B` | Return-to-parent "nest-navigation-bar" background |
| Muted Gold (selected nav) | `#DFDF9E` | Selected nav tab background |
| Hover Green (nav hover) | `#84984C` | Nav link hover background |
| Blue (portlet header) | `#205C90` | Navigation tree portlet header background |
| Dark Teal (edit bar) | `#84B3B3` | Edit bar / admin chrome background |
| Blue (footer) | `#2E76A0` | Portal footer background |

### Typography Colors

| Usage | Color | Hex |
|-------|-------|-----|
| Body/paragraph text | Medium grey | `#666` (via `rgb(102, 102, 102)`) |
| Intro text | Dark grey | `#676767` |
| H1 | Brown/rust | `#A26623` |
| H2–H6 | Brown/rust | `#A26623` |
| Nav background | Dark navy | `#0E1D1C` |
| Nav text (default) | White | `#FFFFFF` |
| Nav text (selected) | Very dark grey | `#222222` |
| Nav hover text | White | `#FFFFFF` |
| Footer background | Blue | `#2E76A0` |
| Footer text | White | `#FFFFFF` |
| Footer link (visited) | Light blue | `#7DD4D6` |
| Site credit text | Pale blue | `#AAE2FD` |
| Footer link hover | White | `#FFFFFF` |

### Style Guide Color Swatches (from equity.css `.STYLEGUIDE` section)

| Name | Hex | Class |
|------|-----|-------|
| Orange | `#F7931F` | `.orange` |
| Brown | `#A26623` | `.brown` |
| Dark Blue | `#205C90` | `.dark-blue` |
| Light Grey | `#F5F5F5` | `.light-grey` |
| Dark Grey | `#676767` | `.dark-grey` |
| Gold | `#F6D514` | `.gold` |
| Blue | `#6D97BF` | `.blue` |

### Additional Accent Colors (ploneCustom.css)

| Name | Hex | Usage |
|------|-----|-------|
| Orange | `#F7931F` | Readmore link hover; button hover |
| Warm orange | `#DD733E` | `.bg-orange` block backgrounds |
| Amber/orange | `#F59E20` | `.btn-solid-orange` button background |
| Dark orange hover | `#E64C00` | Button hover state |
| Gold circle bg | `#EFE48D` | Material icon gold circles |
| Orange hover | `#F19023` | Circle icon hover |
| Warm orange 2 | `#F38B1A` | CTA button hover |
| Dark teal (CTA block) | `#28526E` | `#cta-block` background |
| Gold (CTA banner) | `#F7BD4F` | CTA banner background |
| Page bg | `#FFFFFF` | Body background |

---

## 3. Typography

### Font Families

All fonts are loaded from Google Fonts:

```
https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600|Source+Sans+Pro:400,700&display=swap
https://fonts.googleapis.com/css?family=Merriweather:400,400i,700|Montserrat:400,500,600&display=swap
https://fonts.googleapis.com/icon?family=Material+Icons
https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,wght@0,400;0,700;1,400&display=swap
https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap
```

| Role | Family | Weights |
|------|--------|---------|
| Body text | Open Sans | 400, 400i, 600 |
| Paragraph/intro text | Merriweather (serif) | 400, 400i, 700 |
| Headings (H1–H6) | Montserrat | 400, 500, 600 |
| Portlet headers | Montserrat | 400, 500, 600 |
| Nav links | Montserrat | 600 |
| Read more links | Source Sans Pro | 600 |
| Icons | Material Icons | (icon font) |

### Heading Styles

| Tag | Font | Size | Weight | Color | Line Height |
|-----|------|------|--------|-------|-------------|
| H1 (documentFirstHeading) | Montserrat | 2.6em (~41.6px) | 500 | `#A26623` | default |
| H1 | Montserrat | 2.6em (~41.6px) | 500 | `#A26623` | default |
| H2 | Montserrat | 30px (computed) | 600 | `#A26623` | 1.5em |
| H3 | Montserrat | 24px (computed) | 600 | `#A26623` | 1.5em |
| H4–H6 | Montserrat | 16px+ | 600 | `#A26623` | 1.5em |

Additional heading styles (from letter-spacing): `letter-spacing: -0.0115em`

**Mobile H1:** `margin-top: 0` at max-width 767px

### Body Text

```css
p {
    font-family: 'Merriweather', serif;
    color: #666;
    letter-spacing: 0.01em;
    line-height: 1.6em;
    padding-bottom: 15px;
}
```

### Intro/Lead Text

```css
.intro {
    font-family: 'Merriweather', serif;
    font-size: 17px;
    line-height: 1.7em;
    color: #676767;
    margin: 1em 0;
}
```

### Read More Links

```css
a.readmore {
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    font-family: 'Source Sans Pro', sans-serif;
}
a.readmore:hover { color: #f7931e; }
```

### Tile/Listing Headlines

```css
.tileHeadline {
    font-size: 1.5em;
    font-weight: 600;
}
```

---

## 4. Layout & Structure

### Page Wrapper

```css
#visual-portal-wrapper {
    background-color: #fff;
    margin: 0 auto;
    max-width: 100%;
    min-height: calc(100vh - 190px);
}
```

### Main Content Columns

```css
#portal-columns {
    position: relative;
    width: 1170px;
    margin: 20px auto;
}
@media only screen and (max-width: 1169px) {
    #portal-columns { width: 100%; }
}
```

### Header Height

```css
#portal-top {
    height: 164px;
}
@media only screen and (max-width: 768px) {
    #portal-top { height: 130px; }
}

#portal-header {
    width: 100%;
    height: 150px;
}
```

### Logo

```css
#portal-logo img {
    width: 480px;
    position: relative;
    top: 20px;
    left: 15%;
    transition: all .3s ease-in-out;
}
@media only screen and (max-width: 768px) {
    #portal-logo {
        margin: 0;
        top: 65px;
        position: absolute;
    }
    #portal-logo img {
        width: 330px;
        height: auto;
        left: 5%;
        top: -40px;
    }
}
```

Logo file: `lp-equity-logo.svg` (saved in `images/`)

### Banner Images (Section-Specific)

The site uses section-level CSS classes on `<body>` to set per-section hero banners:

| Body Class | Banner Image | Height |
|-----------|-------------|--------|
| `.site-equity-inclusion` (home) | White background, no image | 30px |
| `.section-resources` | `iStock-1283449654.jpg` | 500px |
| `.section-training-webinars` | `iStock-1226958325.jpg` | 500px |
| `.section-community-hub` | `acoma-pueblo/image` | 500px |
| `.section-equity-inclusion-notes` | `epic-ranch-goat-farm` | 500px |
| `.section-organizations-initiatives-1` | `buffalo-and-barbed-wire.jpg` | 500px |
| `.template-equity_home` | Hidden (`display: none`) | — |

Mobile banner height: `200px` at max-width 768px, `top: 35px`.

### Content Sidebar

```css
#portal-column-one {
    position: relative;
    top: 6em;
}
#portal-column-two {
    position: relative;
    top: 2em;
}
```

### Breadcrumbs

```css
#portal-breadcrumbs {
    font-size: 85%;
    margin: 1.5em auto 2em;
}
/* Hidden on home template */
.template-equity_home #portal-breadcrumbs { display: none; }
```

---

## 5. Navigation

### Return-to-Parent Bar (Nest Navigation Bar)

A thin olive-green bar at the very top of the page linking back to the parent LP site:

```css
.nest-navigation-bar {
    background: #788a3b;
    display: block;
    padding: 5px 40px;
}
.nest-navigation-bar img {
    width: 320px;
}
.nest-nav-inner {
    margin: 0 auto;
    width: 100%;
    padding: 1px 30px;
}
@media only screen and (max-width: 768px) {
    .nest-navigation-bar { padding: 5px 0px; }
    .nest-nav-inner { padding: 1px 5px; }
}
```

The bar contains:
- A logo image linking back to `https://landscapepartnership.org/`
- A "Navigate Target Species" dropdown (shared LP chrome — not equity-specific)

### Global Navigation

```css
#globalnav-wrapper {
    background-color: #0E1D1C;
    border-bottom: none;
    border-top: 1px solid white;
    top: 160px;
}
#portal-globalnav {
    background-color: #0E1D1C;
}
#portal-globalnav li a {
    background-color: #0E1D1C;
    font-size: 16px;
    font-family: 'montserrat', sans-serif;
    font-weight: 600;
}
#portal-globalnav .selected a {
    background: #DFDF9E;
    color: #222 !important;
}
#portal-globalnav a:hover,
#portal-globalnav .selected a:hover {
    background: #84984c;
    color: #fff;
}
#portal-globalnav ul.submenu a {
    font-weight: 400;
}
```

### Sub-site Navigation (second-level tabs)

The equity sub-site has its own tab bar below the main LP navigation. Top-level tabs and their sub-pages:

- **Home**
- **Resources** → Background | Definitions | Assistance | How to work with communities
- **Community Hub** → Collaborative Initiatives | Community-Based Organizations
- **Training & Webinars** → Professional Development | Online Trainings (Webinars, Podcasts) | Training Programs
- **About**
- **Contact Info**

### Personal Tools

```css
#portal-personaltools-wrapper {
    right: 30px;
    top: -35px;
    position: absolute;
}
#portal-personaltools a { color: #fff; }
#portal-personaltools a:visited { color: #a9e1f3 !important; }
```

---

## 6. Buttons

### Generic Button

```css
.button {
    color: #54585b;
    font-size: 1.125rem;
    padding: .75rem 1rem;
    margin-bottom: 0.1875rem;
    display: inline-block;
    text-decoration: none;
    border: 1px solid #888;
    border-radius: 0.25rem;
    text-align: center;
    font-weight: 700;
    transition: background .2s linear, color .2s linear, border-color .2s linear;
    font-family: "Open Sans", Arial, sans-serif;
    box-shadow: 2px 3px 5px -1px rgba(0, 0, 0, 0.35);
}
.button:hover {
    border-color: transparent;
    background: #e64c00;
    color: #ffffff;
}
```

### Solid Orange Button

```css
.btn-solid-orange {
    color: #ffffff !important;
    background: #F59E20;
    border-color: transparent;
}
#content a.btn-solid-orange:hover {
    background: #e64c00;
    color: #ffffff !important;
    border-color: transparent;
}
a.btn-solid-orange:visited { color: #fff !important; }
```

### CTA Button (from ploneCustom.css)

```css
#cta-block {
    background-color: #28526E;
}
.cta-button { background: #f7bd4f; }
#content .cta-button a {
    color: #fff;
    font-family: 'Montserrat';
}
#content .cta-button a:hover {
    background: #f38b1a;
}
```

---

## 7. Content Blocks

### Portlets

```css
dl.portlet {
    font-size: 90%;
    border: 1px solid #ddd;
    border-radius: 6px;
    margin-bottom: 1.5em;
}
dl.portlet dt {
    padding: 1em 1em 0.25em;
    background: transparent;
    line-height: normal;
    color: #666;
    font-family: 'Montserrat', sans-serif;
    font-size: 17px;
}
.portletNavigationTree .portletHeader {
    background: #205C90;
    border-radius: 4px 4px 0 0;
    text-transform: uppercase;
    padding: 15px;
}
```

### Slide Overlay (Hero/Banner Overlays)

```css
.slide-overlay {
    position: absolute;
    z-index: 5;
    top: 35%;
    background: rgba(0, 0, 0, 0.6);
    padding: 30px 30px 40px;
    width: 60%;
    left: 20%;
    color: #fff;
    border-radius: 6px;
    text-align: center;
}
@media only screen and (max-width: 768px) {
    .slide-overlay {
        top: 0;
        background: rgba(0, 0, 0, 0.45);
        width: 100%;
        left: 0;
        border-radius: 0;
    }
}
```

Left-aligned variant: `.slide-overlay-left` — 38% width, positioned 2% from left, 30% from top.

### Tile/Listing Items

```css
.tileItem { clear: both; }
.tileHeadline { font-size: 1.5em; font-weight: 600; }
.tileImage img { width: 280px; height: auto; }
```

### Image Captions

```css
.caption {
    padding: 0 0 10px;
    color: #777;
    font-size: 13px;
}
dd.image-caption {
    color: #666;
    font-size: 100%;
    max-width: 100%;
    padding: 20px;
    text-align: center;
}
```

### Tables

```css
#content table.listing {
    width: 100%;
}
```

### Edit/Admin Bar (Plone chrome)

```css
#edit-bar {
    background-color: #84B3B3;
    border: 0.25em solid #84B3B3;
}
#contentActionMenus { background: #84B3B3; }
#content-views { background-color: #84B3B3; }
```

---

## 8. Footer

The LP shared footer (`#portal-footer`) is used; no equity-specific footer override is defined (the commented-out block in `equity.css` shows it was considered but not applied).

```css
#portal-footer {
    background: #2e76a0;
    color: #fff;
    width: 100%;
    padding: 1.5em;
}
#portal-footer p {
    padding-left: 15px;
    color: #fff;
    font-size: 12px;
}
#portal-footer h3 {
    color: #aae2fd;
    font-size: 20px;
    margin: 17px 0 10px;
}
#portal-footer .ft-menu li a {
    color: #9adff1;         /* footer nav links */
}
#portal-footer .ft-menu li a:hover {
    color: #FFA64D !important;  /* orange hover */
}
#portal-footer .sitecredit a {
    color: #7dd4d6 !important;
}
#portal-footer .sitecredit a:hover { color: #ffffff !important; }
```

### Footer Navigation Links

- About Us
- Members
- Community
- Issues
- Help
- Browse Projects
- Maps and Data
- News and Events
- Resources
- Training
- Contact

### Items Hidden by equity.css

```css
#jumpmenu, .rss, .rss-feeds, .footer-mid, .footer-rt { display: none; }
```

---

## 9. Responsive Breakpoints

All breakpoints from `equity.css` and `ploneCustom.css`:

| Breakpoint | CSS Rule | Elements affected |
|------------|----------|-------------------|
| `max-width: 1169px` | `#portal-columns { width: 100%; }` | Main content container |
| `max-width: 768px` | Multiple rules | Banner heights (→200px), logo size/position, nav wrapper position, search box, nest-nav padding, addthis toolbox, flex layout stacking, image captions full-width, `#content { padding: 0 1em }` |
| `max-width: 767px` | `#content h1 { margin-top: 0 }`, footer sitecredit centering | Heading top margin, footer credit |
| `max-device-width: 480px` (handheld) | Mobile CSS import | Shared mobile overrides |
| `print` | `print.css` | Print layout (see §11) |

Mobile breakpoint is **768px** (primary), **1169px** (container), and **767px** (heading adjustment).

---

## 10. Google Fonts

Five font families are loaded, all from Google Fonts:

| Family | Weights/Styles | Usage |
|--------|---------------|-------|
| Open Sans | 400, 400i, 600 | Body base font; form labels; general UI text |
| Source Sans Pro | 400, 700 | Read-more links |
| Merriweather | 400, 400i, 700 | Paragraph body text; intro/lead text |
| Montserrat | 400, 500, 600 | All headings (H1–H6); navigation links; portlet headers; CTA button text |
| Nunito Sans | 400, 400i (italic), 700 | Loaded but not explicitly cited in equity.css — may be used in content blocks |
| Public Sans | 300, 400, 700 (all italic variants too) | Loaded but not explicitly cited in equity.css |
| Material Icons | (icon font) | Material design icons used in content blocks |

---

## 11. Print Styles

Print styles come entirely from the shared `print.css` (no equity-specific `@media print` blocks in `equity.css`).

### Font Override

```css
@media print {
    body {
        font-family: "Helvetica Neue", Arial, FreeSans, sans-serif;
    }
    h1, h2, h3, h4, h5, h6 {
        font-family: "Helvetica Neue", Arial, FreeSans, sans-serif;
        font-weight: bold;
        line-height: 125%;
        page-break-inside: avoid;
        page-break-after: avoid;
    }
    h1, h2 { letter-spacing: -0.05em; }
}
```

### Links

```css
a {
    text-decoration: none;
    border-bottom: 0.1em solid gray;
    color: black;
}
```

### Hidden Elements (print)

The following are hidden in print:

- `div.top` — page top bar
- `#portal-logo` — site logo
- `#portal-siteactions` — site actions
- `.hiddenStructure`
- `#portal-searchbox`
- `#portal-globalnav` — navigation
- `#portal-personaltools`
- `#portal-breadcrumbs`
- `#edit-bar`
- `#portal-column-one` and `#portal-column-two` — sidebars
- `#portal-languageselector`
- `.contentViews`, `.contentActions`
- `.help`, `.legend`
- `.portalMessage`
- `.documentActions`
- `.listingBar`
- `#portal-footer`, `#portal-colophon`
- `input.standalone`, `.overlay`, `.close`, `.managePortletsFallback`
- `input.context`
- `.visualNoPrint`

### Content Area in Print

```css
#portal-column-content {
    width: 95%;
    overflow: hidden;
}
```

### Tables in Print

```css
table.listing, table.listing td { border: 1pt solid black; border-collapse: collapse; }
table.listing td, table.listing th { padding: 6px; }
```

### Lists in Print

```css
#content ul {
    list-style-image: url('bullet.gif');
    list-style-type: square;
    margin-left: 2em;
    padding: 0;
}
```

**Note:** No sub-site-specific `@media print` rules exist. The shared `print.css` covers all print needs for this sub-site.

---

## 12. Captured CSS Files

| File | Source | Notes |
|------|--------|-------|
| `equity.css` | Sub-site specific | THE primary reference file — all equity-specific overrides |
| `ploneCustom.css` | Shared LP site | Large shared stylesheet; contains LP-wide colors, footer, content blocks |
| `print.css` | Shared LP site | Print stylesheet |
| `slick.css` | Plugin | jQuery Slick carousel/slider CSS |
| `banner-styles.css` | Wayback Machine UI | Archive.org banner styles — not part of original site |
| `iconochive.css` | Wayback Machine UI | Archive.org icon styles — not part of original site |

Note: Several portal_css files (reset, base, mobile, tinymce) were unavailable (HTTP 404 on production; cached-key URLs expired). These use the same base styles as other LP sub-sites.

---

## 13. Captured Images

| File | Type | Usage |
|------|------|-------|
| `lp-equity-logo.svg` | SVG logo | Site header logo (the equity sub-site specific logo) |
| `lp-logo-white.svg` | SVG logo | LP parent site white logo (footer) |
| `wlfw-logo.png` | PNG logo | Working Lands for Wildlife logo |
| `working-lands-logo.png` | PNG logo | Working Lands wordmark |
| `nrcs-transparent.png` | PNG logo | USDA NRCS partner logo |
| `USDA-NRCS-white.png` | PNG logo | USDA NRCS white version |
| `ebtjv-footer.png` | PNG logo | EBTJV partner footer logo |
| `sarp-logo-footer.png` | PNG logo | SARP partner footer logo |
| `northern-bobwhite-logo-footer.png` | PNG logo | Northern Bobwhite partner logo |
| `QF-logo.png` | PNG logo | Quail Forever partner logo |
| `gamelabmartin-footer.png` | PNG logo | Game Lab Martin footer logo |
| `logo-bobscapes-white-type.png` | PNG logo | Bobscapes white type logo |
| `GEORGIA-logo-footer.png` | PNG logo | Georgia footer logo |
| `birdlocale-logo-rounded.png` | PNG logo | BirdLocale rounded logo |

---

## 14. Key Structural Notes for Plone 6 Replication

1. **Logo**: The site logo (`lp-equity-logo.svg`) is an SVG, positioned relatively within `#portal-logo` with `left: 15%`. This is significantly wider (480px) than typical LP sub-site logos.

2. **Nav color scheme**: Dark near-black navy (`#0E1D1C`) is unique to this sub-site — most other LP sub-sites use greens, teals, or forest colors. The olive-green return bar (`#788A3B`) is also equity-specific.

3. **Heading color**: Brown/rust `#A26623` throughout all headings — this is distinct from other LP sub-sites (which often use greens, blues, or oranges).

4. **Body text**: Merriweather (serif) for paragraph text is unusual — most LP sub-sites use Open Sans or Source Sans Pro for body text.

5. **No sub-site-specific footer**: The equity sub-site uses the standard LP footer unchanged. No custom footer panels or logos.

6. **Home template hides**: Banner, breadcrumbs, title, byline, and edit bar are all hidden on `.template-equity_home`. This suggests the home page is a custom full-width template.

7. **Section body classes**: The original site relies heavily on Plone body classes like `.site-equity-inclusion`, `.section-resources`, `.section-community-hub`, `.section-training-webinars` to control banner images and layout per section. These map to Plone 6 body classes from the content path structure.

8. **Portlet navigation tree**: Uses a distinctive blue header `#205C90` for the nav tree portlet, serving as a sidebar table of contents on most pages.

9. **No CSS custom properties (`--vars`)**: This is a Plone 4/5-era site — all colors are hardcoded hex values, not CSS custom properties. When porting to Plone 6, all colors should be declared as CSS custom properties in `:root`.
