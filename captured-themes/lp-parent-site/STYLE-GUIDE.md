# LP Parent Site Style Guide

Reference: `https://landscapepartnership.org/`

Captured: 2026-05-05 from production. Body class on home: `template-landscape_home portaltype-plone-site site-portal userrole-anonymous content-portal`.

---

## 1. Page inventory

| # | Page | URL | Notes |
|---|------|-----|-------|
| 01 | Home | `/` | Full-width hero slideshow (`template-landscape_home`); banner, breadcrumbs, and edit bar hidden |
| 02 | About | `/about` | About-banner image; standard content layout |
| 03 | About — Catalog Guide | `/about/a-guide-to-collaboration-and-communication-tools` | Long document view |
| 04 | About — Services | `/about/services` | Folder listing |
| 05 | About — LP Workspaces | `/about/services/landscape-partnership-workspaces` | Video page |
| 06 | About — WLFW Workspaces | `/about/services/working-lands-for-wildlife-wlfw-workspaces` | Long document |
| 07 | About — FAQs | `/about/faqs` | FAQ accordion |
| 08 | About — Welcome Video | `/about/welcome-to-lp` | Video embed |
| 09 | LP Members / Networks | `/networks` | Folder listing with sub-site tiles |
| 10 | Members — Workspaces | `/networks/workspace/` | Private/public workspace listing |
| 11 | Members — Organizations | `/networks/organizations/` | Grid search |
| 12 | Our Community | `/people` | People directory |
| 13 | Community — Expertise Search | `/people/Members` | Search form |
| 14 | Community — Voices | `/people/voices-from-app-community` | Article listing |
| 15 | Community — Map | `/people/Members/map-search` | Map view |
| 16 | Community — How To Use | `/people/how-to-use-the-lp-search-directory` | Video page |
| 17 | Issues | `/key-issues` | Topic listing with banner |
| 18 | Resources | `/resources` | Folder listing |
| 19 | Resources — LP Products | `/resources/lp-products` | Grid listing |
| 20 | Projects | `/projects` | Project grid with search |
| 21 | Projects — Search | `/projects` (search) | Filtered view |
| 22 | Projects — Submit | `/projects/submit` | Form |
| 23 | Maps & Data | `/maps-data` | Tool listing |
| 24–28 | Maps subpages | Spatial, Aquatic, Appalachian, Regional, ZIP | Various tool views |
| 29 | News | `/news` | News listing |
| 30 | News — Events | `/news` (events) | Calendar + list |
| 31 | News — Newsletters | `/news/newsletters` | Folder |
| 32 | Training | `/training-online-learning` | Course index |
| 33–35 | Training subpages | Videos, Exchange, Collection | Various |
| 36 | Contact | `/contact-info` | Contact form |
| 37 | Help | `/help` | FAQ / how-to |
| 38 | Sitemap | `/sitemap` | Auto-generated |
| 39 | Accessibility | `/accessibility-info` | Policy page |
| 41 | Login | `/login_form` | Auth form |
| 42 | Register | `/register` | Auth form |

### Top-level navigation (`#portal-globalnav`)
| Tab id | Label | Target |
|--------|-------|--------|
| `portaltab-home` | Home (icon) | `/` |
| `portaltab-about` | About | `/about` (submenu: Catalog, Services, FAQs, Welcome Video, Video Collection) |
| `portaltab-networks` | LP Members | `/networks` (submenu: Workspaces, Organizations Search, Eastern Brook Trout, SARP, Working Lands for Wildlife) |
| `portaltab-people` | Our Community | `/people` (submenu: Expertise Search, Voices, Community Map, How To Use) |
| `portaltab-wlfw-link` | WLFW | `/networks/working-lands-for-wildlife` (submenu mirrors main nav) |
| `portaltab-key-issues` | Issues | `/key-issues` (submenu: ANCHOR, Wildland Fire, Climate Context, etc.) |
| `portaltab-resources` | Resources | `/resources` |
| `portaltab-projects` | Projects | `/projects` |
| `portaltab-maps-data` | Apps, Maps & Data | `/maps-data` |
| `portaltab-news` | News & Events | `/news` |
| `portaltab-training-online-learning` | Training | `/training-online-learning` |

### Sub-site utility bars (hidden on parent site, shown on sub-sites)
- `.nest-navigation-bar` — shown on ANCHOR and similar sub-sites; hidden (`display:none`) on parent
- `.wildlandfire-nav-bar`, `.bobscapes-nav-bar`, `.wlfw-nav-bar`, `.gateway-nav-bar`, `.sefire-nav-bar` — sub-site-specific return links; all hidden (`display:none`) on parent
- `.tgt-species` — WLFW target-species dropdown; hidden on parent
- `.landscape-biome-menu` — WLFW landscape biome dropdown; hidden on parent

