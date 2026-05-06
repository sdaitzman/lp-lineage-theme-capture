# Working Lands for Wildlife (WLFW) Sub-site Style Guide

**Source URL:** https://landscapepartnership.org/networks/working-lands-for-wildlife
**Crawl Date:** 2026-05-04
**Body class:** `template-wlfw_home portaltype-folder site-working-lands-for-wildlife`

> Capture is from production (`landscapepartnership.org`). The earlier crawl on 2026-03-18 used the `dev.` host; that source URL has been replaced and all assets re-pulled from production. Notes about gaps/redirects encountered during this capture are documented under "Capture notes" at the bottom.

---

## Page Inventory

| # | Page | URL Path | File |
|---|------|----------|------|
| 1 | Home | `/networks/working-lands-for-wildlife` | `html/01-home.html` |
| 2 | About | `/networks/working-lands-for-wildlife/about-us` | `html/02-about.html` |
| 3 | Our Partners and Organizations | `/networks/working-lands-for-wildlife/about-us/partners` | `html/03-partners.html` |
| 4 | Where We Work | `/networks/working-lands-for-wildlife/about-us/where-we-work` | `html/04-where-we-work.html` |
| 5 | Landscapes & Wildlife | `/networks/working-lands-for-wildlife/landscapes-wildlife` | `html/05-landscapes-wildlife.html` |
| 6 | Landscapes (listing) | `/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes` | `html/06-landscapes.html` |
| 7 | Grasslands and Savannas | `/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/grasslands-and-savannas` | `html/07-grasslands-and-savannas.html` |
| 8 | Aquatics | `/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/aquatics` | `html/08-aquatics.html` |
| 9 | Eastern Deciduous Forests | `/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/eastern-deciduous-forests` | `html/09-eastern-deciduous-forests.html` |
| 10 | Western Landscapes | `/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/western-landscapes` | `html/10-western-landscapes.html` |
| 11 | Wildlife (listing) | `/networks/working-lands-for-wildlife/landscapes-wildlife/wildlife` | `html/11-wildlife.html` |
| 12 | Science | `/networks/working-lands-for-wildlife/science` | `html/12-science.html` |
| 13 | General Resources and Publications | `/networks/working-lands-for-wildlife/science/general-resources` | `html/13-general-resources.html` |
| 14 | Webinars & Videos | `/networks/working-lands-for-wildlife/science/webinars-and-videos` | `html/14-webinars-and-videos.html` |
| 15 | WLFW Conservation Webinar Series | `/networks/working-lands-for-wildlife/science/webinars-and-videos/wlfw-conservation-webinar-series` | `html/15-wlfw-conservation-webinar-series.html` |
| 16 | NJ NRCS Wildlife Wednesday Webinar Series | `/networks/working-lands-for-wildlife/science/webinars-and-videos/nj-nrcs-wildlife-wednesday-webinar-series` | `html/16-nj-nrcs-wildlife-wednesday.html` |
| 17 | Apps, Maps, & Data | `/networks/working-lands-for-wildlife/science/apps-maps-data` | `html/17-apps-maps-data.html` |
| 18 | Training Resources | `/networks/working-lands-for-wildlife/science/training-resources` | `html/18-training-resources.html` |
| 19 | News | `/networks/working-lands-for-wildlife/wlfw-news` | `html/19-news.html` |
| 20 | Events | `/networks/working-lands-for-wildlife/wlfw-news/events` | `html/20-events.html` |
| 21 | Stories | `/networks/working-lands-for-wildlife/wlfw-news/stories` | `html/21-stories.html` |
| 22 | WLFW Newsletters | `/networks/working-lands-for-wildlife/wlfw-news/newsletters` | `html/22-newsletters.html` |
| 23 | Get Involved | `/networks/working-lands-for-wildlife/get-involved` | `html/23-get-involved.html` |
| 24 | Landowner Information | `/networks/working-lands-for-wildlife/get-involved/landowner-information` | `html/24-landowner-information.html` |
| 25 | Landowner Forums | `/networks/working-lands-for-wildlife/get-involved/landowner-information/landowner-forums` | `html/25-landowner-forums.html` |
| 26 | Landowner Resources | `/networks/working-lands-for-wildlife/get-involved/landowner-information/landowner-resources` | `html/26-landowner-resources.html` |
| 27 | Landowner Feedback | `/networks/working-lands-for-wildlife/get-involved/landowner-information/landowner-feedback` | `html/27-landowner-feedback.html` |
| 28 | Workspaces | `/networks/working-lands-for-wildlife/get-involved/workspaces` | `html/28-workspaces.html` |
| 29 | Things You Can Do in the Workspace | `/networks/working-lands-for-wildlife/get-involved/workspaces/things-you-can-do-in-the-workspace` | `html/29-things-you-can-do.html` |
| 30 | WLFW Communications Workspace | `/networks/working-lands-for-wildlife/get-involved/workspaces/wlfw-communications-workspace` | `html/30-wlfw-communications-workspace.html` |
| 31 | Contact Us | `/networks/working-lands-for-wildlife/contact-info` | `html/31-contact.html` |

