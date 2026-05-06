# Ecosystem Benefits & Risks — Style Guide

Sub-site slug: `ecosystem-risks-benefits`
Production URL: https://landscapepartnership.org/ecosystem-risks-benefits
Captured: 2026-05-04

This style guide is derived from a fresh Phase 1 capture of the live production sub-site. Sources:
- `html/` — full page HTML for every nav-reachable page
- `css/` — every linked stylesheet from the home page (sub-site CSS, Plone portal CSS, Font Awesome)
- `images/` — sub-site-specific design imagery (background, header band, logos, icons) plus LP-wide logos
- `screenshots/` — full-height desktop (1280px) and mobile (375px) captures for every enumerated page

The sub-site is a Plone Classic site that sits inside the larger `landscapepartnership.org` portal. Visual identity is defined chiefly by `ecoss.css` (loaded after `ploneCustom.css`), which overrides the LP-wide chrome with a navy-and-teal palette layered over a fixed full-bleed photographic background.

---

## 1. Page inventory

24 pages were enumerated and captured. Every nav-reachable URL (top-level nav, sub-nav, footer links) is included. No sampling — every distinct layout variant in the site's chrome is represented.

| #  | Page name                              | URL path                                                                     | Notes |
|----|----------------------------------------|------------------------------------------------------------------------------|-------|
| 01 | Home                                   | `/ecosystem-risks-benefits`                                                  | Landing page; 2x3 feature card grid + lead paragraphs |
| 02 | About                                  | `/ecosystem-risks-benefits/about`                                            | Section landing |
| 03 | Partners                               | `/ecosystem-risks-benefits/about/partners`                                   | Long-form partner directory (largest page) |
| 04 | Benefits                               | `/ecosystem-risks-benefits/key-ecosystem-services`                           | Section landing for "Key Ecosystem Services" |
| 05 | Water and soils                        | `/ecosystem-risks-benefits/key-ecosystem-services/water`                     | Detail page with hero photo |
| 06 | Harvested species                      | `/ecosystem-risks-benefits/key-ecosystem-services/harvested-species`         | Detail page |
| 07 | Landscape values and sense of place    | `/ecosystem-risks-benefits/key-ecosystem-services/landscape-values-and-sense-of-place` | Detail page |
| 08 | Forest carbon                          | `/ecosystem-risks-benefits/key-ecosystem-services/forest-carbon`             | Detail page |
| 09 | Risks                                  | `/ecosystem-risks-benefits/risks`                                            | Section landing |
| 10 | Urbanization                           | `/ecosystem-risks-benefits/risks/urbanization`                               | Detail page |
| 11 | Energy development                     | `/ecosystem-risks-benefits/risks/energy-development`                         | Detail page |
| 12 | Invasive species and forest pathogens  | `/ecosystem-risks-benefits/risks/invasive-species-and-forest-pathogens-1`    | Detail page |
| 13 | Climate change                         | `/ecosystem-risks-benefits/risks/climate-change-1`                           | Detail page |
| 14 | Wildland fire                          | `/ecosystem-risks-benefits/risks/wildland-fire`                              | Detail page |
| 15 | The Human Landscape                    | `/ecosystem-risks-benefits/human-landscape-1`                                | Section landing |
| 16 | Demographics and Social Values         | `/ecosystem-risks-benefits/human-landscape-1/demographics-and-social-values` | Detail page |
| 17 | Economics and Business                 | `/ecosystem-risks-benefits/human-landscape-1/economics-and-business`         | Detail page |
| 18 | Land Use                               | `/ecosystem-risks-benefits/human-landscape-1/land-use`                       | Detail page |
| 19 | Assessments                            | `/ecosystem-risks-benefits/appalachian-assessments`                          | Listing of assessment links |
| 20 | Framework                              | `/ecosystem-risks-benefits/vulnerability-assessment`                         | Section landing |
| 21 | Tools & Resources                      | `/ecosystem-risks-benefits/tools-resources`                                  | Resource listing |
| 22 | Sitemap                                | `/ecosystem-risks-benefits/sitemap`                                          | Auto-generated nested list |
| 23 | Accessibility                          | `/ecosystem-risks-benefits/accessibility-info`                               | Plone-default text page |
| 24 | Contact                                | `/ecosystem-risks-benefits/contact-info`                                     | Contact form (captcha image) |