---

## 2. Color palette

CSS properties / direct values found in `ploneCustom.css`:

### Primary brand
| Name | Hex | Usage |
|------|-----|-------|
| Slate Blue-Gray | `#657F9E` | Main nav background (`#globalnav-wrapper`, `#portal-globalnav`), `.bg-blue` swatch |
| Dark Navy | `#28526E` | `#cta-block` background |
| Medium Blue | `#2E76A0` | `#portal-footer` background (base LP footer) |
| Medium-Dark Blue | `#205C90` | `#portal-breadcrumbs a`, `.boxed-text` text color |
| Teal-Dark | `#28526b` | Expert-search section background |
| Blue-Gray Alt | `#1F657F` / `#247695` | Group/project buttons |

### Heading / content brown
| Name | Hex | Usage |
|------|-----|-------|
| Warm Brown | `#8E6747` | All `h1`–`h6` color; `.sw-brown` swatch; `.featured-heading` |
| Gold Brown | `#C1B259` | `.bg-gold` background; `.gold-block`; `.sw-gold` swatch |

### Accent / action
| Name | Hex | Usage |
|------|-----|-------|
| CTA Gold/Yellow | `#f7bd4f` | `.cta-button` background |
| CTA Hover Orange | `#f38b1a` | `.cta-button:hover` |
| Orange | `#f8903e` | `.btn-orange`, `.btn-orange-large` |
| Orange Hover | `#F7700D` | `.btn-orange:hover` |
| Orange (block) | `#ef9b26` | `.orange-block` background |
| Orange (bg) | `#dd733e` | `.bg-orange`, `.sw-red-orange` swatch |
| Red | `#FF6633` | `.btn-red` |
| Heading Gold | `#f7d25b` | Overlay `h2` color; `#cyclist h2` |
| Amber | `#f7c60e` | `.overlay-btn-3 a:hover` text |

### Neutrals
| Name | Hex | Usage |
|------|-----|-------|
| Body Text | `#444` | `p`, `#content li` |
| Light Body Text | `#676767` | `.intro` |
| Dark Gray | `#333` | `#portal-globalnav ul.submenu a` |
| Medium Gray | `#666` | `.featurebox > p` |
| Caption/Meta | `#7e7e7e` | `.detail-txt` |
| Light BG | `#f5f5f5` | `.grey-bg` |
| Off-White BG | `#f6f3ed` | `#portal-banner` default bg; `.bg-gold-lite` border |
| Light Beige | `#e5e5dc` | `#slick-slider` background; `#cyclist.featured` bg |
| Tan | `#e7e5da` | `.tan-block` |
| Border Gray | `#DDD` | `table.simple`, `dl.portlet` |
| Edit Bar Green | `#75ad0a` | Admin-only Plone edit bar |

### Named swatches (from `.swatch`/`.colorguide` style guide page)
| Class | Hex | Label |
|-------|-----|-------|
| `.sw-blue-grey` | `#657e9e` | Blue-gray (nav) |
| `.sw-green` | `#94a362` | Green |
| `.sw-gold` | `#c1b259` | Gold |
| `.sw-red-orange` | `#dd733e` | Red-orange |
| `.sw-brown` | `#8E6747` | Brown (headings) |

---

## 3. Typography

### Font stacks
```
Body:     'Open Sans', sans-serif
Headings: 'Montserrat', sans-serif
Nav:      'Source Sans Pro', sans-serif  (base nav font, 18px)
Search:   'Montserrat', sans-serif
Portlets: 'Montserrat', sans-serif (portlet header)
Serif:    'Merriweather', serif  (`.popquote`)
Utility:  'Nunito Sans', 'Public Sans'  (loaded, used in sub-sites)
Icons:    Material Icons (CDN), Font Awesome 4.2.0 (MaxCDN)
```

### Heading sizes
```css
h1, #content h1.documentFirstHeading {
  color: #8E6747;
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  font-size: 36px;       /* 30px at ≤600px */
  line-height: 1.5em;
  letter-spacing: -0.0125em;
  margin: 1.5em 0 0.5em; /* margin-top: 0 at ≤600px */
}
h2 { font-size: 30px; }
h3 { font-size: 24px; margin-bottom: .5em; margin-top: 1em; }
/* h4/h5/h6 inherit Montserrat 500, #8E6747, scale down from h3 */
```

### Body text
```css
body { font-family: 'Open Sans', sans-serif; line-height: 1.5em; background: #fff; }
p    { color: #444; font-size: 16px; line-height: 1.6em; }
.intro { font-size: 20px; line-height: 1.5em; color: #676767; margin: 1em 0; }
.introtext { font-size: 16px; line-height: 1.5em; color: #444; font-weight: 600; }
#content li { color: #444; font-size: 1.2em; letter-spacing: 0.01em; line-height: 1.5em; margin-bottom: 10px; }
```