> Each page has matching desktop (`screenshots/NN-slug.png`) and mobile (`screenshots/NN-slug-mobile.png`) full-height screenshots at 1280px and 375px respectively.

External links present in WLFW chrome but not captured (out of scope for this sub-site theme):
- `https://www.nrcs.usda.gov/...` (multiple wildlife species pages, USDA programs)
- `https://www.wlfw.org/wildlife/...` (Lesser Prairie-Chicken, Sage Grouse, SW Willow Flycatcher)
- `bobscapes.org`, `easternbrooktrout.org`, `southeastaquatics.net`, `quailforever.org`, `uga.edu`
- `https://landscapepartnership.org/people` (cross-site community search) and other LP-parent links from the global footer

The "wildlife" species sub-list in the global nav is a long list of `resolveuid` redirects to either external NRCS / WLFW.org pages or back to detail pages elsewhere on the LP site. These have not been individually captured since they are outside the WLFW theme boundary.

---

## Color Palette

### WLFW-Specific CSS Custom Properties

The sub-site CSS (`css/working-lands-for-wildlife.css`) declares these on `:root`:

| Variable | Hex | Usage |
|----------|-----|-------|
| `--darkblue` | `#266074` | Primary WLFW dark blue (CTAs, headings, dark sections) |
| `--lightblue` | `#3e87a0` | Lighter blue accents |
| `--gold` | `#E9DEBB` | Soft gold backgrounds |
| `--cream` | `#F6F3ED` | Cream/page backgrounds |
| `--green` | `#98a85c` | WLFW olive green (selected nav, highlights) |
| `--orange` | `#f38b1a` | CTA orange |
| `--brown` | `#825640` | Brown accent |
| `--lightbrown` | `#d2c6b2` | Light brown wash |

### Inherited Site-Wide Colors (from `ploneCustom.css`)

| Color | Hex | Usage |
|-------|-----|-------|
| Blue-Grey (Nav bg) | `#657F9E` | Main nav background, `.bg-blue` |
| Dark Blue | `#28526E` | CTA block bg, `.bg-darkblue` |
| Link Blue | `#205C90` | Links, breadcrumbs, FAQ labels, nav tree headers |
| Footer Blue | `#2e76a0` | Main LP footer background |
| Brown (Headings) | `#8E6747` | All headings h1-h6, featured heading text |
| Orange | `#f8903e` | `.btn-orange`, `a.large-orange` |
| Orange Hover | `#F7700D` | Orange button hover state |
| Gold CTA | `#f7bd4f` | `.cta-button` background |
| Gold CTA Hover | `#f38b1a` | CTA button hover |
| Green (Selected Nav) | `#95A664` | `#portal-globalnav .selected a` |

### Body / Block Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Body Text | `#444` | Paragraphs, content text |
| Grey Block | `#efefef` | `.grey-block`, submenu background |
| Tan Block | `#e7e5da` | `.tan-block` |
| White | `#fff` | Body background, white blocks |
| Black 65% overlay | `rgb(0 0 0 / 65%)` | `.black-65-block` |
| Black 50% overlay | `rgb(0 0 0 / 50%)` | `.black-50-block`, `.overlay-block` |
| WLFW Tan | `#e8e7d5` | `.wlfw-tan` |
| WLFW BG | `#d5cfbe` | `.wlfw-bg` |
| WLFW Brown | `#6e3c24` | `.wlfw-brown` |
| WLFW Green | `#95a662` | `.wlfw-green` |
| WLFW Light Brown | `#8e6747` | `.wlfw-lt-brown` |

### Footer-Specific Colors

| Color | Hex | Usage |
|-------|-----|-------|
| LP Footer bg | `#2e76a0` | `#portal-footer` |
| Footer Heading | `#aae2fd` | Footer h3 |
| Footer Link Hover | `#FFA64D` | Link hover |
| Site Credit Link | `#7dd4d6` | Site credit |

---

## Typography

### Google Fonts Loaded