### Capture notes / unreachable pages

- **"Conditions of Membership"** — the footer link points to `/ecosystem-risks-benefits/resources/help-1/how-to-participate/conditions-of-membership`. This URL returns **HTTP 404** on production (and the sibling `/resources/help-1/...` path also 404s). The link is broken on the live site; it could not be captured. Other LP sub-sites resolve this link successfully, suggesting the `resources/help-1` content tree was not duplicated under the ecosystem-risks-benefits sub-site.
- **External "Tools & Resources" sub-nav items** ("Ecosystem Benefits and Risks Final Narrative" and "LanDat Assessment Tool") point to `applcc.org` — out of scope for sub-site theme capture.
- **External hero feature links** on the home page ("Ecosystem Services Conservation Atlas" → `applcc-ecosystemservices.org`, "Conservation Design" → `applcc.databasin.org`) are external and not captured as sub-site pages.
- **`return-to-LP` banner link** at the very top points to the parent portal home — out of scope here.

---

## 2. Color palette

The sub-site's distinctive palette is defined inline in `css/ecoss.css` (no CSS custom properties were declared — values are literal hex). Cross-site chrome from `ploneCustom.css` contributes additional colors used in the footer and links.

### Sub-site core (from `ecoss.css`)

| Color           | Hex        | Usage |
|-----------------|------------|-------|
| Deep navy       | `#173145`  | Global nav background; nav link background; hover text color |
| Deep navy alt   | `#173245`  | Body background fallback (under the bg image) — virtually identical to `#173145` |
| Heading blue    | `#205c90`  | All headings (`h1`–`h4`); breadcrumb links (also from ploneCustom) |
| Selected teal   | `#5b9a9a`  | `#portal-globalnav .selected a` background |
| Hover teal      | `#69ABBB`  | Nav link hover background |
| Accent orange   | `#EB801C`  | Search button background |
| Hover orange    | `tomato` (`#FF6347`) | Search button hover |
| White           | `#fff`     | Page card background (`#portal-columns`); link/text on dark |
| Text grey       | `#676767`  | `.intro` lead text |
| Caption grey    | `#777`     | `dd.image-caption` |
| Border grey     | `#999`     | Search input border |
| Soft grey       | `#cccccc`  | `.image-inline` border |
| Drop-shadow     | `rgba(50, 50, 50, 0.41)` | `#visual-portal-wrapper` box-shadow |

### Footer / global chrome (from `ploneCustom.css`)

| Color           | Hex        | Usage |
|-----------------|------------|-------|
| Footer blue     | `#2e76a0`  | `#portal-footer` background |
| Footer link cyan| `#7dd4d6`  | `#portal-footer .sitecredit a` |
| Footer light cyan | `#aae2fd`| `.sitecredit` text |
| Footer help link  | `#9adff1`| `#portal-footer .help a:link` |
| Footer help hover | `#FFA64D`| `#portal-footer .help a:hover` |
| Heading dark    | `#17455e`  | Footer "RSS" / "HELP" labels |

### Background imagery

The body background is an opaque navy with a fixed photographic overlay:
```
body {
  background: url("ecoss-images/ecoss-bg.jpg") no-repeat center center fixed #173245 !important;
  background-size: cover !important;
}
```
Image: `images/ecoss-bg.jpg` (162 KB JPEG). This produces the green-blue forested mountain scene visible behind the white page card on every page.

A 1px-tall PNG (`portal-header-bg.png`, 180 bytes) repeats horizontally to draw a subtle band across the top of `#portal-top` (240 px tall).

---

## 3. Typography

### Loaded Google Fonts (from `<head>` of every page)

```html
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600|Source+Sans+Pro:400,700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Merriweather:400,400i,700|Montserrat:400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap" rel="stylesheet">
```