### Links
```css
a:visited { color: #205C90 !important; }
/* Breadcrumbs */
#portal-breadcrumbs a { color: #205C90; }
/* Readmore / more-link */
.more-link { font-size: 13px; font-weight: 600; text-transform: uppercase; }
/* Description / document description */
#content .documentDescription, #content #description {
  font-size: 1.35em; line-height: 1.5em;
  font-family: 'Montserrat', sans-serif; font-weight: 500;
}
```

### Special text classes
```css
.heading-gold  { color: #f7d25b !important; font-size: 2.6em; letter-spacing: -0.025em; line-height: 2.3rem; }
.heading-white { color: #fff !important; font-weight: 600; font-family: 'Montserrat'; font-size: 2.7em; text-transform: uppercase; }
.heading-large { font-size: 2.3em; margin: 1em 0 0.5em; }           /* 1.8em at ≤767px */
.slogan        { font-size: 22px; font-style: italic; line-height: 1.5em; }
.popquote      { color: #205c90; font-family: 'Merriweather'; font-size: 1.5em; font-style: italic; line-height: 1.4em; }
.detail-txt    { font-family: 'montserrat'; font-size: 13px; text-transform: uppercase; letter-spacing: 0.05em; color: #7e7e7e; }
.text18 { font-size: 18px; }
.text20 { font-size: 20px; }
```

---

## 4. Layout & structure

### Page widths
- `#visual-portal-wrapper`: `max-width: 1170px`, centered; `min-height: calc(100vh - 190px)`; `background: #fff`
- `#portal-header`: `width: 1170px`, `margin: 0 auto`, `height: 215px` (185px on mobile)
- `#portal-columns`: centered within wrapper
- `.narrow`, `.inner-container`: `width: 1170px`, `margin: 0 auto`; `max-width: 100%` below 1170px
- `#portal-footer-wrapper div#portal-footer-inner`: `max-width: 1170px`, `margin: 0 auto`

### Banner / portal-top
```css
#portal-top {
  background-image: url(blue-top-bar.png); /* decorative blue stripe at top */
  background-repeat: repeat-x;
  position: relative;
}
#portal-banner {
  display: block;
  height: 350px;         /* 130px on ≤768px */
  background-position: center;
  background-size: cover;
  background-color: #f6f3ed;
  width: 100vw;
  position: relative;
  margin-left: -50vw; left: 50%; /* full-bleed trick */
}
```

Section-specific banner images (background only, no `<img>` tag):
- `.section-about`: `about-banner` image
- `.section-people`: `sheep-D4396-1.jpg`
- `.section-key-issues`: `timber-harvest.jpg`
- `.section-resources`: `sydney-herron-unsplash.jpg`
- `.section-news`: `toad.jpg`
- `.section-maps-data`: `partners-banner.jpg`
- `.section-projects`: French broad river photo
- `.section-training-online-learning`: `downloading-data.jpg`
- `.section-help`: `gary-bendig-unsplash.jpg`

Template overrides (hide banner):
- `template-landscape_home`, `template-landscape_home_test`, `template-wlfw_home`, `site-working-lands-for-wildlife`, `site-login`, `template-folder_contents`, `template-search`, `template-login_form`, etc.: `display: none`
- `.template-people-search`: `height: 0`
- `.section-issues`: `height: 100px; background: #f6f3ed`

### Logo
```css
#portal-logo { display: inline-block; margin: 70px 20px 20px; }
/* Logo img: src="logo.png", height="115" width="382" */
@media (max-width: 768px) {
  #portal-logo { position: absolute; top: 30px; left: 10px; margin: 0; }
  #portal-logo img { width: 295px; height: auto; }
}
```

### Grid system
| Class | Columns | Gap | Notes |
|-------|---------|-----|-------|
| `.grid-container-2col` | `50% 1fr` | 30px | Collapses at ≤768px |
| `.grid-container-2col-no-gap` | `50% 1fr` | 0 | Collapses at ≤768px |
| `.grid-container-3col` | `repeat(3, minmax(0,1fr))` | 30px | Stacks at ≤768px |
| `.grid-container-3col-gap10` | `repeat(3, 1fr)` | 10px | Stacks at ≤768px |
| `.grid-container-4col` | `repeat(4, minmax(0,1fr))` | 0 | Stacks at ≤768px |
| `.grid-container-4col-w-gap` | `repeat(4, 1fr)` | 30px | Stacks at ≤768px |
| `.grid-container-4colstack` | `25% 25% 25% 25%` | 0 | Stacks at ≤768px |
| `.grid-container-5col` | `repeat(5, 1fr)` | 20px | Stacks at ≤767px |
| `.grid-container-6col` | `repeat(6, 1fr)` | 20px | 2-col at ≤767px |
| `.grid-container-three-quarter` | `75% 1fr` | 30px | Stacks at ≤768px |
| `.grid-container-65-35` | `65% 1fr` | 30px | Block at ≤768px |
| `.grid-container-50-25-25` | `50% auto auto` | 30px | Stacks at ≤768px |
| `.grid-container-25-50-25` | `auto 50% auto` | 30px | Stacks at ≤768px |
| `.grid-container-30-70` | `30% auto` | 0 | Stacks at ≤768px |
| `.grid-container-70-30` | `70% auto` | 0 | Stacks at ≤768px |
| `.grid-container-40-60` | `40% auto` | 0 | Stacks at ≤768px |
| `.grid-container-20-80` | `20% auto` | 0 | Stacks at ≤768px |

