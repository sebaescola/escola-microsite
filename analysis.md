# Escola Design System Analysis

**Source pages analysed:** escola.ch/digitale-verwaltung · escola.ch/zurich-event.php  
**Date:** 2026-04-08  
**CSS ground truth:** https://www.escola.ch/css/escola-page.css (versioned as `?12`)

---

## 1. Typography

### Font Families

| Role | Family | Format | Hosting |
|------|--------|--------|---------|
| Display / Headings (h4, labels) | `Gothamrounded` | OTF | Self-hosted at `/fonts/GothamRounded-*.otf` |
| Body / UI | `Nunito` | WOFF2 + WOFF | Self-hosted at `/fonts/nunito/nunito-*.woff2` |
| Icons | Font Awesome Pro 6.5.1 | WOFF2 | Self-hosted at `/fonts/fontawesome/6.5.1/` |

Gotham Rounded weights available: 300 Light, 400 Book, 500 Medium, 700 Bold (plus italic variants).  
Nunito weights available: 400, 500, 600, 700.

**Fallback stack:** `Nunito, sans-serif` on `body`.

---

### Type Scale

| Element | Font | Size | Line-height | Weight | Align | Letter-spacing | Colour |
|---------|------|------|-------------|--------|-------|----------------|--------|
| `<body>` | Nunito | 14px | 20px | 400 | — | — | #333333 |
| `<h1>` | Nunito | 38px | 44px | 700 | center | — | inherited |
| `<h2>` | Nunito | 38px | 40px | 700 | center | 1px | rgba(0,0,0,0.8) |
| `<h3>` | Nunito | 24px | 30px | 400 | center | — | rgba(0,0,0,0.6) |
| `<h4>` | Gothamrounded | 18px | 24px | 700 | — | 1.2px | #0083DB |
| `<h5>` | Nunito | 18px | 20px | 400 | center | — | #494949 |
| `<p>` | Nunito | 18px | 24px | 300 | center | 0.3px | #494949 |
| Hero paragraph | Nunito | 56px | 72px | — | — | — | #0083DB |
| Nav link | Nunito | 18px | — | 700 | — | 0.8px | #333333 |
| Button (primary) | Nunito | 16px | — | 700 | center | 4px (uppercase) | #FFFFFF |
| Button (secondary) | Nunito | 15px | — | 700 | — | 0.1px | #FFFFFF |
| Register btn | Nunito | 15px | 140% | 700 | — | 0.03em | #0083DB |
| Footer button | Nunito | 15px (1.05vw fluid) | 140% | 700 | center | 0.03em | #0083DB |
| Label (form) | Nunito | 11px | — | 700 | — | — | #5E5E5E |
| Input text | Nunito | ~14.4px (.9rem) | 1.5 | 400 | — | — | #4C4C4C |
| Modal title | Nunito | 24px | 120% | 700 | — | 0.01em | #000000 |
| Checkbox label | Nunito | 20px | 120% | 700 | — | 0.01em | product colour |
| Body text (modal) | Nunito | 15px | 140% | 400 | left | 0.01em | #333333 |

**Key observations:**
- H1 and H2 share the same size (38px) — differentiated by letter-spacing (H2 +1px) and slight colour opacity difference.
- Paragraph text is centred by default; modal/card body text is left-aligned.
- Headings use `text-align: center` throughout landing page sections.
- The hero number/stat is rendered at 56px in #0083DB to create maximum visual impact.

---

## 2. Colour System

### Primary Palette

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-primary` | `#0083DB` | Buttons, nav active/hover, h4 colour, footer background, links |
| `--color-primary-dark` | `#006CB5` | Button hover/pressed state |
| `--color-primary-mid` | `#007FE7` | Secondary CTA buttons (`button-2`) |
| `--color-primary-light` | `#009DDB` | Lighter accent |
| `--color-light-blue` | `#A8DCFF` | Footer link text, light accent labels |
| `--color-card-bg` | `#EAF7FF` | Card default background (very light blue tint) |
| `--color-card-bg-hover` | `#B7DAF1` | Card hover background |

### Neutrals

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-text` | `#333333` | Primary body text, nav links |
| `--color-text-medium` | `#494949` | Paragraph text, h5 |
| `--color-text-muted` | `#5E5E5E` | Form labels, secondary text |
| `--color-border` | `#C2C2C2` | Input borders |
| `--color-border-light` | `#D6D6D6` | Button outlines |
| `--color-border-divider` | `#EEEEEE` | Modal header border, section dividers |
| `--color-bg` | `#FFFFFF` | Page background |
| `--color-bg-section` | `#F2F2F2` | Alternate section backgrounds |

### Product Accent Colours

