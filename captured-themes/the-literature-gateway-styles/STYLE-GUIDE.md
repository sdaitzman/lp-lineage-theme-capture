# The Literature Gateway Sub-site Style Guide

Reference: `https://landscapepartnership.org/networks/working-lands-for-wildlife/the-literature-gateway` (production)

Source CSS: `literature.css` / `literature-gateway-3.css` (sub-site specific) + `ploneCustom.css` (shared portal styles).

---

## Page Inventory

All pages reachable from the sub-site nav, sub-site footer, and per-page sidebars. Captured at desktop 1280px and mobile 375px, full-page.

| # | Page | URL | HTML | Desktop | Mobile |
|---|------|-----|------|---------|--------|
| 01 | Home | `/networks/working-lands-for-wildlife/the-literature-gateway` | `html/01-home.html` | `screenshots/01-home.png` | `screenshots/01-home-mobile.png` |
| 02 | Background | `.../the-literature-gateway/about` | `html/02-background.html` | `screenshots/02-background.png` | `screenshots/02-background-mobile.png` |
| 03 | Gateway Tool (welcome) | `.../the-literature-gateway/gateway-tool` (redirects to `/welcome-to-the-literature-gateway-tool`) | `html/03-gateway-tool.html` | `screenshots/03-gateway-tool.png` | `screenshots/03-gateway-tool-mobile.png` |
| 04 | Resources (listing) | `.../the-literature-gateway/resources` | `html/04-resources.html` | `screenshots/04-resources.png` | `screenshots/04-resources-mobile.png` |
| 05 | Advanced Search | `.../the-literature-gateway/search_form` | `html/05-advanced-search.html` | `screenshots/05-advanced-search.png` | `screenshots/05-advanced-search-mobile.png` |
| 06 | Site Map | `.../the-literature-gateway/sitemap` | `html/06-sitemap.html` | `screenshots/06-sitemap.png` | `screenshots/06-sitemap-mobile.png` |
| 07 | Accessibility | `.../the-literature-gateway/accessibility-info` | `html/07-accessibility.html` | `screenshots/07-accessibility.png` | `screenshots/07-accessibility-mobile.png` |
| 08 | Contact | `.../the-literature-gateway/contact-info` | `html/08-contact.html` | `screenshots/08-contact.png` | `screenshots/08-contact-mobile.png` |
| 09 | Conditions of Membership | `https://landscapepartnership.org/help/general-user-support/how-to-participate/conditions-of-membership` (parent LP, after redirect) | `html/09-conditions-of-membership.html` | `screenshots/09-conditions-of-membership.png` | `screenshots/09-conditions-of-membership-mobile.png` |
| 10 | Resource detail (layout variant) | `.../the-literature-gateway/resources/technical-documentation-html` | `html/10-resource-detail.html` | `screenshots/10-resource-detail.png` | `screenshots/10-resource-detail-mobile.png` |

### Nav tabs (`#portal-globalnav`)

- **Home** – sub-site root
- **Background** – `/about`
- **Gateway Tool** – `/gateway-tool` (redirects to a child page; renders without standard chrome)
- **Resources** – `/resources` (listing of Plone Documents and Files)

### Footer links scoped to the sub-site

`Site Map`, `Accessibility`, `Contact`, `Conditions of Membership` (last lives outside the sub-site under the parent LP `/help/...` tree).

### Resource items (leaf pages)

`/resources` lists individual articles and PDFs, including: `technical-documentation-html` (captured as variant), `how-to-cite-html`, `video-how-to-use-the-literature-gateway-tool`, `what-evidence-exists-for-landbird-species-environment-relationships-...`, `do-review-papers-on-bird-vegetation-relationships-...`, plus folders `feedback/` and `anchor/`. All resource detail pages share the same template/layout, so one (`technical-documentation-html`) is captured as the layout variant per the plan §1.1.

---

## Capture notes