Legacy float-based columns:
| Class | Width | Notes |
|-------|-------|-------|
| `.span3` / `.span3last` | ~23–24% float left | Stacks at ≤768px |
| `.span4` / `.span4last` | ~31.6% float left | Stacks at ≤768px |
| `.span6` / `.span6.last` | ~47.75% float left | Stacks at ≤768px |
| `.five-column` | ~18% float left | |
| `.row-fluid .span9` | 74.47% float right | |

### Spacing utilities
`.space` (25px h), `.space10/15/20/30`, `.pad10/20/30/40`, `.gap10/15/20/30`, `.gap` (30px), `.clear` (clear: both; 1px).

### Full-bleed helpers
```css
.fullwidth-section {
  width: 100vw; position: relative;
  margin-left: -50vw; left: 50%;
  padding: 2em 0;
}
```

---

## 5. Navigation

### Global nav (`#portal-globalnav`) — main horizontal tabs
```css
#globalnav-wrapper {
  background-color: #657F9E;
  border-bottom: medium none;
  border-top: 1px solid white;
  margin-bottom: 0px;
  position: absolute;
  top: 0; width: 100%;
}
#portal-globalnav {
  font-weight: 400;
  background-color: #657F9E;
  display: flex;
  justify-content: center;
  margin: 0;
}
#portal-globalnav li a {
  background-color: #657F9E;
  min-width: 2.5em;
  padding: 14px;
  font-size: 18px;
  font-family: 'Source Sans Pro', sans-serif;
  color: #fff;
}
/* Home tab: icon only */
#portaltab-home > a {
  background: url("../menu-home-white.png") no-repeat center 15px !important;
  text-indent: -999em;
}
/* Hover */
#portal-globalnav a:hover, #portal-globalnav .selected a:hover {
  background: #4C6C8C; color: #fff;
}
/* Selected/active */
#portal-globalnav .selected a { background: #95A664; color: white; }
```

### Submenus (dropdowns)
```css
#portal-globalnav ul {
  position: absolute; width: 230px;
  left: -999em;              /* off-screen when hidden */
  background: #fff;
  box-shadow: 0px 0px 5px #666;
}
#portal-globalnav ul.submenu a       { background: #efefef; color: #333; }
#portal-globalnav ul.submenu a:hover { background-color: #7d9cc0 !important; color: #fff !important; }
#portal-globalnav ul.submenu a:visited { background-color: #efefef !important; color: #666 !important; }
/* Nested sub-submenu offset */
#portal-globalnav li ul ul { margin: -4px 0 0 228px; box-shadow: 0px 0px 5px #666; }
```

### Search box
```css
#portal-searchbox {
  border: none; background: none;
  position: relative; top: 74px; right: 0; z-index: 2;
}
#searchGadget { width: 13em; font-size: 13px; font-family: 'Montserrat', sans-serif; }
```

### Personal tools (login/register)
- `.loginbutton a` / `.logoutbutton a` / `.registerbutton a`: SVG image-based buttons, 88×24px, positioned at top-right
- `#portal-personaltools-wrapper`: `position: absolute; right: 220px; top: 90px`

### Partner site selector
```css
#partnerSiteSelection {
  position: absolute; right: 0; top: 90px;
  width: 256px; border-radius: 6px; border: 1px solid #ccc;
}
```

### `nest-navigation-bar` (sub-site return bar)
The `nest-navigation-bar` is **hidden on the parent site** (`display: none`) and activated by sub-site CSS:
```css
.nest-navigation-bar {
  background: #405D68;   /* overridden by each sub-site */
  display: none;
  padding: 10px 25px 0;
}
.nest-nav-inner { width: 1160px; margin: 0 auto; }
a.return-link {
  color: #fff !important; font-size: 13px;
  font-family: 'montserrat'; font-weight: 600;
  background-image: url(arrow-left-white.png);
  background-repeat: no-repeat; padding-left: 25px;
}
a.return-link:hover { color: #f7d25b !important; }
```