Each Escola product has a dedicated accent colour used for labels, icons, and background tints (10% opacity):

| Product | Hex | Tint (10%) |
|---------|-----|------------|
| Schulmanager | `#FF8483` | `rgba(255,132,131,0.10)` |
| Förderplanung | `#65CFCE` | `rgba(101,207,206,0.10)` |
| Webauftritt | `#DC87C4` | `rgba(220,135,196,0.10)` |
| Lernwelt | `#938EDF` | `rgba(147,142,223,0.10)` |
| Schulangebote | `#E0A025` | `rgba(224,160,37,0.10)` |
| Escola App | `#1B77D1` | `rgba(27,119,209,0.10)` |

### Colour Application Rules
- **Footer background = primary blue** (`#0083DB`). All footer text is white (`#FFFFFF`) or light-blue (`#A8DCFF`).
- **Buttons:** filled = `#0083DB` white text; outline = transparent/`#0083DB` border; ghost = `hsla(0,0%,100%,0.2)` with dark text.
- **Nav hover** = `inset 0 4px 0 0 #0083DB` border + `color: #0083DB` — a top-bar indicator, not background fill.
- **Card selection** = fills entire card with `#0083DB`.
- **Error** = `#FE5F55` text on `#FCE5E5` background.
- No dark mode detected.

---

## 3. Spacing & Layout

### Base Unit
4px grid. Key values: 4, 8, 12, 16, 20, 24, 32, 40, 48, 60, 64, 80, 96px.

### Containers

| Name | Max-width | Notes |
|------|-----------|-------|
| `.container` | 1300px | Main content container |
| `.nav-container` | 1260px | Navbar inner |
| `.container-narrow` | 1000px | Narrower content (e.g. text sections) |
| `.max-width-1440` | 1440px | Full-bleed with max cap (footer, etc.) |
| `.max-width-text` | 884px | Hero text paragraph max-width |
| Modal dialog | 766px | Desktop modal max-width |

### Section Padding

| Class | Padding |
|-------|---------|
| `.section` | `80px 60px 0px` |
| `.section--first` | `padding-top: 100px` (accounts for 80px fixed navbar) |
| `.section--large-padding` | `80px 60px` |
| `.section-blue` | `80px` top + bottom |
| `.content` | `104px 48px` |
| `.features-container` | `60px 68px 54px` |

### Card Spacing
- Card: `padding: 16px 16px 8px 24px`, `margin: 24px`, `max-width: 288px`
- Card small: `width: 240px`, `padding-top: 12px`, `padding-right: 24px`
- Grid gap: 16px

### Component Internal Spacing
- Modal header: `padding: 17.5px 32px`
- Modal body: `padding: 32px`
- Modal footer: `padding: 1rem`
- Nav height: `80px`
- Nav link padding: `30px 16px`

---

## 4. Component Catalogue

### Navigation Bar
- **Position:** Fixed, `z-index: 400`, full-width
- **Background:** White (`#FFFFFF`) with `box-shadow: 0 0 40px 0 rgba(20,20,20,0.10)`
- **Height:** 80px
- **Max-width inner:** 1260px, horizontally centred
- **Logo:** Left-aligned SVG (`/images/Logo-Blue.svg`)
- **Links:** Right-aligned, 5 nav items + `Anmelden` CTA + "Testzugang" button
- **Link style:** Nunito bold 18px, `#333333`, `letter-spacing: 0.8px`
- **Active/hover indicator:** `inset 0 4px 0 0 #0083DB` top-border via box-shadow + `color: #0083DB`
- **Dropdown:** `.has-drop-down` with accordion behaviour on mobile
- **Mobile:** Hamburger toggle, collapses to full-screen mobile menu; `.white_section` (desktop dropdown) hidden below 991px

### Hero Section
- **Background:** Typically white or very light, no heavy gradients on product pages
- **Headline:** H1 or large paragraph at 56px / 72px line-height in `#0083DB`
- **Subheadline:** H3 at 24px / 30px, `rgba(0,0,0,0.6)`
- **CTA buttons:** Primary blue + outline white side-by-side
- **Max text width:** 884px centred

### Feature / Benefit Cards (`.card`)
- **Layout:** Flex row of cards, `max-width: 288px` each, `margin: 24px`
- **Background:** `#EAF7FF` (light blue tint)
- **Border-radius:** 8px
- **Hover:** Scale 1.02 + deep box-shadow `0 37px 90px -55px rgba(0,0,0,0.6)` + `#B7DAF1` bg
- **Selected state:** Full `#0083DB` fill
- **Icon:** Product-colour SVG icon top-left
- **Content:** Product name (font-weight 700, product colour) + description paragraph