- **Source URL change.** Previous capture cited `dev.landscapepartnership.org`; capture is now from production (`landscapepartnership.org`) per the plan rule that production is the only canonical source.
- **`Conditions of Membership` link is broken inside the sub-site.** The footer link points to `.../the-literature-gateway/resources/help-1/how-to-participate/conditions-of-membership` which returns 404. The actual destination after following the parent-site path is `https://landscapepartnership.org/help/general-user-support/how-to-participate/conditions-of-membership` — that page is captured as `09-conditions-of-membership.html`. It is rendered with the parent LP chrome, not the Literature Gateway theme.
- **`Gateway Tool` redirects.** `/gateway-tool` redirects to `/welcome-to-the-literature-gateway-tool` which is the captured target. The page intentionally hides the standard chrome (header / nav / breadcrumbs / edit bar / `#portal-top`) and shows a `.gateway-nav-bar` instead — see Navigation section.
- **Login / Register pages not captured.** They use generic Plone forms with the sub-site chrome; not part of the design surface and not reachable through the sub-site nav (only via the WLFW return bar's parent links). Plone control-panel views are out of scope.
- **CSS files retained from the prior capture but not currently linked from these pages:** `dateinput.css`, `dropdown-menu.css`, `fullcalendar.css`, `jquery.css`, `ploneboard.css`, `truegallery.css`. Kept because the live site loads them on logged-in / portlet-heavy views.
- **Image `contact-banner.jpg` referenced in `literature.css` returns 404 on production** — likely orphaned rule. Not downloaded.
- **Reference screenshots are full-page (`fullPage: true`).** Spot-check heights: home desktop 1280×1635, home mobile 375×3356, gateway-tool 1280×1152, resources 1280×~6000+, resource detail 1280×9419 (long article).

---

## Color Palette

### CSS Custom Properties (`:root`)

| Variable | Hex | Usage |
|----------|-----|-------|
| `--darkblue` | `#266074` | Header bg, nav bg, footer bg, heading color |
| `--lightblue` | `#3484a3` | Secondary blue |
| `--green` | `#b1c260` | Accent green |
| `--topgreen` | `#88b66a` | Return-to-WLFW bar, edit bar |
| `--heading` | `#266074` | All heading colors (h1–h6) |
| `--yellow` | `#F9D909` | Yellow accent |

### Additional colors used in `literature.css` / `ploneCustom.css`

| Hex | Usage |
|-----|-------|
| `#266074` | Dark blue – nav background, globalnav, footer background |
| `#3890ae` | Nav hover background |
| `#bac966` | Nav selected/active background (yellow-green) |
| `#88b66a` | Top green bar ("Return to WLFW"), edit bar |
| `#e86129` | Orange – link hover, feature block headings, readmore hover, gateway-nav-bar hover |
| `#f7931e` / `#f7931f` | Orange – readmore button, styleguide swatch |
| `#F59E20` | `.btn-solid-orange` background |
| `#ef8f39` | `.btn-orange` background |
| `#e64c00` | Button hover (darker orange) |
| `#fd7916` | Blue block link hover |
| `#f1d215` | Blue block h4 (gold) |
| `#f9d90f` | Blue block link color (gold) |
| `#fced20` | WLFW nav bar link hover (bright yellow) |
| `#D0F7FF` / `#d0f7ff` | Blue block subhead, footer heading |
| `#b3dde7` | Sitecredit link |
| `#a9e1f3` | Personal tools visited link |
| `#276f88` | `.documentFirstHeading` color |
| `#222` | Nav selected text |
| `#666` | Body paragraph, portlet header |
| `#676767` | `.intro` color, dark grey swatch |
| `#777` | `.caption` text |
| `#9d9d9d` | `.material-icons-black` |
| `#444` | Gateway tool `.gateway-nav-bar` background |
| `#205c90` | Portlet header bg |
| `#a26623` | Brown swatch |
| `#efefef` | Feature block border, submenu hover, grey background |
| `#f5f5f5` | Light grey swatch |
| `#ddd` | Portlet border |
| `#ccc` | Borders |
| `#fff` | White – backgrounds, nav text, button text |
| `#ff9900` / `#f90` | Footer menu link hover |
| `rgba(20 83 120 / 80%)` | `.blue-block` overlay |
| `rgba(0, 0, 0, 0.6)` | `.slide-overlay` background |
| `rgba(0, 0, 0, 0.5)` | `.center-block-overlay`, portlet overlay |
| `rgba(255, 255, 255, 0.25)` | `.btn.large-white` background |

---

## Typography

### Font Families

| Font | Source | Usage |
|------|--------|-------|
| **Merriweather** | Google Fonts (`400,400i,700`) | Body text, document descriptions |
| **Montserrat** | Google Fonts (`400,500,600`) | Headings (h1–h6), nav links, buttons, subheads, footer menu, sitecredit |
| **Open Sans** | Google Fonts (`400,400i,600`) | `.button` font, readmore links |
| **Source Sans Pro** | Google Fonts (`400,700`) | Loaded but not explicitly used in `literature.css` |
| **Nunito Sans** | Google Fonts (`400,700,400i`) | Loaded but not explicitly used in `literature.css` |
| **Public Sans** | Google Fonts (`300,400,700,300i,400i`) | Loaded but not explicitly used in `literature.css` |
| **Material Icons** | Google Fonts | Icon font for feature blocks |
| **Font Awesome 4.2.0** | MaxCDN | Additional icons |

### Google Fonts load tags (from `index.html`)

```html
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600|Source+Sans+Pro:400,700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Merriweather:400,400i,700|Montserrat:400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap" rel="stylesheet">
```

### Font sizes & treatments

| Element | Size | Weight | Family | Other |
|---------|------|--------|--------|-------|
| Body | inherit | – | Merriweather, serif | `-webkit-font-smoothing: antialiased` |
| `#content h1` | 32px | 600 | Montserrat | color `--heading` |
| `h1.documentFirstHeading` | 34px | 600 | Montserrat | color `#276f88`, `text-transform: capitalize` |
| h2 | 26px | 600 | Montserrat | – |
| h3 | 24px | 600 | Montserrat | – |
| h4 | 20px | 600 | Montserrat | – |
| All h1–h6 | – | 600 | Montserrat, Verdana, sans-serif | line-height 1.3em, letter-spacing -0.0115em |
| p | 16px | – | (inherited Merriweather) | color `#666`, line-height 1.6em, letter-spacing 0.01em |
| `.intro` | 18px | – | – | line-height 1.7em, color `#676767` |
| `.heading-white` | 2.7em (mobile 2.4em) | 600 | Montserrat | uppercase, letter-spacing -0.025em |
| `.subhead` | 14px | – | – | uppercase, letter-spacing 2px, color `#7f7f87` |
| `.blue-block .subhead` | 14px | 600 | Montserrat | letter-spacing 4px, color `#D0F7FF`, uppercase |
| `.small-heading` | 14px | – | – | uppercase, letter-spacing 1px |
| `.caption` | 13px | – | – | color `#777` |
| Nav links | 16px | 500 | Montserrat | uppercase |
| Nav submenu links | 15px | – | – | text-transform none |
| WLFW nav bar | 13px | 600 | Montserrat | uppercase, letter-spacing 1px |
| `.gateway-nav-bar` links | 13px | 600 | Montserrat | uppercase, letter-spacing 1px |
| Footer menu items | 15px | 500 | Montserrat | – |
| Portlet header | 17px | – | Montserrat | color `#666` |
| Breadcrumbs | 85% | – | – | – |

---

## Layout & Structure

### Page width

| Element | Width | Notes |
|---------|-------|-------|
| `#visual-portal-wrapper` | max-width 100% | Full-width wrapper |
| `#portal-columns` | 1170px | Content area, centered (`margin: 0 auto`) |
| `#portal-columns` (mobile) | 96% | At `max-width: 768px` |
| `.narrow` | 1170px | Centered container |
| `.narrow` (mobile) | max-width 100%, padding 0 1rem | – |
| `.section-gateway-tool #portal-columns` | 100% | Full-width for tool page |

### Header / banner

| Element | Value | Notes |
|---------|-------|-------|
| `#portal-top` height | 215px | Background image: `literature-images/bird-banner.jpg` |
| `#portal-top` (mobile) | 130px | background-size 100% |
| `#portal-top` bg-size | 52% | `background-repeat: repeat-x` |
| `#portal-header` height | 130px | Transparent background, position relative |
| Logo width | 780px | `left: 10%`, `top: 75px`, z-index 2 |
| Logo (mobile) | width 95% | `left: 5px`, `top: 10px` |
| Min viewport height | `calc(100vh - 220px)` | On `#visual-portal-wrapper` |

### Banner images (per body-class section)

| Section | Image | Notes |
|---------|-------|-------|
| Home (`.section-the-literature-gateway-1`) | `literature-images/forest-1.jpg` | cover, left top |
| Background (`.section-about`) | `literature-images/about-banner.jpg` | center, hidden on `#portal-banner` |
| Contact (`.section-contact`) | `literature-images/contact-banner.jpg` | rule present in CSS but image returns 404 on production – orphaned |

### Content blocks

| Block | Min-height | Background |
|-------|------------|------------|
| `.gateway-block` | 400px | `literature-images/smoky-mtn-fall.jpg`, cover, center |
| `.mapviewer-block` | 200px | `literature-images/Indigo-bunting.jpg`, cover |
| `.block-400` | 400px | – |
| `.block-200` | 200px | – |

---

## Navigation

### Top return bar (`.wlfw-nav-bar`)

- Background `#88b66a` (top green)
- Padding `10px 30px`
- Font Montserrat 600 13px
- Links white, uppercase, letter-spacing 1px
- Link hover `#fced20` (bright yellow)

### Main navigation (`#globalnav-wrapper`)

- Background `#266074` (dark blue)
- `border-bottom: 2px solid #266074`
- `position: top: 175px`
- Links aligned right: `display: flex; justify-content: flex-end; margin-right: 4em`

### Nav links (`#portal-globalnav li a`)

- Background `#276074`
- Font Montserrat 500 16px
- `text-transform: uppercase`
- Padding `10px 30px`
- Color white

### Nav states

| State | Background | Text |
|-------|------------|------|
| Default | `#276074` | white |
| Hover | `#3890ae` | white |
| Selected | `#bac966` | `#222` |
| Selected + hover | `#3890ae` | white |

### Submenu links

- `text-transform: none`
- `font-size: 15px`
- Hover: bg `#efefef`, color `#E86128` (orange)

### Home tab specifics

- Home tab submenu hidden (`display: none`)
- Home tab text shown (no logo image)

### Mobile navigation (`max-width: 767px`)

- `#portal-globalnav` hidden by default, shown when `.opened`
- Nav items full width (`width: 100%`)
- Mobile toggle font Montserrat 600 13px
- `#globalnav-wrapper` `top: -40px`

### Gateway Tool page navigation

- `#portal-globalnav`, breadcrumbs, header, edit bar, `#portal-top` all hidden / zero-height
- `.gateway-nav-bar` rendered instead: bg `#444`, padding `10px 30px`
- Links: white, uppercase, Montserrat 600 13px, letter-spacing 1px
- Hover: `#e86129` (orange)

### Personal tools

- `right: 30px; top: -40px`
- Link color white
- Visited `#a9e1f3`

### Search box (`.LSBox`)

- `position: relative; top: 70px`
- Background white
- Padding 11px
- Border-radius 6px
- Box-shadow `0px 1px 5px 0 rgb(75 75 75 / 25%)`
- Mobile: `top: 113px`, position absolute, transparent bg, no shadow, `left: 57px`, width 150px

---

## Buttons

### `.button` (generic)

- Color `#54585b`, Open Sans 700 1.125rem
- Padding `.75rem 1rem`, border `1px solid #888`, border-radius 0.25rem
- Box-shadow `2px 3px 5px -1px rgba(0,0,0,0.35)`
- Transition: bg/color/border 0.2s linear
- Hover: bg `#e64c00`, color white, border transparent

### `.btn-solid-orange`

- bg `#F59E20`, color white, border transparent
- Hover bg `#e64c00`

### `.btn-orange`

- bg `#ef8f39`, color white, Montserrat 600 13px, uppercase, letter-spacing 1px

### `.btn.large-white` (inside `#content`)

- Border `1px solid #fff`, bg `rgba(255,255,255,0.25)`
- Color white, padding 15px, uppercase
- Montserrat 600 14px, letter-spacing 0.075em
- Border-radius 4px, transition all 0.3s ease-in-out
- Hover (in `.blue-block`): bg `rgb(8 48 70)`

### `a.readmore`

- 13px / 600 / Open Sans / uppercase
- Hover color `#f7931e`

---

## Content Blocks

### `.blue-block`

- bg `rgba(20 83 120 / 80%)` (dark blue semi-transparent)
- Padding `40px 30px`
- `.subhead`: Montserrat 600 14px, letter-spacing 4px, color `#D0F7FF`, uppercase
- `h4`: color `#f1d215` (gold), 22px
- `p`: color white, 16px, line-height 1.7em
- Links: color `#f9d90f` (gold), hover `#fd7916` (orange)

### `.feature-block`

- Border `6px solid #efefef`
- Padding 30px (mobile 15px, center text)
- Background white
- `h3`: margin-top 10px, 28px, color `#e86129`

### `.gateway-block`

- bg `literature-images/smoky-mtn-fall.jpg`, cover, center
- min-height 400px
- `position: relative; top: -35px`

### `.slide-overlay`

- `position: absolute; z-index: 5; top: 55%`
- bg `rgba(0,0,0,0.6)`
- Padding `30px 30px 40px`
- Width 70%, left 15%
- Color white, border-radius 6px, text-align center
- Mobile: top 35%, width 100%, left 0, border-radius 0, bg rgba 0.45

### `.gateway-tool-overlay`

- bg `literature-images/chestnut-sided-warbler.jpg`
- Padding `90px 15px 20px`
- Border-radius 10px
- background-position left center, cover

### `.center-block-overlay`

- bg `rgba(0,0,0,0.5)`
- Border `1px solid #fff`
- Padding 20px
- Border-radius 12px

### Material Icons

- `.material-icons`: 60px, color white
- `.material-icons-black`: 68px, color `#9d9d9d`

---

## Grid Layouts (from `ploneCustom.css`)

| Class | Columns | Gap |
|-------|---------|-----|
| `.grid-container-2col` | `50% 1fr` | 30px |
| `.grid-container-2col-no-gap` | `50% 1fr` | 0 |
| `.grid-container-3col` | `repeat(3, minmax(0, 1fr))` | 30px |
| `.grid-container-3col-gap10` | `repeat(3, 1fr)` | 10px |
| `.grid-container-three-quarter` | `68% 1fr` (literature.css) / `75% 1fr` (ploneCustom) | 30px |

All grid layouts collapse to single column at `max-width: 768px`.

### Utility classes

| Class | Value |
|-------|-------|
| `.shiftup` | `position: relative; top: -40px` |
| `.floatright` | `float: right` |
| `.space10` | `height: 10px; display: block` |
| `.space20` | `height: 20px; display: block` |
| `.space40` | `height: 40px; display: block` |
| `.bg-grey` | `background: #efefef` |
| `.gap10` | `gap: 10px; padding-right: 10px` |
| `.gap15` / `.gap20` / `.gap30` | `gap: 15px / 20px / 30px` |

---

## Footer

### Main footer (`#portal-footer-wrapper`)

- Background `#266074` (dark blue)

### Literature Gateway footer (`#portal-footer-lit-gateway`)

- `display: block` (overrides `display: none` in ploneCustom.css)
- Padding 2em
- Margin 2em auto
- Width 80% (mobile 100%, padding 1.5em, margin 1em auto)

### Footer layout (`.footer-container`)

- `display: flex; flex-direction: row; justify-content: space-between; align-items: flex-start`
- Mobile: `flex-direction: column-reverse; align-items: center`
- `.block-1`: margin-top 1.5em (logos)
- `.block-2`: width 15% (Browse menu)
- `.block-50`: width 53% (Contributors); mobile 90%

### Footer headings

- Color `#d0f7ff` (light cyan)
- margin-top 15px

### Footer menu (`.ft-menu`)

- `display: flex; flex-direction: column; justify-content: space-evenly`
- Items Montserrat 500 15px, padding `2px 0`
- Link color white, hover `#ff9900`

### Sitecredit

- Montserrat 12px uppercase, letter-spacing 0.05em
- Link `#b3dde7`, hover `#f90`
- Background icon `fergusonlynch-icon.png`

### Hidden footer elements

- `.lp-footer`, `.footer-left`, `.footer-rt`, `#jumpmenu`, other-subsite footers (bobscapes / birdlocale / fire / sefiremap / wlfw) — present in HTML but hidden via their respective CSS

---

## Portlets

### Navigation portlet

- Header bg `#205C90`, border-radius `4px 4px 0 0`, uppercase, padding 15px

### Generic portlet (`dl.portlet`)

- font-size 90%
- Border `1px solid #ddd`, border-radius 6px
- Margin-bottom 1.5em
- Header transparent bg, Montserrat 17px, color `#666`

---

## Responsive Breakpoints

| Breakpoint | Elements affected |
|------------|-------------------|
| `max-width: 768px` | `#portal-columns` (96%), `.narrow` (100%), `#portal-top` (130px), `#portal-logo img` (95%), `.LSBox` (absolute, 113px), `.footer-container` (column-reverse), `.block-50` (90%), `#portal-footer-lit-gateway` (100%), `.grid-container-2col` / `-3col` / `-three-quarter` (single col), `.heading-white` (2.4em), `.sitecredit` (margin adjust), `.bottom-nav` (single col grid), `.flex-container` (column), `.flex-container.space-between` (4-col grid) |
| `max-width: 767px` | `#portal-globalnav` (hidden, toggled by `.opened`), `.bird-overlay` (hidden), `.feature-block` (padding 15px, center text) |

---

## Key background images

| Image (in `images/`) | Used in |
|----------------------|---------|
| `bird-banner.jpg` | `#portal-top` header background |
| `forest-1.jpg` | Home `#portal-banner` |
| `smoky-mtn-fall.jpg` | `.gateway-block` hero |
| `Indigo-bunting.jpg` | `.mapviewer-block` |
| `about-banner.jpg` | Background page banner |
| `chestnut-sided-warbler.jpg` | `.gateway-tool-overlay` |
| `canada-warbler-masked.png` | Used in `ploneCustom.css` |
| `literature-logo-wlfw.svg` | Header logo (large) |
| `literature-logo.png` | Smaller header logo variant |
| `LG-logo-white.svg` | Footer logo |
| `csdv-abbrev.svg`, `CSDV-Logo-Small.svg` | Center for Science Discovery & Visualization mark |
| `FSshield.png` | USFS shield |
| `iup-logo.png` | Indiana University of PA logo |
| `AUNE-logo.png` | Antioch University New England logo |
| `fl-logo-white.svg` | Ferguson Lynch credit logo |
| (missing) `contact-banner.jpg` | Referenced in CSS but 404 on production – not downloaded |

---

## CSS file inventory

| File | Size | Purpose |
|------|------|---------|
| `literature.css` / `literature-gateway-3.css` | ~25KB | Sub-site-specific styles (primary). Files are byte-identical; the production HTML references the latter relative URL. |
| `ploneCustom.css` | ~131KB | Shared portal customizations (grids, blocks, shared classes) |
| `base.css` | ~70KB | Plone base styles |
| `reset.css` | ~480B | CSS reset |
| `dropdown-menu.css` | 2KB | Dropdown menu styles (older capture; not loaded by these pages) |
| `mobile.css` | 1KB | Mobile-specific (`@media handheld, screen and (max-device-width: 480px)`) |
| `print.css` | 2.5KB | Print styles (loaded with `media="print"`) |
| `jquery.css` | 9KB | jQuery UI styles (older capture) |
| `dateinput.css` | 2.4KB | Date input widget (older capture) |
| `fullcalendar.css` | 22KB | Calendar widget (older capture) |
| `truegallery.css` | 22KB | Gallery portlet (older capture) |
| `ploneboard.css` | 4KB | Discussion board (older capture) |
| `contentleadimage.css` | 304B | Lead image |
| `tinymce.css` | 854B | TinyMCE editor stylesheet |
| `font-awesome.min.css` | (CDN) | Font Awesome 4.2.0 icons |

---

## Print styles

`portal_css/print.css` is loaded via `media="print"` on every captured page. Inventory of rules in that file:

- Hides chrome: `#portal-personaltools-wrapper`, `#portal-globalnav-wrapper`, `#portal-anontools`, `#portal-searchbox`, `#portal-footer-signature`, `#portal-colophon`, `.skiplink`, `.hiddenStructure`, `#edit-bar`, `.portlet`, `.portletNavigationTree`, `.editbar`, the LiveSearch box.
- Forces black on transparent: `body { color: black; background: transparent; }` and removes link colors.
- Strips backgrounds: most navigation / header / footer wrappers reset to transparent and `box-shadow: none`.
- `@page` margin set (default 1in). No `@page :first` or sized page.
- Adds visible URL after external links (`a[href^="http"]:after { content: " (" attr(href) ") "; }`) for printed reference.
- Tables: `border-collapse` retained, header cells black on white.

No additional `@media print` blocks were found embedded in `literature.css`, `literature-gateway-3.css`, or `ploneCustom.css`. Sub-site-specific print overrides are therefore minimal — Phase 3.6 should rely on the shared `_print.scss` and only add overrides for sub-site-specific blocks (`.gateway-block`, `.gateway-nav-bar`, `.gateway-tool-overlay`, `.blue-block`, `.feature-block`, `.slide-overlay`) that should be hidden or simplified for print, plus the `.wlfw-nav-bar` chrome.

---

## Body classes (for CSS targeting)

- `template-document_view` – standard document view
- `portaltype-document` – Plone Document content type
- `site-the-literature-gateway` – identifies the sub-site (root pages)
- `section-the-literature-gateway-1` – home page section (note: `-1` suffix from Plone duplicate handling)
- `section-about` – Background page
- `section-gateway-tool` – Gateway Tool wrapper
- `section-welcome-to-the-literature-gateway-tool` – the redirected target page
- `section-resources` – Resources listing
- `content-the-literature-gateway-1` – content identifier on home
- `userrole-anonymous` – anonymous user