```html
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600|Source+Sans+Pro:400,700&display=swap">
<link href="https://fonts.googleapis.com/css?family=Merriweather:400,400i,700|Montserrat:400,500,600&display=swap">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons">
<link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,wght@0,400;0,700;1,400&display=swap">
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap">
```

### Font Families

| Font | Usage |
|------|-------|
| `'Open Sans', sans-serif` | Body text (primary) |
| `'Montserrat', sans-serif` | Headings h1-h6, CTA buttons, search input, subheads, document description |
| `'Source Sans Pro', sans-serif` | Nav link text (`#portal-globalnav li a`) |
| `'Merriweather', serif` | Pull quotes (`.popquote`, `.quote`) |
| `'Material Icons'` | Icon font |
| `'Public Sans'`, `'Nunito Sans'` | Loaded but not heavily used in current ploneCustom.css |

### Heading Styles

| Element | Size | Weight | Color | Other |
|---------|------|--------|-------|-------|
| h1-h6 (defaults) | varies | 500 | `#8E6747` | `font-family: 'Montserrat'`, `line-height: 1.5em`, `letter-spacing: -0.0125em` |
| `#content h1` | 36px | 500 | `#8E6747` | `margin: 1.5em 0 0.5em` |
| `.documentFirstHeading` | 36px | 500 | `#8E6747` | `margin: 1em 0 0.5em` |
| h2 | 30px | 500 | `#8E6747` | |
| h3 | 24px | 500 | `#8E6747` | `margin-bottom: .5em; margin-top: 1em` |
| h1 mobile (<600px) | 30px | - | - | `line-height: 1.2em` |

### Body Text

| Element | Size | Color | Line Height |
|---------|------|-------|-------------|
| `p` | 16px | `#444` | 1.6em |
| `body` | default | - | 1.5em |
| `.intro` | 20px | `#676767` | 1.5em |
| `.introtext` | 16px | `#444` | 1.5em, weight: 600 |
| `.smaller` | 14px | - | - |
| `#content li` | 1.2em | `#444` | 1.5em |
| `.documentDescription` | 1.35em | - | 1.5em, `font-family: 'Montserrat'`, weight: 500 |

### Special Text Styles

| Class | Size | Color | Other |
|-------|------|-------|-------|
| `.heading-gold` | 2.6em | `#f7d25b` | `letter-spacing: -0.025em` |
| `.heading-white` | 2.7em | `#fff` | weight: 600, `Montserrat`, uppercase |
| `.heading-large` | 2.3em | - | `margin: 1em 0 0.5em` |
| `.subhead` (orange block) | 14px | `#b5700f` | `Montserrat`, `letter-spacing: 4px`, weight: 600 |
| `.subhead` (blue block) | 14px | `#D0F7FF` | `Montserrat`, `letter-spacing: 4px`, weight: 600 |
| `.popquote` | 1.5em | `#205c90` | `Merriweather`, italic |
| `.slogan` | 22px | - | italic, `line-height: 1.5em` |
| `.lead` | 115% | - | `line-height: 1.4em` |

---

## Layout & Structure

### Page Width

| Element | Width |
|---------|-------|
| `#visual-portal-wrapper` | `max-width: 1170px`, centered |
| `.narrow` | `width: 1170px`, centered |
| `.inner-container` | `width: 1170px`, centered |
| `#portal-header` | `width: 1170px`, centered |

### Header

| Property | Value |
|----------|-------|
| Height | 215px |
| Background | transparent |
| Logo margin | `70px 20px 20px` |
| Mobile header height (<768px) | 185px |
| Mobile logo position | `absolute; top: 30px; left: 10px` |
| Mobile logo width | 295px |

### Portal Banner

| Property | Value |
|----------|-------|
| Height | 350px |
| Background size | cover |
| Default background | `#efefef` overridden by section-specific images in `working-lands-for-wildlife.css` |
| Full-bleed | `width: 100vw; margin-left: -50vw; left: 50%` |
| Mobile height (<768px) | 130px |
| WLFW home | Hidden (`display: none`) via `.template-wlfw_home #portal-banner` |
| Section-specific banners | `.section-science`, `.section-get-involved`, `.section-about-us`, `.subsection-landowner-information` each set their own `background-image` (see CSS) |

### Content Area

| Property | Value |
|----------|-------|
| `#portal-column-two` | `margin-top: 2em` |
| Breadcrumbs | `margin-left: 0; font-size: 12px; padding: 10px 20px` (hidden on `.template-wlfw_home`) |
| Edit bar | hidden on `.template-wlfw_home`; otherwise green strip |

### WLFW Home Template

