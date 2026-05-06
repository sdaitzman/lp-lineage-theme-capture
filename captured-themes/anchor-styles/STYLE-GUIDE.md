# ANCHOR Sub-site Style Guide

Reference: `https://landscapepartnership.org/key-issues/anchor`

Captured: 2026-05-04 from production. Body class: `site-anchor`.

---

## 1. Page inventory

| # | Page | URL | Notes |
|---|------|-----|-------|
| 01 | Home (ANCHOR) | `/key-issues/anchor` | Main landing; title/byline hidden via `.template-document_view`; full 440px banner |
| 02 | ANCHOR Resources | `/key-issues/anchor/anchor-resources` | Folder listing of child resources (5 items) |
| 03 | ANCHOR MAP | `/key-issues/anchor/anchor-map` | Embedded map; short banner (230px) |
| 04 | ANCHOR Registration Form | `/key-issues/anchor/anchor-registration-form` | Form view; short banner (230px) |
| 05 | ANCHOR Fact Sheet | `/key-issues/anchor/anchor-resources/anchor-fact-sheet` | Document/PDF download page |
| 06 | ANCHOR Fact Sheet (Español) | `/key-issues/anchor/anchor-resources/anchor-fact-sheet-espanol` | Spanish version |
| 07 | ANCHOR Land Journal Publication | `/key-issues/anchor/anchor-resources/anchor-an-opportunity-to-change-landscape-connectivity-networks-and-conservation-delivery-at-scale-in-the-u-s` | External PDF link page |
| 08 | Integrating multiple data sources... | `/key-issues/anchor/anchor-resources/integrating-multiple-data-sources-species-distribution-models-estimate-distribution-abundance-nobo-us` | External link page |
| 09 | Appendix: Partner Resources | `/key-issues/anchor/anchor-resources/appendix-partner-resources` | Listing page; uses `.subsection-appendix-partner-resources-...` body class to hide H1 |
| 10 | Sitemap | `/key-issues/anchor/sitemap` | Sub-site footer link |
| 11 | Accessibility | `/key-issues/anchor/accessibility-info` | Sub-site footer link |
| 12 | Contact | `/key-issues/anchor/contact-info` | Sub-site footer link |
| 13 | Conditions of Membership | `/key-issues/anchor/resources/help-1/how-to-participate/conditions-of-membership` | Sub-site footer link, returns 404 within ANCHOR sub-tree (see Capture notes) |

### Top-level navigation (`#portal-globalnav`)
| Tab id | Label | Target |
|--------|-------|--------|
| `portaltab-anchor-homepage` | Home | `/key-issues/anchor` (resolveUid) |
| `portaltab-anchor-resources` | ANCHOR Resources | `/key-issues/anchor/anchor-resources` (with submenu of 4 items) |
| `portaltab-anchor-map` | ANCHOR MAP | `/key-issues/anchor/anchor-map` |
| `portaltab-anchor-registration-form` | ANCHOR Registration Form | `/key-issues/anchor/anchor-registration-form` |

### `nest-navigation-bar` (top utility bar)
- "Return to Landscape Partnership Site" link
- Dropdowns: Target Species, WLFW Landscapes, Companion Sites
- Linked sub-sites (cross-WLFW navigation, not enumerated here as ANCHOR pages).

### Footer link list (sub-site-specific)
- Site Map → `/key-issues/anchor/sitemap`
- Accessibility → `/key-issues/anchor/accessibility-info`
- Contact → `/key-issues/anchor/contact-info`
- Conditions of Membership → resolves outside ANCHOR sub-tree (404 within `/key-issues/anchor/`)

### Capture notes
- All 13 enumerated URLs were captured at desktop (1280px) and mobile (375px), full-page.
- **Page 13 (Conditions of Membership)** returned HTTP 404 from production — the link in the sub-site footer points to a path under `/key-issues/anchor/resources/help-1/...` that does not exist. The 404 page itself is captured to document footer rendering when this link is followed; a working alternative URL (typically `/help/conditions-of-membership` at the LP root) lives outside the sub-site and is not in scope for the ANCHOR replication.
- The ANCHOR site has no left-column sidebar portlet on most page templates (`#portal-column-one` is hidden via `display: none` on `.section-anchor`).
- The footer is shared with all WLFW sub-sites; only the four sub-site-specific links above are unique to ANCHOR.