### Mobile navigation (≤768px)
```css
#globalnav-wrapper { margin-bottom: 0px; margin-top: 150px; position: absolute; }
.menu-toggle { display: block; background: url('menu-toggle.png') 10px center no-repeat black;
               color: white; padding: 5px 15px 5px 35px; font-size: 80%; z-index: 5; }
#portal-globalnav { display: none; }
#portal-globalnav.opened { display: block; }
#portal-globalnav li { width: 100%; }
/* Dropdowns show as expanded stacked list on mobile */
#portal-globalnav li:hover ul.submenu { position: relative; width: 100%; margin: 0; }
```

### Breadcrumbs
```css
#portal-breadcrumbs { margin: 0; padding: 10px 20px; font-size: 12px; }
#portal-breadcrumbs a { color: #205C90; }
/* Hidden on home template: .template-landscape_home #portal-breadcrumbs { display: none; } */
```

---

## 6. Buttons & CTAs

### Default button
```css
.button {
  padding: 10px 20px; margin: 10px 0;
  background-color: white; border: 1px solid #d6d7d8;
  border-radius: 5px; line-height: 1.5em; font-size: 18px;
}
/* display: block at ≤600px */
```

### Orange buttons
```css
.btn-orange, a.btn-orange {
  background: #f8903e; padding: 10px 15px;
  border: 1px solid #fff; border-radius: 5px;
  font-size: 13px; font-weight: 600; color: #fff !important;
  letter-spacing: 0.025em;
}
#content a.btn-orange:hover { background: #F7700D; color: #fff !important; }

.btn-orange-large { /* same colors, font-size: 18px; display: inline-block */ }
```

### Red button
```css
.btn-red { background: #FF6633; padding: 10px 15px; border-radius: 5px; font-size: 18px; }
```

### Blue button
```css
a.btn-blue { background-color: #0e71eb; color: #fff !important; padding: 8px 15px; border-radius: 8px; }
#content a:hover.btn-blue { background: #1a5cbb; }
```

### CTA button (hero/section block)
```css
.cta-button {
  padding: 15px 25px; background: #f7bd4f;
  font-size: 20px; border-radius: 5px; border: 1px solid #fff; margin: 0 1.5em;
}
.cta-button:hover { background: #f38b1a; }
#content .cta-button a { color: #fff; font-family: 'Montserrat'; font-weight: 600; }
```

### Large colored link-buttons
```css
#content a.large-orange {
  background: #f8903e; color: #fff !important;
  padding: 15px; text-transform: uppercase;
  border: 1px solid #fff; border-radius: 4px;
  font-size: 14px; font-weight: 600; letter-spacing: 0.075em;
}
#content a.large-orange:hover { background: #F7700D; }

#content a.btn.large-white {
  background: rgba(255,255,255,0.25); color: #fff !important;
  padding: 15px; border: 1px solid #fff; border-radius: 4px;
  font-size: 14px; font-weight: 600; text-transform: uppercase;
}

#content a.btn.large-brown { background: #835440; color: #fff !important; /* same padding/style */ }
a.button-dark { background: #274352; color: #eaea8b !important; padding: 15px 25px; border-radius: 5px; font-size: 18px; }
```

### Overlay buttons
```css
a.overlay-btn { background: rgba(0,0,0,0.5); color: #fafafa !important; font-size: 20px; font-weight: 600; border-radius: 0 0 5px 5px; }
#content a.overlay-btn-2 { background: rgba(0,0,0,0.5); border: 1px solid #fff; font-size: 1.3em; padding: 15px; border-radius: 6px; color: #fff !important; transition: all .5s ease-in-out; }
#content a.overlay-btn-2:hover { background: rgba(255,255,255,1); color: #222 !important; }
```

### Expert / dark-theme buttons
```css
a.expert-btn {
  background: #1d3c4c; color: #f7b61b !important;
  border: 1px solid #fff; padding: 10px; margin: 1em;
  text-transform: uppercase; font-size: 16px; font-weight: 600;
}
a.button-dark { background: #274352; color: #eaea8b !important; }
a.button-dark:hover { background: #132631; color: #fb9a1e !important; }
```

### Back-to-top
```css
.back-to-top a {
  position: fixed; bottom: 0.75em; right: 0.75em;
  width: 110px; height: 35px; line-height: 35px;
  background: #222; color: #ccc !important;
  border-radius: 5px; font-size: 13px; text-transform: uppercase; z-index: 100;
}
.back-to-top:hover a { background: #000; color: #87a301 !important; }
```

---

## 7. Content blocks