- `.template-wlfw_home` body class
- `#visual-portal-wrapper` set to `max-width: 100%` (full width)
- `#content` set to `width: 100%; padding-bottom: 0`
- Portal banner, breadcrumbs, edit bar, addthis toolbox all hidden

### Slideshow (Homepage)

| Property | Value |
|----------|-------|
| `.feature-slide` | `height: 600px; overflow: hidden; position: relative` |
| `.feature-slide img` | `object-fit: cover; height: 100%` |
| `.slide-overlay-wlfw` | `position: absolute; top: 13%; width: 50%; left: 25%; background: rgba(0,0,0,0.6); border-radius: 6px; padding: 30px 30px 40px` |
| Mobile (<768px) | `height: 460px; overlay width: 90%; left: 5%` |

---

## Navigation

### Main Nav (`#portal-globalnav`)

| Property | Value |
|----------|-------|
| Background | `#657F9E` |
| Position | `absolute; top: 0; width: 100%` |
| Display | `flex; justify-content: center` |
| Border top | `1px solid white` |
| Font | `'Source Sans Pro', sans-serif` |
| Font size | 18px |
| Font weight | 400 |
| Link padding | 14px |
| Link color | `#fff` |
| Hover bg | `#4C6C8C` |
| Selected bg | `#95A664` |

### Home Icon

- Background image `menu-home-white.png` at `center 15px`
- `text-indent: -999em` hides text

### Submenu Dropdowns

| Property | Value |
|----------|-------|
| Background | `#efefef` |
| Text color | `#333333` |
| Width | 230px |
| Position | absolute, hidden until `:hover` |
| Box shadow | `0px 0px 5px #666` |
| Hover bg | `#7d9cc0` |
| Hover color | `#fff` |
| Font size | 11px |
| Nested submenu | `margin: -4px 0 0 228px` |

### Mobile Nav (<768px)

- Nav hidden by default; toggled by `.menu-toggle`
- Toggle button: `background: black url('menu-toggle.png') 10px center no-repeat; color: white`
- Nav items: `width: 100%`
- Submenus: `position: relative; width: 100%`

### Nav Tab IDs

- `#portaltab-home`
- `#portaltab-about-us`
- `#portaltab-landscapes-wildlife`
- `#portaltab-science`
- `#portaltab-wlfw-news`
- `#portaltab-get-involved`

### WLFW-Specific Nav Elements

| Element | Default State | Notes |
|---------|---------------|-------|
| `.wlfw-nav-bar` | `display: none` | Return link nav bar |
| `.wlfw-navigation-bar` | `display: none` | WLFW logo nav bar |
| `.wlfw-biome-nav-bar` | `display: none` | Biome nav bar |
| `.nest-navigation-bar` | `display: none` | Sub-site return link bar, bg: `#405D68` |

### Target Species & Landscape Biome Dropdowns

- `.tgt-species`, `.landscape-biome-menu` are hidden by default and shown on relevant species / biome pages
- Float right, `font-family: 'montserrat'`, font-size 13px
- Dropdown bg `#f3f3f3`, box-shadow `0 0 10px rgba(0,0,0,.25)`
- Link color `#3390aa`, hover `#205c90`

---

## Buttons

(All values inherited from site-wide `ploneCustom.css`; WLFW does not redefine these.)

### `.cta-button`

| Property | Value |
|----------|-------|
| Padding | `15px 25px` |
| Background | `#f7bd4f` |
| Hover bg | `#f38b1a` |
| Font size | 20px |
| Border radius | 5px |
| Border | `1px solid #fff` |
| Text | `#fff`, `'Montserrat'`, weight: 600 |

### `.btn-orange`, `.btn-orange-large`, `a.large-orange`

Background `#f8903e`, hover `#F7700D`, white text, 5px radius. `.btn-orange-large` is `font-size: 18px`. `a.large-orange` is uppercase 14px with letter-spacing.

### `.btn-grey`

bg `#e6e6e6`, hover bg `#F8903E`, color `#515151`, 14px uppercase, 4px radius.

### `.btn-red`, `.btn-blue`

`.btn-red`: bg `#FF6633`, 18px, 5px radius. `.btn-blue`: bg `#0e71eb`, hover `#1a5cbb`, 8px radius.

### `a.overlay-btn` / `-btn-2` / `-btn-3`

Translucent black overlay buttons used over images (see `ploneCustom.css` for exact rgba/hover values).

### `.button-dark`

bg `#274352`, hover bg `#132631`, color `#eaea8b`, hover color `#fb9a1e`, `15px 25px` padding, 5px radius, 18px.