---

## 2. Color palette

CSS custom properties / direct colors found in `anchor.css` and `ploneCustom.css`:

### Primary / brand
| Name | Hex | Usage |
|------|-----|-------|
| Navy Blue | `#27426A` | Main nav bg, footer bg, all H1–H6, `.anchor-text` (overrides base `#657F9E`) |
| Dark Blue | `#205C90` | Portlet headers, breadcrumb links |
| Slate Blue-Gray | `#657F9E` | Base LP nav bg (NOT used in ANCHOR — overridden) |
| Muted Olive | `#84984C` | Nav hover state |
| Light Gold | `#DFDF9E` | Nav selected tab bg |
| Yellow Hover | `#FFE061` | `.nest-navigation-bar a:hover` |

### Accent
| Name | Hex | Usage |
|------|-----|-------|
| Solid Orange | `#F59E20` | `.btn-solid-orange` background |
| Hover Orange | `#E64C00` | Default button hover bg |
| Brand Orange | `#F7931F` / `#F7931E` | `.orange` swatch, `.readmore` hover |
| Gold | `#F6D514` | `.gold` swatch |
| Tan | `#F0DEBB` | `.bg-tan`; `.sitecredit a:hover` |
| Footer Heading Gold | `#F4D69E` | `#portal-footer h3` |
| Brown | `#A26623` | `.brown` swatch |
| Blue Swatch | `#6D97BF` | `.blue` swatch |

### Neutrals
| Name | Hex | Usage |
|------|-----|-------|
| Body Text | `#666` | `p`, `dl.portlet dt` |
| Caption Gray | `#777` | `.caption` |
| Light Body Text | `#676767` | `.intro` |
| Dark Text | `#222` | Selected nav-link text; `.back-to-top a` bg |
| Light Bg | `#F5F5F5` | `.light-grey`, `.grey-bg` |
| Border Gray | `#DDD` | `dl.portlet` border |
| Border Light | `#DFDFDF` | `.image-border` |
| Edit Bar Teal | `#84B3B3` | Plone admin edit bar (admin only) |

---

## 3. Typography

Headings, body text, intro text, readmore links, portlet headings — primary font stack:

```css
body { font-family: 'Open Sans', sans-serif; line-height: 1.5em; }
p    { color: #666; line-height: 1.6em; padding-bottom: 15px; }
.intro { font-size: 17px; line-height: 1.7em; color: #676767; margin: 1em 0; }

h1.documentFirstHeading, h1 {
  color: #27426A;
  font-family: 'Montserrat', sans-serif;
  font-size: 2.6em;
  font-weight: 500;
  margin-top: 1.5em;        /* 0 on mobile */
  margin-bottom: 0.5em;
}
h2, h3, h4, h5, h6 {
  color: #27426A;
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  line-height: 1.5em;
  letter-spacing: -0.0115em;
  margin-bottom: 0;
}

dl.portlet dt {
  font-family: 'Montserrat', sans-serif;
  font-size: 17px;
  color: #666;
}

a.readmore {
  font-size: 13px;
  font-weight: 600;
  text-transform: uppercase;
  font-family: 'Source Sans Pro', sans-serif;
}
a.readmore:hover { color: #F7931E; }
```

Title/byline are hidden on document views: `.template-document_view .documentByLine, .template-document_view .documentFirstHeading { display: none !important; }` and on the appendix template via `.subsection-appendix-partner-resources-...`.

Captions:
```css
.caption          { padding: 0 0 10px; color: #777; font-size: 13px; }
dd.image-caption  { color: #666; font-size: 100%; max-width: 100%; padding: 20px; text-align: center; }
```

---

## 4. Layout & structure

### Page widths
- `#portal-header`: 1170px centered (100% on mobile)
- `#portal-columns`: 1170px centered, margin: 20px auto (100% below 1169px)
- `#visual-portal-wrapper`: max-width 100%; min-height calc(100vh - 190px)
- `.narrow` / `.inner-container`: 1170px max-width, centered

### Banner heights
- `.site-anchor #portal-banner`: 440px desktop, 230px mobile (≤768px)
- `.section-anchor-map #portal-banner`, `.section-anchor-registration-form #portal-banner`: 230px (always)