### Product Label Cards (Modal / Selection)
- **Label background:** Product tint (10% opacity)
- **Checkbox label text:** 20px bold, product accent colour
- **Layout:** 2-column grid on desktop, single column on mobile (`<= 991px`)
- **Gap:** 16px

### CTA Buttons

| Variant | Class | Background | Border | Text | Radius | Padding |
|---------|-------|-----------|--------|------|--------|---------|
| Primary | `.button` | `#0083DB` | none | white, uppercase, 16px bold, ls 4px | 8px | 24px 32px 22px |
| White | `.button.button-white` | `#FFFFFF` | none | `#0083DB` | 8px | same |
| Secondary | `.button-2` | `#007FE7` | none | white, 15px bold | 4px | 12px 15px |
| Ghost | `.button-3` | `hsla(0,0%,100%,0.2)` | `inset 0 0 0 1px rgba(0,0,0,0.2)` | dark 60% | 4px | 13px 16px 12px |
| Outline | `.btn-outline-primary` | transparent | `#0083DB` | `#0083DB` | 0.2rem | 12.5px 32px |
| Register | `.register-btn` | transparent | `1px solid #D6D6D6` | `#0083DB` | 5px | 0 8px/16px |

**Hover rules:**  
- Primary: `box-shadow` grows + `letter-spacing` tightens slightly (200ms ease)  
- Outline primary: fills with `#0083DB`, text turns white  
- Footer buttons: border `inset 0 0 0 1px #0083DB`

### Footer
- **Background:** `#0083DB` (full primary blue)
- **Layout:** Multi-column grid inside `.max-width-1440` container
- **Columns:** Products · Über uns / Links · Kontakt · Social
- **Text:** White (`#FFFFFF`); secondary links `#A8DCFF`
- **Logo:** White version (`/images/eacola-logo.svg` or Logo-Blue.svg inverted)
- **Social icons:** Font Awesome, width `10vw` (max 48px)
- **Footer buttons:** `width: 20vw` (max 300px), rounded 3px, semi-transparent bg, `#0083DB` text with Nunito bold

### Modal (Multi-step Form)
- **Overlay:** `rgba(0,0,0,0.5)` fixed full-screen
- **Dialog:** max-width 766px desktop, `margin: 1.75rem auto`
- **Content:** white, `border: 1px solid rgba(0,0,0,0.2)`, `border-radius: 0.3rem`
- **Header:** `padding: 17.5px 32px`, bottom border `1px solid #eee`
- **Title:** 24px bold, `#000000`, `line-height: 120%`, `letter-spacing: 0.01em`
- **Body:** `padding: 32px`
- **Steps:** Products selection → Basic info (contact form) → Success message
- **Error state:** `#FCE5E5` bg, `#FE5F55` text

### Event Details Block (zurich-event.php pattern)
- Sections: Wann (date) · Wo (location) · Zeitplan (schedule) · Gäste (guests)
- Each block: label + value, left-aligned
- Location: links to Google Maps
- Timeline: `ab HH:MM Uhr` format, inline list

### App Store Reviews Carousel
- Star rating display
- Quote text + reviewer name + time ago
- Carousel/swipe enabled (via `js/swipe.js`)

---

## 5. Motion & Animations

### Transition Inventory (from CSS source)

```css
/* Nav links, cards, general UI */
transition: all 200ms cubic-bezier(0.645, 0.045, 0.355, 1);

/* Button shadow + letter-spacing */
transition: box-shadow 200ms ease, letter-spacing 200ms ease;

/* Nav link colour + box-shadow */
transition: color 200ms cubic-bezier(0.645, 0.045, 0.355, 1), box-shadow 200ms ease;

/* Button complex: shadow + letter-spacing + radius */
transition: box-shadow 200ms cubic-bezier(0.455, 0.030, 0.515, 0.955),
            letter-spacing 300ms ease,
            border-radius 200ms ease;

/* Opacity fades (modals, overlays) */
transition: opacity 300ms ease-in-out;

/* Background colour */
transition: background-color 200ms ease;

/* General */
transition: all 0.3s;

/* Card transform */
transition: transform ease 0.4s;

/* Card combined */
transition: box-shadow 300ms ease, background-color 300ms ease, transform 200ms ease;
```

### Key Patterns
- **Duration:** Almost exclusively `200ms` for micro-interactions; `300ms` for card/hover; `400ms` for transform
- **Primary easing:** `ease` (simple) for most; `cubic-bezier(0.645, 0.045, 0.355, 1)` for text/nav (this is the standard "ease-in-out" cubic — feels smooth and professional)
- **Button hover:** `box-shadow` intensifies + `letter-spacing` subtly reduces (200ms) — unique to Escola
- **Card hover:** scale(1.02) + deep shadow + bg colour (300ms ease)
- **Modal open:** opacity 0 → 1 (300ms ease-in-out), flex display toggle via JS
- **Nav dropdown:** JS-driven accordion on mobile; CSS transition on desktop