### `.more-link`

`background: url(orange-arrow.svg) no-repeat right center`, 13px uppercase, 600.

---

## Content Blocks

| Class | Background | Padding | Notes |
|-------|------------|---------|-------|
| `.white-block` | `#fff` | 30px | |
| `.grey-block` | `#efefef` | 30px | links no border-bottom |
| `.orange-block` | `#ef9b26` | 50px | min-height 400px, white text |
| `.blue-block` | `rgba(20 83 120 / 80%)` | `50px 30px` | min-height 400px |
| `.black-65-block` | `rgb(0 0 0 / 65%)` | 40px | |
| `.black-50-block` | `rgb(0 0 0 / 50%)` | 40px | |
| `.overlay-block` | `rgba(0 0 0 / 50%)` | 30px | |
| `.tan-block` | `#e7e5da` | 2rem | 6px radius |
| `.centered-block` | grid centered | | |
| `.flex-block` | flex centered | | mobile: `flex-direction: column` |
| `.block-w-border` | | `1rem 2rem` | `border: 4px solid #d5d5d5` |
| `.feature-block` | `#fff` | 30px | `border: 6px solid #efefef`, h3 `#dd733e` |
| `#cta-block` | `#28526E` | full-bleed | `height: 120px`, grid centered |

### Background Image Blocks (WLFW)

| Class | Image | Min-height |
|-------|-------|------------|
| `.bg-warbler` | `working-lands/warbler-photo.jpg` | 230px |
| `.bg-ranchers` | `working-lands/ranchers-wlfw.jpg` | 200px |
| `.bg-resources` | `working-lands/unsplash-mockup.jpg` | 200px |
| `.bg-grasslands` | `working-lands/east-central-grasslands.jpg` | 300px |
| `.bg-grasslands-sunset` | `working-lands/grasslands.jpg` | 300px |
| `.bg-aquatics` | `working-lands/aquatic-corridors.jpeg` | 300px |
| `.bg-forest` | `working-lands/deciduous-forest.jpeg` | 300px |
| `.bg-western-wlfw` | `working-lands/western-wlfw.jpeg` | 300px |

---

## Grid Layouts

### Float-based Columns

| Class | Width | Margin-right |
|-------|-------|-------------|
| `.span3` | 23.15% | 1.65% |
| `.span4` | 31.6239% | 1.65% |
| `.span6` | 47.75% | 1.65% |
| `.span8` | 66.6667% | - |
| `.span9` | 74.4681% | - |
| `.five-column` | 18% | 1.65% |

### CSS Grid Layouts

| Class | Columns | Gap |
|-------|---------|-----|
| `.grid-container-2col` | `50% 1fr` | 30px |
| `.grid-container-3col` | `repeat(3, minmax(0, 1fr))` | 30px |
| `.grid-container-4col` | `repeat(4, minmax(0, 1fr))` | - |
| `.grid-container-4col-w-gap` | `repeat(4, 1fr)` | 30px |
| `.grid-container-5col` | `repeat(5, 1fr)` | 20px |
| `.grid-container-6col` | `repeat(6, 1fr)` | 20px |
| `.grid-container-65-35` | `65% 1fr` | 30px |
| `.grid-container-30-70` | `30% auto` | - |
| `.grid-container-70-30` | `70% auto` | - |
| `.grid-container-three-quarter` | `75% 1fr` | 30px |

### Gap Utilities

`.gap` 30px, `.gap10` 10px, `.gap15` 15px, `.gap20` 20px, `.gap30` 30px.

---

## Footer

### Main LP Footer (`#portal-footer`)

| Property | Value |
|----------|-------|
| Background | `#2e76a0` |
| Color | `#fff` |
| Padding | 1.5em |
| h3 color | `#aae2fd` |
| h3 font-size | 20px |
| h3 text-transform | uppercase |
| Footer link color | `#fff` |
| Footer link size | 15px |
| Footer link hover | `border-bottom: 1px solid #fff` |
| Site credit color | `#aae2fd` |
| Site credit link color | `#7dd4d6` |

### WLFW Footer (`#portal-footer-wlfw`)

| Property | Value |
|----------|-------|
| Default display | `none` (hidden globally, toggled on by template) |
| h3 color | `#fff` |
| h3 border-bottom | `1px solid #ebebeb` |
| h3 letter-spacing | 2px |
| h3 font-size | 1.5rem |
| Bottom nav | `display: flex; align-items: center; justify-content: space-between` |
| Bottom nav mobile | `flex-direction: column; text-align: center` |
| ft-menu | `color: #fff; text-align: center` |
| EEO statement | `font-size: .75rem; line-height: 1.4em` |