### Colored content blocks
```css
.white-block  { background: #fff; margin: 0; padding: 30px; }
.grey-block   { background: #efefef; margin: 0; padding: 30px; }
.orange-block { background: #ef9b26; margin: 0; padding: 50px; min-height: 400px; }
/* Mobile: padding 30px 30px 5px; min-height: 200px */
.blue-block   { background: rgba(20 83 120 / 80%); padding: 50px 30px; min-height: 400px; }
.tan-block    { background: #e7e5da; padding: 2rem; border-radius: 6px; }
.overlay-block { padding: 30px; background: rgba(0 0 0 / 50%); }
.black-65-block { background: rgb(0 0 0 / 65%); padding: 40px; }
.black-50-block { background: rgb(0 0 0 / 50%); padding: 40px; }
```

### Block subheads (within colored blocks)
```css
.orange-block .subhead, .black-50-block .subhead {
  font-family: 'Montserrat'; letter-spacing: 4px; font-weight: 600;
  color: #b5700f;     /* or #fbd84d for black-50 */
  margin-bottom: 1em; font-size: 14px;
}
.blue-block .subhead { color: #D0F7FF; /* same style */ }
```

### Background color helpers
```css
.bg-orange     { background: #dd733e; }
.bg-white      { background: #fff; }
.bg-gold       { background: #C1B259; padding: 30px 20px; border-top: 10px solid #8e6746; }
.bg-gold-lite  { background: #f6f3ed; border: 3px solid #d5cfbe; }
.bg-green      { background: #b1c279; padding: 10px; }
.bg-grey       { background: #efefef; }
.grey-bg       { background: #f5f5f5; }
.bg-blue       { background: #657F9E; }
.bg-darkblue   { background-color: #28526E; }
.bg-lt-blue    { background: #78a9e2; }
.bg-footer-blue{ background: #2e76a0; }
```

### CTA block (homepage bar)
```css
#cta-block {
  display: grid; align-items: center; justify-items: center;
  height: 120px; background-color: #28526E;
  width: 100vw; position: relative; margin-left: -50vw; left: 50%; top: 40px;
}
```

### Hero slideshow (home page)
The home page uses `#cyclist-wrapper-full` with `.feature-slide` items:
```css
#cyclist-wrapper-full { width: 100%; height: auto; position: relative; z-index: 1; }
.feature-slide { height: 600px; overflow: hidden; position: relative; }
.feature-slide img { object-fit: cover; height: 100% !important; }
/* Mobile: height: 460px */
```

Overlay variants (centered on slide image):
```css
.slide-overlay       { position: absolute; z-index: 5; top: 24%; background: rgba(0,0,0,0.6);
                       padding: 30px 30px 40px; width: 60%; left: 20%;
                       color: #fff; border-radius: 6px; text-align: center; }
.slide-overlay-left  { /* same; left: 3%; width: 44%; top: 15% */ }
.slide-overlay-right { /* same; right: 3%; width: 38%; top: 25% */ }
/* At ≤979px: width: 70%; left: 15%; top: 20% */
/* At ≤768px: width: 90%; left: 5%; top: 8%; padding: 15px 30px 40px */
```

Slide nav (slick/cycle pager) sits at `#cyclist-nav` (absolute, `left: 42.5%`, `top: 560px`; `left: 35.5%`, `top: 360px` on mobile).

### Slick slider (non-home pages)
```css
#slick-slider {
  background: #e5e5dc; border-bottom: 6px solid #d8d4cb; border-top: 6px solid #d8d4cb;
  padding: 1.5em; min-height: 360px;
}
#slick-slider .featured > h4 { font-size: 22px; line-height: 1.2em; }
#slick-slider .featured > p  { color: #666; font-size: 16px; }
img.slick-img { width: clamp(180px, 360px, 100%); float: left; margin: 0 2rem 1rem 0; background: #fff; padding: 4px; }
```

### Feature / info boxes
```css
.featurebox, .featureboxlast {
  border: 1px solid #ccc; margin-bottom: 10px; box-shadow: 0px 0px 10px -6px rgba(0,5,68,1);
  border-radius: 4px; min-height: 400px; padding: 15px;
}
.featurebox:hover, .featureboxlast:hover { background: #ebebeb; }
.featurebox h4 { color: #0093C6; font-size: 20px; line-height: 1.2em; }
.featurebox > h4 a         { color: #0093c6 !important; }
.featurebox > h4 a:hover   { color: #009333 !important; }
```

### Grid tile layout (folder/collection views)
```css
.grid_layout { display: flex; flex-wrap: wrap; justify-content: space-between; place-content: flex-start; }
.grid_layout .tileItem {
  width: calc((90% - (3 - 1) * 25px) / 3 - 1px); margin: 0 30px 30px 0;
  border: 1px solid #ededed; transition: box-shadow 0.3s linear;
}
.grid_layout .tileItem:hover { box-shadow: 0px 5px 10px 0px #ddd; }
.gridImage img { width: 100%; height: 220px; object-fit: cover; }
.grid_layout .tileHeadline { padding: 15px 15px 5px; }
.grid_layout .tileBody     { padding: 0 15px; }
/* Collapses to 100% width at ≤770px */
```