### Scroll-triggered animations
- No `data-aos` or `data-animate` attributes detected in current markup
- Page uses jQuery + Webflow interactions for any scroll triggers
- Recommended pattern for replicas: `IntersectionObserver` with `opacity + translateY(24px)` → `opacity: 1 + translateY(0)` at 500ms

### Parallax / Sticky
- Navbar is `position: fixed` — sticky throughout scroll
- No evidence of parallax backgrounds

---

## 6. Icon & Illustration Style

### Icons
- **Library:** Font Awesome Pro 6.5.1 (self-hosted)
- **Usage:** `<i class="fa-...">` or `<span class="fa-...">` inline
- **Product icons:** Custom SVGs per product, served as `<img src="/images/[Product].svg">`
- **Size pattern:** Social icons `10vw` (max 48px); footer button icons `1.3vw` (max 18px)
- **Arrow icons:** Custom SVG at `assets/arrow-left.svg`, used in dropdown indicators

### Illustration / Graphics Style
- SVG-based, flat design — no 3D or isometric illustrations
- Product icons use product accent colour fills (Schulmanager = #FF8483, etc.)
- App screenshots appear as device mockups (implied by app microsite section)
- "Swiss made software" badge in footer

---

## 7. Responsive Behaviour

### Breakpoints

| px | Direction | Layout change |
|----|-----------|---------------|
| `443px` | max | Calendly modal height 100vh |
| `667px` | max | Mobile modal adjustments |
| `991px` | max | Desktop nav hidden; mobile accordion; `.white_section` hidden; footer buttons full-width |
| `992px` | min | Desktop modal max-width 766px |
| `1440px` | min | Title/footer button font sizes switch from `vw` to fixed `px` |

### Key Layout Shifts
- **Navigation (≤ 991px):** Desktop dropdown links hidden; mobile accordion with `.has-drop-down` toggling `.accordion`; hamburger icon visible
- **Product grid:** Collapses from multi-column to single column
- **Footer buttons:** `width: 20vw` on desktop → `width: 100%` approach on mobile
- **Modal form grid:** `49% 49%` two columns → `unset` single column on mobile
- **Footer row ordering:** `.third_row_js .icons` becomes `justify-content: space-between; width: 100%`

### Touch Targets
- Buttons: minimum 40px height (`register-btn` = 40px exactly)
- Nav links: 80px height container for 30px vertical padding each side
- Footer button: `9.5px 0` padding (roughly 38px+ with content)

---

## 8. Page Structure — digitale-verwaltung

Sections observed (top → bottom):
1. **Navbar** (fixed, white)
2. **Hero** — Blue headline, subheadline, 2 CTA buttons
3. **Product feature section** — 6 product cards in grid
4. **Content/text section** — Alternating image + text blocks per product feature
5. **Testimonial / quote section** — Customer quotes
6. **CTA section** — "Wir beraten Sie gerne!" with 3 action buttons
7. **Footer** — Blue, multi-column

---

## 9. Page Structure — zurich-event.php (Escola App event page)

Sections (top → bottom):
1. **Navbar** (fixed, white)
2. **Hero** — "Jetzt die Escola App kennenlernen!" headline + city announcement copy
3. **App Store Reviews carousel** — 3 displayed, star ratings
4. **Event Details block** — Wann / Wo / Zeitplan / Gäste
5. **Das erwartet Sie** — 5 feature points (Einblicke, Praxisbeispiele, Erfahrungsberichte, Team, Netzwerken)
6. **Alternative attendance options** — 3 cards (Online, Visit, Try it)
7. **More Reviews** — Additional App Store quotes
8. **Registration section** — CTA button "Zur Anmeldung"
9. **CTA strip** — "Wir beraten Sie gerne!" with 3 modals
10. **Footer** — Blue, multi-column

---

## 10. Design Philosophy Summary

- **Clean, trustworthy, Swiss professional** — generous whitespace, constrained typography, no aggressive gradients
- **Blue as the single anchor colour** — all interactive and brand moments use #0083DB
- **Product colours as the supporting palette** — never used for structural UI, only for product identity
- **Centered-text sections** feel editorial; left-aligned modals/forms feel functional
- **Shadows communicate elevation**, not decoration — deeper on cards, lighter on nav
- **Motion is subtle and purposeful** — 200ms ease for all micro-interactions, nothing flashy
- **Self-hosted fonts** signal brand maturity; Gotham Rounded adds a premium rounded feel to headings