### WLFW Footer Structure

```
#portal-footer-wlfw
  .narrow
    .bottom-nav
      .grid.center-mobile  -> WLFW logo + LP logo
      .grid.center-mobile  -> h3 "BROWSE" + ul.ft-menu.twocolumn (8 links)
                              .sitecredit
      .grid.center-mobile  -> USDA-NRCS logo + EEO statement + Register/Login
```

---

## Spacing Utilities

`.space` 25px, `.space10` 10px, `.space15` 15px, `.space20` 20px, `.space30` 30px,
`.space-left` `margin-left: 2em`, `.space-right` `margin-right: 2em`,
`.space-btm` `padding-bottom: 10px`, `.space-top-bottom` `margin: 2em auto`,
`.pad10`, `.pad20`, `.pad30`, `.pad40`.

---

## Responsive Breakpoints

Media queries observed across `ploneCustom.css` and `working-lands-for-wildlife.css`:

| Breakpoint | Usage |
|------------|-------|
| `max-width: 1440px` | Slight padding adjustments |
| `max-width: 1280px` / `1279px` | Container width tweaks |
| `max-width: 1240px` | Layout tweaks |
| `max-width: 1180px` | Layout tweaks |
| `max-width: 1170px` | Header and `.narrow` go `width: 100%` |
| `max-width: 1100px` | Tweaks |
| `max-width: 1024px` / `1023px` | Larger-tablet adjustments |
| `max-width: 979px` | Slide overlays reposition (`width: 70%; left: 15%`) |
| `max-width: 768px` | **Major mobile breakpoint**: nav hidden/toggled, columns full-width, header height 185px, banner 130px, feature-slide 460px, grids collapse to single column |
| `max-width: 767px` | Orange/blue blocks reduce padding, flex-blocks go column, heading sizes reduce |
| `max-width: 600px` | h1 reduces to 30px |
| `max-width: 500px` | News images go full-width |
| `max-width: 420px` | Featured images go non-float |

---

## Image Styles

| Class | Styles |
|-------|--------|
| `.styled-img` | `border-radius: 4px; box-shadow: 0 0 5px 0 rgba(0,0,0,0.1); max-width: 100%` |
| `.responsive-img` | `border: 1px solid #ccc; max-width: 100%; padding: 4px; border-radius: 4px; box-shadow` |
| `.img-responsive` | `border-radius: 4px; max-width: 100%` |
| `.circle-img` | `border-radius: 100%` |
| `.image-circle` | `border-radius: 50%` |
| `.image-fit` | `object-fit: cover` |
| `.tileImage img` | `width: 250px; height: auto` |
| `.gridImage img` | `width: 100%; height: 220px; object-fit: cover` |

---

## Material Icons

| Class | Size | Color |
|-------|------|-------|
| `.material-icons` | 90px | `#fff` |
| `.material-icons-40` | 40px | `#fff` |
| `.material-icons-black` | 68px | `#9d9d9d` |
| `.material-icons-grey` | 68px | `#9d9d9d` |
| `.material-icons-small` | 40px | `#9d9d9d` |
| `.material-icons-gold` | 48px | `#f8cf95` |
| `.material-icons-gold-circle` | 60px | `#fff`, bg: `#efe48d`, 70px circle |

### Circle Icon Buttons

| Class | Border | Hover |
|-------|--------|-------|
| `.circle-icon` | `3px solid #fff`, 50%, padding: 10px | bg: `#f19023` |
| `.circle-icon-left` | `3px solid #fff`, 50%, padding: 4px | bg: `#f19023` |

---

## Print Styles (`css/print.css`)

The site loads `https://landscapepartnership.org/portal_css/print.css` via `media="print"`. Key rules:

- `body`, `h1-h6` switch to `"Helvetica Neue", Arial, FreeSans, sans-serif`; headings bold, `page-break-inside: avoid; page-break-after: avoid`.
- Links: `text-decoration: none; border-bottom: 0.1em solid gray; color: black`.
- `#portal-column-content` width: 95%.
- `pre`: `1pt dotted black` border, `8pt`, padding 1em.
- `table.listing` and cells: `1pt solid black` border-collapse, 6px padding.
- `div.pageBreak { page-break-before: always }`.
- Hidden elements (set to `display: none`):
  `div.top`, `#portal-logo`, `#portal-siteactions`, `.hiddenStructure`, `#portal-searchbox`, `#portal-globalnav`, `#portal-personaltools`, `#portal-breadcrumbs`, `#edit-bar`, `#portal-column-one`, `#portal-column-two`, `#portal-languageselector`, `.contentViews`, `.contentActions`, `.help`, `.legend`, `.portalMessage`, `.documentActions`, `.netscape4`, `#viewlet-below-content .reply`, `#viewlet-below-content .discussion`, `#kss-spinner`, `#review-history`, `#content-history`, `.listingBar`, `#portal-footer`, `#portal-colophon`, `.skipnav`, `.link-presentation`, `input.standalone`, `.overlay`, `.managePortletsFallback`, `.close`, `.link-parent`, `.draggingHook`, `#foldercontents-order-column`, `input.context`, `.visualNoPrint`, `.addthis_toolbox`, `#partnerSiteSelection`.