### Image utilities
```css
.rounded    { border-radius: 8px; }
img.rounded { border-radius: 5px; }
.rounded15  { border-radius: 15px; }
.shadow-btm { box-shadow: 3px 8px 10px -4px rgb(0 0 0 / 40%); }
.image-inline { border: 1px solid #ccc; padding: 4px; max-width: 100%; background: #fff; }
.responsive-img { border: 1px solid #ccc; margin: 10px 0; max-width: 100%; padding: 4px; border-radius: 4px; box-shadow: 0 0 5px 0 rgba(0,0,0,0.1); background: #fff; }
.circle-img { border-radius: 100%; }
.image-fit  { object-fit: cover; }
```

### Portlets (sidebar)
```css
dl.portlet { font-size: 90%; border: 1px solid #DDD; margin-bottom: 1.5em; }
.portletNavigationTree .portletHeader {
  background: #222; border-radius: 5px;
  font-size: 16px; margin-top: 3em; margin-bottom: 5px;
}
.portletNavigationTree .portletHeader a { color: #9ff3ff !important; font-weight: 400; }
dl.portlet ul.navTree .navTreeCurrentItem {
  background: #f6f6f6 url("arrow-orange.png") no-repeat 5px 14px;
  margin-left: -1.3em; padding-left: 1.25em; color: #000 !important;
}
.portletItem li { font-size: 14px; list-style: none; margin-left: 10px; }
```

### Flex containers
```css
.flex-block     { display: flex; align-items: center; }  /* flex-direction: column at ≤767px */
.flex-wrapper   { display: flex; }                       /* flex-direction: column at ≤768px */
.flex           { display: flex; align-items: center; }
.flex-item-wrap { flex: 1; }
.flex-item      { flex: 1; }
.flex-wrap      { flex-wrap: wrap; }
.align-center   { align-content: center; }
```

### Column utilities (CSS columns)
```css
.threecolumn { column-count: 3; column-gap: 40px; }
.twocolumn   { column-count: 2; column-gap: 40px; }
/* Both collapse to 1 column at ≤768px */
```

### Accordion / FAQ
```css
.faq-section label { font-size: 1.2em; background: #eee; color: #205c90; display: block; padding: 7px 10px; font-weight: bold; border-radius: 5px; border: 1px solid #ddd; }
.faq-section input[type=checkbox]:checked~label { background: #f9f3d8; }
.faq-section input[type="checkbox"]:checked ~ p { color: #444; display: block; font-size: 1.1em; }
```

---

## 8. Footer

### Main LP footer (`#portal-footer`)
```css
#portal-footer {
  background: #2e76a0;    /* the base LP footer color */
  color: #fff;
  width: 100%; padding: 1.5em;
  position: relative; bottom: 0; left: 0; margin: 0;
}
#portal-footer h3 { color: #aae2fd; font-size: 20px; margin: 17px 0 10px; text-transform: uppercase; }
#portal-footer p  { color: #fff; font-size: 12px; padding-left: 15px; }
#portal-footer .sitecredit a, #portal-footer .sitecredit a:visited { color: #7dd4d6 !important; }
#portal-footer .sitecredit a:hover { color: #ffffff !important; }
#portal-footer ul.ft-menu { color: #fff; margin-top: 0; }
#portal-footer .ft-menu li a { color: #fff !important; font-size: 15px; line-height: 1.8em; }
#portal-footer .ft-menu li a:hover { border-bottom: 1px solid #fff; }
.footer-left li > a       { color: #FFFFFF !important; }
.footer-left li > a:hover { color: #FFA64D !important; }
```

### Footer layout (5-column grid)
Uses `.grid-container-5col` (5 columns, 20px gap, stacks at ≤767px):
1. WLFW logo + USDA NRCS lockup (SVG)
2. EBTJV logo + SARP logo
3. "Learn" links — About Us, Members, Community, Issues, Help
4. "Browse" links — Projects, Maps and Data, News and Events, Resources, Training
5. Contact + LP logo (SVG) + partner-site selector `<select>`

### Site credit
```css
#portal-footer .sitecredit {
  background: url("fergusonlynch-icon.png") no-repeat scroll 0 0;
  color: #aae2fd; font-size: 12px; letter-spacing: 0.05em;
  line-height: 1.1rem; padding-left: 50px; text-transform: uppercase; width: 185px;
}
```

### Sub-site-specific footers (hidden on parent, shown via sub-site CSS)
- `#portal-footer-wlfw` — WLFW footer: `display: none` (default)
- `#fire-footer`, `#sefiremap-footer`, `#bobscapes-footer`, `#birdlocale-footer`, `#portal-footer-lit-gateway` — all `display: none` on parent