### Logo
```css
#portal-logo img {
  width: 577px; height: 182px;
  position: relative; top: 10px; left: 16%;
}
/* Mobile (≤768px): width 350px, left 10px */
```

### Grid system (`ploneCustom.css`)
| Class | Columns | Gap |
|-------|---------|-----|
| `.grid-container-2col` | `50% 1fr` | 30px |
| `.grid-container-3col` | `repeat(3, minmax(0,1fr))` | 30px |
| `.grid-container-4col` | `repeat(4, minmax(0,1fr))` | 0 |
| `.grid-container-5col` | `repeat(5, 1fr)` | 20px |
| `.grid-container-three-quarter` | `80% 1fr` (anchor) / `75% 1fr` (base) | 25–30px |
| `.grid-container-2col-no-gap` | `50% 1fr` | 0 |

All grid layouts collapse to single column at ≤768px.

### Flex / fullwidth helpers
```css
.flex-container       { display: flex; align-items: flex-start; }   /* stacks <768px */
.fullwidth-section    { width: 100vw; position: relative;
                        margin-left: -50vw; left: 50%;
                        padding: 2em 0; margin-bottom: 2em; }
```

### Spacing utilities
`.space` (25px), `.space10/15/20/30`, `.pad10/20/30`, `.gap10/15/20/30`, `.clear`.

---

## 5. Navigation

### `nest-navigation-bar` (top utility bar)
```css
.nest-navigation-bar {
  background: #27426A;       /* anchor.css overrides base #405D68 */
  display: block;            /* anchor.css overrides base display:none */
  padding: 10px 30px;
  font: 600 12px/1 'Montserrat', sans-serif;
  letter-spacing: 1px;
  text-transform: uppercase;
}
.nest-navigation-bar a       { color: #fff; }
.nest-navigation-bar a:hover { color: #FFE061; }
.nest-nav-inner              { margin: 0 auto; width: 100%; padding: 1px 30px; }
```

### Global nav (`#portal-globalnav`) — top tabs
```css
#globalnav-wrapper {
  background-color: #27426A;
  border-bottom: medium none;
  border-top: 1px solid white;
  top: 388px;               /* absolutely positioned over the banner */
}

#portal-globalnav {
  background-color: #27426A;
  display: flex;
  justify-content: center;
}
#portal-globalnav li a {
  background-color: #27426A;
  font: 600 16px 'Montserrat', sans-serif;
  padding: 14px;
  color: #fff;
}

/* Selected */
#portal-globalnav .selected a              { background: #DFDF9E; color: #222; }
/* Hover (incl. selected) */
#portal-globalnav a:hover,
#portal-globalnav .selected a:hover        { background: #84984C; color: #fff; }
```

Mobile (≤768px): `#globalnav-wrapper { top: 45px }`, `.menu-toggle` (black hamburger button) is shown, `#portal-globalnav` is hidden until `.opened` is added; nav items stack 100% width.

### Submenus (dropdowns)
```css
#portal-globalnav ul {
  position: absolute; width: 230px; left: -999em;     /* hidden off-screen */
  background: #fff; box-shadow: 0 0 5px #666;
}
#portal-globalnav ul.submenu a       { font-weight: 400; background: #efefef; color: #333; }
#portal-globalnav ul.submenu a:hover { background: #7d9cc0; color: #fff; }

/* The "Home" tab has no submenu by design */
#portaltab-home-link ul.submenu { display: none; }
```

### Search box
```css
#portal-searchbox { top: -30px; right: 30px; border-radius: 6px; }
.LSBox            { top: 85px; position: relative; right: 2rem;
                    background: rgba(255,255,255,0.35);
                    padding: 11px 15px; border: 1px solid #fff; border-radius: 6px; }
```

### Breadcrumbs
Hidden on most ANCHOR pages: `#portal-breadcrumbs { display: none; }` (selectively re-enabled in some templates).

---

## 6. Buttons