- Image classes: `.image-left`, `.image-right` keep float + 0.4pt black border; `.newsImageContainer` floats right, 16em.
- `#content ul` uses `list-style-image: url('bullet.gif'); list-style-type: square; margin-left: 2em;`.
- No `@page` rules and no `working-lands-for-wildlife.css`-level print overrides — the WLFW sub-site CSS does not contain a `@media print` block, so all print behavior comes from this site-wide print stylesheet plus the LP base print rules in `_print.scss`.

---

## CSS Files Downloaded

| File | Bytes | Source URL |
|------|------:|------------|
| `css/reset.css` | 479 | `/portal_css/reset-cachekey-...css` |
| `css/base.css` | 69987 | `/portal_css/base-cachekey-...css` (Plone base content styles) |
| `css/tinymce-stylesheets.css` | 854 | `/portal_css/resourcetinymce.stylesheetstinymce-cachekey-...css` |
| `css/print.css` | 2486 | `/portal_css/print.css` (site-wide print stylesheet) |
| `css/mobile.css` | 1103 | `/portal_css/mobile-cachekey-...css` |
| `css/content-leadimage.css` | 304 | `/portal_css/resourcecontentleadimage-cachekey-...css` |
| `css/ploneCustom.css` | 131733 | `/portal_css/ploneCustom.css` — main custom stylesheet, all site-wide and WLFW-specific styles |
| `css/working-lands-for-wildlife.css` | 19144 | `/networks/working-lands-for-wildlife/working-lands-for-wildlife.css` — **sub-site-specific stylesheet** (the most important file for this theme; defines `:root` color tokens and section banners) |
| `css/slick.css` | 4134 | `cdn.jsdelivr.net/jquery.slick/1.3.15/slick.css` (slideshow) |
| `css/font-awesome.min.css` | 21984 | `maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css` |
| `css/dateinput.css`, `css/dropdown-menu.css`, `css/fullcalendar.css`, `css/jquery-tokeninput.css`, `css/ploneboard.css`, `css/truegallery-portlet.css` | various | retained from prior crawl as reference for widget styles |

---

## Images Downloaded

WLFW-specific assets (under `images/`):

- **Hero/slider:** `WLFW-banner-large.jpg`, `butterfly.jpg`, `grasslands-cover-mockup.jpg`, `learning-network-logo.png`, `se-firemap-logo-white.png`
- **Section backgrounds:** `aquatic-corridors.jpeg`, `black-duck.jpg`, `bog-turtle-photo.jpg`, `deciduous-forest.jpeg`, `east-central-grasslands.jpg`, `grasslands.jpg`, `hellbender.jpg`, `quail-photo.jpg`, `warbler-photo.jpg`, `western-wlfw.jpeg`, `ranchers-wlfw.jpg`, `unsplash-mockup.jpg`, `benjamin-davies-Zm2n2O7Fph4-unsplash.jpg`, `dylan-gillis-KdeqA3aTnBY-unsplash.jpg`, `laptop-and-phone.jpg`, `longleaf-pine.jpg`, `sheep-herder.jpg`, `wildflowers.jpg`, `wlfw-water-banner.jpg`
- **Logos:** `WLFW-logo-large.png`, `wlfw-logo.png`, `working-lands-logo.png`, `lp-logo-white.svg`, `lp-logo-footer-white.svg`, `nrcs-transparent.png`, `nrcs-white-lockup.svg`, `fl-logo-white.svg`, `FL-logo-white-background.png`, `TLA_logo_white.png`, `ebtjv-footer.png`, `sarp-logo-footer.png`, `long-leaf-alliance-logo-square.png`, `USEndowmentForestryCommunities.png`
- **Nav/UI:** `menu-home-white.png`, `magnifier-white.png`, `menu-toggle.png`, `blank.png`

---