The portal-wide `<head>` requests five Google Fonts families. The ecosystem-risks-benefits sub-site only actually uses **Open Sans** (and **Material Icons** for material-icon ligatures used elsewhere in the portal — not visible on this sub-site's pages).

### Body type

- **Family:** `'Open sans', sans-serif` (declared in `ploneCustom.css` line 8 — note the lowercase variant; `ecoss.css` separately declares `'Open Sans', sans-serif` on headings)
- **Line-height:** `1.5em` (body)
- **Base size:** browser default (`100%` set on `#content` in ecoss.css)

### Headings

`ecoss.css` overrides h1–h4 globally:
```css
h1, h2, h3, h4 {
  color: #205c90;
  font-family: 'Open Sans', sans-serif;
  font-weight: 600;
  letter-spacing: -0.0115em;
  line-height: 1.2em;
  margin-bottom: 10px;
}
```

### Lead / intro text

```css
.intro {
  color: #676767;
  font-size: 1.3em;
  font-weight: 300;
  line-height: 1.4em;
  margin: 1em 0;
  -webkit-font-smoothing: antialiased;
}
```

### Image caption

```css
dd.image-caption {
  color: #777;
  font-size: 11pt;
  line-height: 1.3em;
  margin: 6px 15px 10px !important;
  max-width: 92%;
}
```

### Other type observations

- `ploneCustom.css` declares additional families that are **not** used on this sub-site's pages but are loaded portal-wide: `Merriweather` (serif, used by other LP sub-sites), `Montserrat` (used by working-lands-for-wildlife etc.), `Source Sans Pro`, `myriad-pro`. These are only relevant if the theme ever needs to render content authored on a sibling sub-site.

---

## 4. Layout & structure

The site is centered on a **1000px-wide white card** floating over a full-bleed fixed photographic background.

| Element                  | Width / Height | Notes |
|--------------------------|----------------|-------|
| `#visual-portal-wrapper` | `max-width: 1000px`; centered (`margin: 0 auto`); `min-height: calc(100vh - 190px)` | Box-shadow `0 10px 20px rgba(50, 50, 50, 0.41)` — provides the floating card effect |
| `#portal-header`         | `width: 1000px`; transparent background | |
| `#portal-top`            | `height: 240px`; `background: url(ecoss-images/portal-header-bg.png) repeat-x 0 15px` | Top band; logo sits inside |
| `#portal-logo`           | `display: block; margin: 50px 0 30px` | Asset: `images/ecoss-logo.png` (24 KB PNG) |
| `#globalnav-wrapper`     | `width: 1000px`; `background-color: #173145`; `top: 127px` (within header) | |
| `#portal-globalnav`      | `background-color: #173145`; `justify-content: left` | Flex row |
| `#portal-columns`        | `background-color: #fff; padding-top: 10px` | Three-column page body (left col, content, right col) |
| `#portal-searchbox`      | Absolute-positioned (`top: 75px`); `margin-top: -73px`; `padding: 10px`; `border-radius: 6px`; `background: url(black55.png) repeat` (semi-transparent black) | |
| `#portal-personaltools-wrapper` | Absolute; `right: 0; top: 197px` | |
| `#portal-footer-inner`   | `max-width: 1000px !important` | |
| `#content`               | `margin: 2em` | |

### Page-level shape (vertical)

```
+-------- ecoss-bg.jpg (fixed, behind everything) --------+
|                                                          |
|  RETURN TO LANDSCAPE PARTNERSHIP SITE    (LP-wide bar)   |
|                                                          |
|  +---- #visual-portal-wrapper (1000px, white) ----+     |
|  |  #portal-top  (240px tall, header-bg band)     |     |
|  |    [ecoss-logo.png]                            |     |
|  |    [Sections heading + searchbox top-right]    |     |
|  |  #globalnav-wrapper (navy bar)                 |     |
|  |  #portal-columns                               |     |
|  |    .breadcrumb                                 |     |
|  |    h1 / byline / content                       |     |
|  |    "Filed under" tags                          |     |
|  +-----------------------------------------------+      |
|                                                          |
|  #portal-footer  (LP-wide blue bar)                     |
|                                                          |
+----------------------------------------------------------+
```

---

## 5. Navigation

### Global nav

Lives in `#globalnav-wrapper > #portal-globalnav`. Top-level items are the section roots: Home, About, Benefits (Key Ecosystem Services), Risks, The Human Landscape, Assessments, Framework, Tools & Resources.

```css
#globalnav-wrapper {
  background-color: #173145;
  margin-top: 15px;
  margin-bottom: 10px;
  top: 127px;          /* relative to header */
  width: 1000px;
}
#portal-globalnav { background-color: #173145; justify-content: left; }
#portal-globalnav li a {
  background: #173145;
  font-size: 1.1em;
  font-weight: normal;
  min-width: 2.5em;
  padding: 0.85em 1.1em;
}
#portal-globalnav li a:hover {
  background: #69ABBB;
  color: #173145 !important;
}
#portal-globalnav .selected a {
  background: #5b9a9a;
}
```

The nav has **no dropdown / submenu UI** — child pages are listed in the left sidebar (`#portal-column-one`) instead. Submenus that other LP sub-sites use are explicitly hidden:
```css
li#portaltab-home ul.submenu,
li#portaltab-child-home ul.submenu { display: none; }
#portaltab-the-cooperative,
#portaltab-research,
#portaltab-projects { display: none !important; }
```

### Sidebar (sub-nav)

The "Sections" navigation portlet on the left column lists the full hierarchy. Sub-items appear nested under their parent (e.g. "Benefits → Water and soils, Harvested species, …"). All styling here comes from the LP-wide `ploneCustom.css` and Plone defaults.

### Breadcrumbs

```css
#portal-breadcrumbs a { color: #205C90; }
```

The "RETURN TO LANDSCAPE PARTNERSHIP SITE" bar is an LP-wide horizontal banner at the very top that links back to the parent portal.

### Personal tools

`#portal-personaltools-wrapper` is absolutely-positioned at `right: 0; top: 197px` — login / register icons in the top-right corner of the white card.

---

## 6. Buttons

The sub-site has very few button variants — most CTA-style links are inline or are the Plone-default "Read More" pattern. The one stylized button is the search submit:

```css
.searchButton {
  background: #EB801C url(magnifier.png) center center !important;
  border: none;
  border-radius: 3px;
  color: #fff;
  margin-left: 5px;
  padding: 7px 3px;
}
.searchButton:hover {
  background: tomato;
  color: #fff;
}
```

Search input:
```css
#searchGadget { width: 15em; }
input.searchField {
  -moz-appearance: none;
  border: 1px solid #999;
  border-radius: 4px;
  padding: 8px 10px;
}
.searchSection { color: #fff; display: none; }
```

LP-wide buttons (`#content a.btn-grey`, `.btn.large-white`, `.btn.large-brown`, `.cta-button`) are defined in `ploneCustom.css` but **none are used inside the captured ecosystem-risks-benefits content pages** — they exist for cross-site consistency and can be ignored when replicating this sub-site.

---

## 7. Content blocks

The home page uses a 2-row × 3-column **section-card grid** rendered by Plone's standard document_view: each card has an `h2` title (linked) followed by a single descriptive paragraph. Cards have no special background — they sit on the white `#portal-columns` background separated by Plone's default whitespace.

The home page also features a **hero feature row** with two icon-led cards (`guide-icon.png` + `conservation-design.png`), each linking to an external Conservation Atlas / Databasin gallery.

```html
<div>
  <a href="..."><img src=".../guide-icon.png" /></a>
  <h3><a>Ecosystem Services Conservation Atlas</a></h3>
  <p>Explore landscapes through a collection of maps and data layers …</p>
</div>
```

These are styled by inline content (no dedicated CSS class on this sub-site).

### Inline image float

```css
.image-inline, a .image-inline, a:visited .image-inline {
  border: 1px solid #cccccc;
  float: right;
  margin-left: 1.5em;
  margin-top: 0.75em;
  padding: 0;
}
.captioned img { border: none !important; }
```

### Two-column helper

```css
.span6last { float: right; margin-right: 0; width: 47.75%; }
@media only screen and (max-width: 680px) {
  .span6last { float: none; margin-right: 0; width: 100%; }
}
```

There are **no** sub-site-specific cards, ribbons, callouts, or decorative blocks beyond what Plone renders by default.

---

## 8. Footer

The footer is the LP-wide blue band defined in `ploneCustom.css`. It is **not** customized for this sub-site (in fact the sub-site's `ecoss.css` hides one alternate variant: `.lp-footer { display: none; }`).

```css
#portal-footer {
  background: #2e76a0;
  color: #fff;
  width: 100%;
  padding: 1.5em;
  position: relative;
  bottom: 0;
  left: 0;
  margin: 0;
}
#portal-footer p { padding-left: 15px; color: #fff; font-size: 12px; }
#portal-footer-inner { max-width: 1000px !important; }    /* sub-site override */
```

Footer link list (Site Map / Accessibility / Contact / Conditions of Membership) is plain text-on-blue. Site credit (`fergusonlynch.com`) and "Powered by Plone & Python" appear inline.

```css
#portal-footer .sitecredit a { color: #7dd4d6 !important; }
#portal-footer .sitecredit       { color: #aae2fd; font-size: 12px; letter-spacing: 0.05em; ... }
#portal-footer .help > a:link    { color: #9adff1; }
#portal-footer .help > a:hover   { color: #FFA64D !important; }
```

A "Back to Top" anchor sits at the bottom-right of the footer and scrolls to `#top`. Sibling sub-site footers (`#fire-footer`, `#sefiremap-footer`, `#bobscapes-footer`, `#birdlocale-footer`, `#portal-footer-lit-gateway`) are explicitly hidden — only the default LP footer is shown.

---

## 9. Responsive breakpoints

`ecoss.css` declares only **one** sub-site-specific breakpoint:

| Breakpoint                             | Effect |
|----------------------------------------|--------|
| `@media only screen and (max-width: 680px)` | `.span6last` becomes full-width, no float (single-column layout for 2-col helper) |

Beyond that, the sub-site inherits the LP-wide breakpoint set from `ploneCustom.css` and the legacy Plone `mobile.css` (loaded with `media="handheld, screen and (max-device-width: 480px)"`):

| Breakpoint pattern                                     | Source              | Notes |
|--------------------------------------------------------|---------------------|-------|
| `@media handheld, screen and (max-device-width: 480px)` | mobile.css          | Full Plone mobile reset: hides logo, stacks columns, enlarges nav links / inputs |
| `@media (max-width: 420px)`                            | ploneCustom.css     | Tight phone breakpoint |
| `@media (max-width: 500px)`                            | ploneCustom.css     | Small phone |
| `@media (max-width: 600px)`                            | ploneCustom.css     | Phone |
| `@media (max-width: 667px)`                            | ploneCustom.css     | iPhone landscape |
| `@media (max-width: 680px)`                            | ecoss.css           | sub-site `.span6last` |
| `@media (max-width: 767px)`                            | ploneCustom.css     | Bootstrap-style "sm" |
| `@media (max-width: 768px)`                            | ploneCustom.css     | Tablet portrait |
| `@media (max-width: 770px)`                            | ploneCustom.css     | Tablet portrait |
| `@media (max-width: 979px)`                            | ploneCustom.css     | Bootstrap-style "md" |
| `@media (max-width: 1100px)`                           | ploneCustom.css     | Larger viewports |
| `@media (max-width: 1170px)`                           | ploneCustom.css     | Container threshold |
| `@media (min-device-width: 768px) and (max-device-width: 1024px)` | ploneCustom.css | iPad |

**Practical implication:** The site shows its native 1000-px desktop layout from ~1024 px upward; below ~979 px Plone/legacy CSS begins stacking columns and enlarging touch targets; below 480 px the full mobile reset kicks in.

---

## 10. Google Fonts

| Family          | Weights / styles requested                | Where used on this sub-site |
|-----------------|-------------------------------------------|------------------------------|
| Open Sans       | 400, 400i, 600                            | All body text and headings (sub-site override + `ploneCustom.css` body) |
| Source Sans Pro | 400, 700                                  | Loaded but **not used** on this sub-site (used elsewhere in portal) |
| Merriweather    | 400, 400i, 700                            | Loaded but not used here |
| Montserrat      | 400, 500, 600                             | Loaded but not used here |
| Material Icons  | (icon font)                               | Loaded but not visibly used here |
| Nunito Sans     | 400, 700, 400i                            | Loaded but not used here |
| Public Sans     | 300, 400, 700, 300i, 400i                 | Loaded but not used here |

When porting, only **Open Sans** is required to match this sub-site visually. The other families can be omitted from the theme's `<head>` if the theme is scoped to this sub-site only.

---

## 11. Print styles

A dedicated `print.css` is loaded via `<link media="print">` for every page. This is portal-wide LP/Plone Classic CSS — no sub-site-specific print rules exist in `ecoss.css` or in `@media print` blocks elsewhere.

### What `print.css` does

- Sets serif-free body and headings to `"Helvetica Neue", Arial, FreeSans, sans-serif`; bold weight on headings; tighter letter-spacing on h1/h2.
- All anchors print as black with a 0.1em-solid-grey border-bottom (no underline).
- `#portal-column-content` widened to 95%.
- `.documentDescription` set bold.
- `pre` becomes bordered with `1pt dotted black`, font-size 8pt.
- `table.listing` cells get `1pt solid black` borders, `border-collapse: collapse`, 6 px padding.
- `div.pageBreak` forces `page-break-before: always`.
- `#content dt` / `p` / `table` get tighter top/bottom margins.
- A long `display: none` list hides chrome:
  - `div.top`, `#portal-logo`, `#portal-siteactions`, `.hiddenStructure`, `#portal-searchbox`, `#portal-globalnav`, `#portal-personaltools`, `#portal-breadcrumbs`, `#edit-bar`, `#portal-column-one`, `#portal-column-two`, `#portal-languageselector`, `.contentViews`, `.contentActions`, `.help`, `.legend`, `.portalMessage`, `.documentActions`, `.netscape4`, `#viewlet-below-content .reply`, `#viewlet-below-content .discussion`, `#kss-spinner`, `#review-history`, `#content-history`, `.listingBar`, `#portal-footer`, `#portal-colophon`, `.skipnav`, `.link-presentation`, `input.standalone`, `.overlay`, `.managePortletsFallback`, `.close`, `.link-parent`, `.draggingHook`, …

### Sub-site `@media print` rules

**None.** A search across `ecoss.css`, `ploneCustom.css`, `base.css`, `mobile.css`, `reset.css`, and `resourcecontentleadimage.css` finds no `@media print` block beyond `print.css` itself. The shared LP base print stylesheet (`_print.scss`) in plonetheme.lp will fully cover this sub-site; no per-sub-site overrides are needed.

---

## File index

- `STYLE-GUIDE.md` — this file
- `html/01-home.html` … `html/24-contact.html` — captured raw HTML for every enumerated page
- `css/ecoss.css` — sub-site-specific CSS (most important file for replication)
- `css/ploneCustom.css` — LP-wide overrides (footer, headings, partial buttons, breakpoints)
- `css/base.css` — Plone's compiled base CSS (legacy Classic UI core)
- `css/reset.css` — Plone reset
- `css/mobile.css` — legacy Plone mobile reset (480 px breakpoint)
- `css/print.css` — LP-wide print stylesheet
- `css/resourcecontentleadimage.css`, `css/resourcetinymce-stylesheetstinymce.css` — Plone add-on CSS
- `css/font-awesome.min.css` — Font Awesome 4.2.0 from BootstrapCDN (loaded portal-wide; not visibly used on this sub-site)
- `images/ecoss-bg.jpg` — fixed full-bleed body background photograph
- `images/portal-header-bg.png` — 1×40 px tile that repeats horizontally across the header band
- `images/ecoss-logo.png` — sub-site logo
- `images/conservation-design.png`, `images/guide-icon.png` — home-page hero feature icons
- `images/black55.png` — semi-transparent black tile used as searchbox background
- `images/magnifier.png` — search button glyph
- `images/lp-logo-white.svg`, `images/lp-logo-footer-white.svg`, `images/fl-logo-white.svg` — LP-wide logos referenced from the parent portal chrome (provided for context)
- `screenshots/NN-slug.png` — full-height desktop captures (1280 px wide)
- `screenshots/NN-slug-mobile.png` — full-height mobile captures (375 px wide)