```css
/* Default button */
.button {
  color: #54585B;
  font-size: 1.125rem;
  font-weight: 700;
  font-family: "Open Sans", Arial, sans-serif;
  padding: .75rem 1rem;
  border: 1px solid #888;
  border-radius: 0.25rem;
  box-shadow: 2px 3px 5px -1px rgba(0,0,0,0.35);
}
.button:hover { background: #E64C00; color: #fff; border-color: transparent; }

/* Solid orange */
.btn-solid-orange { color: #fff; background: #F59E20; border-color: transparent; }
.btn-solid-orange:hover { background: #E64C00; color: #fff; }
```

Other button color helpers in `ploneCustom.css`: `.btn-blue`, `.btn-red`, `.btn-orange`, `.cta-button` — see `images/screenshots/01-home.png` for usage.

---

## 7. Content blocks

```css
.bg-tan          { background: #F0DEBB; padding: 2rem; }
.bg-white-rounded{ background: #fff; border-radius: 15px; }
.grey-bg         { background: #f5f5f5; }
.fullwidth-section { /* see §4 */ }

.partner-block   { display: flex; align-items: center; justify-content: space-around;
                   gap: 20px; margin: 2em auto; }
/* Mobile: 3-column grid */

.card-white      { padding: 15px; border-radius: 3px; background-color: #fff; }

/* Image utilities */
.rounded         { border-radius: 8px; }
img.rounded      { border-radius: 5px; }
.rounded15       { border-radius: 15px; }
.shadow-btm      { box-shadow: 3px 8px 10px -4px rgb(0 0 0 / 40%); }
.image-border    { border: 1px solid #DFDFDF; }
.image-right     { margin: 0 0 0 2em; }

/* Tile listings */
.tileHeadline    { font-size: 1.5em; font-weight: 600; }
.tileImage img   { width: 280px; height: auto; }
```

### Portlets (sidebar)
```css
dl.portlet { font-size: 90%; border: 1px solid #DDD; border-radius: 6px;
             margin-bottom: 1.5em; }
.portletNavigationTree .portletHeader {
  background: #205C90; border-radius: 4px 4px 0 0;
  text-transform: uppercase; padding: 15px;
}
```

### Back-to-top
```css
.back-to-top a {
  position: fixed; bottom: 0.75em; right: 0.75em;
  width: 110px; height: 35px; line-height: 35px;
  background: #222; color: #ccc;
  border-radius: 5px; font-size: 13px; text-transform: uppercase;
  z-index: 100;
}
.back-to-top:hover a { background: #000; color: #87A301; }
```

---

## 8. Footer

```css
#portal-footer {
  background: #27426A;            /* anchor override of base #2E76A0 */
  color: #fff;
  padding: 1.5em;
}
#portal-footer h3                  { color: #F4D69E; }
#portal-footer p                   { color: #fff; font-size: 12px; }
#portal-footer .sitecredit a       { color: #fff; }
#portal-footer .sitecredit a:hover { color: #F0DEBB; }

#portal-footer ul.ft-menu          { list-style: none; margin: 0; padding: 0; }
#portal-footer .ft-menu li a       { color: #fff; font-size: 14px; }
#portal-footer .ft-menu li a:hover { color: #F0DEBB; }
```

### Layout
`grid-container-5col` (5 columns, 20px gap, stacks at ≤767px):
1. WLFW logo + USDA NRCS lockup
2. EBTJV logo + SARP logo
3. "Learn" links (About, Members, Community, Issues, Help)
4. "Browse" links (Projects, Maps, News, Resources, Training)
5. Contact + LP logo + sub-site selector dropdown

ANCHOR-specific footer links (within col 1 sub-list): Site Map, Accessibility, Contact, Conditions of Membership.

---

## 9. Responsive breakpoints

| Breakpoint | Behavior |
|------------|----------|
| 1170px | `#portal-header`, `.narrow`, `.inner-container` go 100% width |
| 1169px | `#portal-columns` goes 100% width |
| 979px  | Top header link font size reduces |
| **768px** | Primary mobile breakpoint: nav collapses, all `.grid-container-Xcol` stack, banner shrinks 440→230px, logo shrinks 577→350px, `.menu-toggle` appears, `.flex-container` stacks |
| 767px  | `h1 { margin-top: 0 }`, `.grid-container-5col` stacks |
| 480px  | Handheld media |

---

## 10. Google Fonts

Loaded via `<link>` in `<head>`:

```
Open Sans         400, 400i, 600
Source Sans Pro   400, 700
Merriweather      400, 400i, 700
Montserrat        400, 500, 600
Nunito Sans       400, 700, 400i
Public Sans       300, 400, 700, 300i, 400i
Material Icons    (icon font)
```

Plus Font Awesome 4.2.0 via MaxCDN.

Saved fetched stylesheet responses: `css/google-fonts-1.css`, `google-fonts-2.css`, `google-fonts-material-icons.css`.

---

## 11. Print styles

Sole site-wide print stylesheet: `css/print.css` (Plone Barceloneta-derived, **not** ANCHOR-specific). Neither `anchor.css` nor `ploneCustom.css` define their own `@media print` blocks — the LP base print sheet is the only print rule set.

Highlights of `print.css`:
- Body/headings switch to `"Helvetica Neue", Arial, FreeSans, sans-serif`; headings bold + `page-break-inside: avoid`.
- Anchors → black, no underline, with `border-bottom: 0.1em solid gray` instead.
- `#portal-column-content { width: 95% }` so content fills page; `#portal-column-one`, `#portal-column-two` hidden.
- Hides chrome: `div.top, #portal-logo, #portal-siteactions, .hiddenStructure, #portal-searchbox, #portal-globalnav, #portal-personaltools, #portal-breadcrumbs, #edit-bar, #portal-languageselector, .contentViews, .contentActions, .help, .legend, .portalMessage, .documentActions, #portal-footer, #portal-colophon, .skipnav, .listingBar, .addthis_toolbox, #partnerSiteSelection, #viewlet-below-content .reply, .visualNoPrint, .overlay, .managePortletsFallback, .draggingHook, input.standalone, input.context`.
- Floats/clears images via `.image-left`, `.image-right`, `.image-inline`.
- `pre { border: 1pt dotted black; font-size: 8pt; padding: 1em }`.
- `table.listing` + cells get `1pt solid black` borders, collapsed.
- `div.pageBreak { page-break-before: always; }`.
- No `@page` margin rules. No URL-after-link printing. No background-color overrides beyond defaults.

For Phase 3 print-styles work, `_print.scss` (the LP base) covers most of these; ANCHOR-specific overrides should only be needed if the new theme adds `nest-navigation-bar`, hero banner, or fullwidth blocks that should be hidden in print but aren't yet covered by base.

---

## CSS file hierarchy (load order on the live site)

1. `reset.css`
2. `jquery.css` (jQuery UI)
3. `base.css` (Plone Barceloneta base)
4. `dropdown-menu.css` (globalnav dropdown mechanics)
5. `tinymce.stylesheetstinymce.css`
6. `print.css`
7. `mobile.css`
8. `plone.app.jquerytools.dateinput.css`
9. `fullcalendar.css`
10. `plonetruegallery-portlet.css`
11. `contentleadimage.css`
12. `ploneboard.css`
13. **`ploneCustom.css`** (≈131 KB) — site-wide LP custom styles, all sub-site classes here
14. `font-awesome.min.css`
15. Google Fonts (3 separate `<link>` requests)
16. **`anchor.css`** (≈12 KB) — ANCHOR sub-site overrides, loaded last

`anchor.css` is the key sub-site file: it changes nav and footer to navy `#27426A`, shows the `nest-navigation-bar`, swaps banner imagery, and tweaks selected-nav coloring. Everything ANCHOR-specific lives in this file or under `.site-anchor` / `.section-anchor*` selectors in `ploneCustom.css`.

---

## Key differences from base LP site

- Nav background: `#27426A` (navy) vs base `#657F9E` (slate)
- Footer background: `#27426A` vs base `#2E76A0`
- Heading + nav font: explicit Montserrat (base uses Source Sans Pro for nav at 18px)
- Selected nav: light gold `#DFDF9E` + `#222` text (base uses olive `#95A664`)
- Nav hover: muted olive `#84984C` (base uses `#4C6C8C` blue)
- Banner: custom grasslands image (`hero-banner-grasslands.jpg`), 440px / 230px
- `nest-navigation-bar`: visible (`display: block`), navy bg (base hides it)
- Title + byline hidden on document views; H1 hidden on `appendix-partner-resources`
- Breadcrumbs hidden site-wide
- `#portal-top` height 0, no background image
- Left sidebar (`#portal-column-one`) hidden across the sub-site