---

## 9. Responsive breakpoints

| Breakpoint | Behavior |
|------------|----------|
| **1170px** | `#portal-header`, `.narrow`, `.inner-container` go 100% width |
| **979px** | `top-header` link font shrinks to 13px; slide overlays shift to `top: 20%; width: 70%; left: 15%` |
| **768px** | **Primary mobile breakpoint**: `#portal-header` height 185px; `#portal-logo` goes absolute (top: 30px, left: 10px), shrinks to 295px wide; `#portal-banner` height 130px; `#portal-globalnav` hidden, `.menu-toggle` shown; all CSS grid layouts stack; `.flex-wrapper` stacks; `#portal-searchbox` repositions; `#portal-globalnav.opened` shows stacked nav; `.section-people` portlet goes inline |
| **767px** | `.grid-container-5col` stacks to block; `.grid-container-6col` → 2 columns; `.threecolumn`/`.twocolumn` → 1 column |
| **600px** | `h1` / `.documentFirstHeading` → 30px; `.slide-area` padding adjusts; `.button` → `display: block` |
| **500px** | `.news-image img` → full-width, float none |
| **480px** | Handheld `@media` |
| **420px** | `.featuredimg` float adjusts |

---

## 10. Google Fonts

Loaded via `<link>` in `<head>`:
```
Open Sans      400, 400i, 600
Source Sans Pro 400, 700
Merriweather   400, 400i, 700
Montserrat     400, 500, 600
Nunito Sans    400, 700, 400i
Public Sans    300, 400, 700, 300i, 400i
Material Icons (icon font)
```
Plus Font Awesome 4.2.0 via MaxCDN CDN.
Slick.js slider CSS via `//cdn.jsdelivr.net/jquery.slick/1.3.15/slick.css`.

---

## 11. CSS file hierarchy (load order on the live site)

1. `reset.css`
2. `resourcejquery-*.css` (jQuery UI, `@import`)
3. `base-*.css` (Plone Barceloneta base)
4. `dropdown-menu-*.css` (`@import`)
5. `resourcetinymce.stylesheetstinymce-*.css`
6. `print.css` (media: print)
7. `mobile-*.css` (media: handheld, screen and max-device-width: 480px)
8. `resourceplone.app.jquerytools.dateinput-*.css` (`@import`)
9. `fullcalendar-*.css` (`@import`)
10. `resourceplonetruegallery-portlet-*.css` (`@import`)
11. `resourcecontentleadimage-*.css`
12. `ploneboard-*.css` (`@import`)
13. **`ploneCustom.css`** (~6400 lines) — all LP site-wide styles plus all sub-site selector blocks
14. Font Awesome 4.2.0 (CDN `<link>`)
15. Slick carousel CSS (CDN `<link>`)
16. Google Fonts (3–5 separate `<link>` requests)
17. `cyclist.css` (`@import` via inline `<style>`) — slideshow wrapper/nav styles
18. Page-template-specific inline `<style>` blocks (e.g. hiding `#content-views`, `.contentActions`)

Sub-site CSS files (e.g. `anchor.css`) are loaded last when a sub-site page is viewed; they override `ploneCustom.css` using body-class selectors like `.site-anchor` or by loading a separate stylesheet.

---

## 12. Key design decisions / parent-site vs. sub-site distinctions

- **Nav color** (`#657F9E` slate blue-gray) is the parent site's nav background. Sub-sites override it (e.g. ANCHOR uses `#27426A` navy, WLFW uses a darker navy).
- **Footer color** (`#2E76A0` medium blue) is the parent LP footer. Sub-site footers use different colors or entirely different `<div>` ids.
- **Heading color** (`#8E6747` warm brown) is uniquely the LP parent. Sub-site headings override with their own palette (ANCHOR uses `#27426A` navy).
- **Selected nav tab**: `#95A664` olive-green on parent; sub-sites use different highlight colors.
- **Nav hover**: `#4C6C8C` darker blue on parent; sub-sites vary.
- **Breadcrumbs**: Visible by default on parent (hidden on sub-site home templates or sub-site document views).
- **Left sidebar**: `#portal-column-one` can appear on parent pages; hidden on most sub-sites via `.section-X #portal-column-one { display: none; }`.
- **`nest-navigation-bar`**: Hidden (`display: none`) on parent, shown on sub-sites.
- **Home template** (`template-landscape_home`): Hides banner, edit bar, breadcrumbs, addthis toolbox; sets `#visual-portal-wrapper` to `max-width: 100%`; shows full-width hero slideshow.
- **`#portal-top`** blue stripe: Shown on parent (background-image repeating-x); hidden on sub-sites.