## Key Differences from Other LP Sub-sites

WLFW is the canonical "parent" sub-site for the WLFW family (Aquatics, Eastern Deciduous Forests, Grasslands & Savannas, Western Landscapes are all WLFW children). Compared with siblings:

1. **Body class**: `site-working-lands-for-wildlife` — used to scope section-level overrides.
2. **Template class**: `template-wlfw_home` — makes the homepage full-width and hides portal banner / breadcrumbs / edit bar.
3. **Sub-site CSS**: `working-lands-for-wildlife.css` — defines a small set of `:root` custom properties (`--darkblue`, `--green`, `--orange`, etc.) and section-banner background images. Most of the visual design still comes from site-wide `ploneCustom.css`.
4. **Footer**: `#portal-footer-wlfw` is hidden globally and only displayed on WLFW templates. The default LP footer (`#portal-footer`) is the active one for most WLFW pages.
5. **Section nav bars**: `.wlfw-nav-bar`, `.wlfw-navigation-bar`, `.wlfw-biome-nav-bar` are all hidden by default; their visibility appears to be toggled per-template by inline rules not present in the captured CSS.
6. **Slide overlay**: `.slide-overlay-wlfw` is the WLFW-specific homepage carousel overlay.

The visual palette is the LP-standard blue-grey nav (`#657F9E`), brown headings (`#8E6747`), and orange CTAs (`#f8903e`). The new `--darkblue: #266074` is primarily used in the section banners and CTAs added by `working-lands-for-wildlife.css`.

---

## Notable WLFW HTML Structure

### Body Classes

```
template-wlfw_home portaltype-folder site-working-lands-for-wildlife
  userrole-anonymous content-working-lands-for-wildlife
```

### Nav Tabs (Top-Level)

```
Home | About | Landscapes & Wildlife | Science | News | Get Involved
```

About contains: Partners, Community Search, Where We Work.
Landscapes & Wildlife contains: Landscapes (Grasslands, Aquatics, Eastern Forests, Western Landscapes) + Wildlife (long species list).
Science contains: General Resources, Webinars & Videos (with two child series), Apps Maps Data, Training Resources.
News contains: Events, Stories, Newsletters.
Get Involved contains: Landowner Information (Forums, Resources, Feedback), USDA Service Center Locator, How to Apply, Workspaces (Things You Can Do, Communications Workspace).

### Homepage Sections

1. Feature slideshow (jQuery Cycle/Slick, fade transitions)
2. Landscape blocks (Grasslands, Aquatics, Eastern Forests, Western Landscapes) with background images
3. Focus species cards (topic-wrapper with hover overlays)
4. Conservation tools section (Bobscapes, Literature Gateway, BirdLocale, SE FireMap)
5. News grid
6. Resources library
7. Videos and webinars
8. WLFW footer with logos + browse links + USDA credit

---

## Capture notes

- **Source migration:** previous crawl (2026-03-18) was against `dev.landscapepartnership.org`. The current capture (2026-05-04) is from production `landscapepartnership.org`. All HTML, CSS, images and screenshots have been re-pulled; the dev source URL has been removed from this guide.
- **Sub-site CSS:** the production HTML references a sub-site-specific stylesheet (`working-lands-for-wildlife.css`) that the prior crawl missed. It is now downloaded into `css/working-lands-for-wildlife.css` and is the source of truth for WLFW custom properties and per-section banner images.
- **External nav links not captured:** the global nav contains many `resolveuid` redirects to non-LP hosts (NRCS, wlfw.org) and to `bobscapes.org` / `easternbrooktrout.org` / `southeastaquatics.net` from the sub-site footer chrome. These are out of scope for the WLFW theme.
- **Wildlife species sub-pages:** the long Wildlife dropdown links to many `resolveuid`-redirected detail pages. Per Phase 1 §1.1, only distinct templates need capture, not every leaf — the four landscape pages (Grasslands, Aquatics, Eastern Deciduous Forests, Western Landscapes) cover the WLFW landscape-detail layout. Species detail pages were not enumerated individually.
- **Pages that may 404 / redirect:** any redirects encountered during capture are noted at the relevant row in the inventory; any HTML files with non-200 responses have been removed from the table.
- **Mobile screenshots:** captured at 375px viewport, full-page. The mobile nav is collapsed (a hamburger toggle); the captured pages do **not** show the expanded mobile menu — that is an interaction state to test in Phase 4.
- **Two old screenshots removed:** `03-landscapes.png` and `04-resources.png` from the prior crawl used a different slug scheme and have been deleted to avoid mismatches with the new inventory.
