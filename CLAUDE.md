# CLAUDE.md — Nebur Logistics Website

> This file is the single source of truth for Claude Code when building, iterating, and maintaining the Nebur website.
> Read this file fully before writing any code, creating any file, or making any structural decision.

---

## Project Overview

| Field | Value |
|---|---|
| **Company** | Nebur Logistics |
| **Tagline** | Fast. Reliable. Delivered. |
| **Type** | Multi-page marketing website |
| **Market** | Nigeria (initial), pan-African expansion planned |
| **Inspiration** | EVRI-style last-mile parcel logistics |
| **Stack** | Static HTML files with shared CSS in `assets/styles.css`, page-specific CSS inline per HTML file, and vanilla JavaScript — no build step required |
| **Fonts** | Inter (loaded via Google Fonts CDN) |
| **Hosting** | Netlify (static deploy from `main` branch) |
| **Repository** | Git with structured Git Flow branching strategy |

---

## Mission

Build a clean, fast, professional multi-page marketing website for Nebur — a Nigerian logistics company offering parcel delivery, last-mile solutions, and e-commerce fulfilment services. Every page must convey **trust, speed, and reliability** while loading quickly on lower-end Android devices and variable mobile network speeds common across Nigeria.

---

## Site Architecture — Pages

The website consists of four HTML pages. Every page shares the same `<header>`, `<footer>`, and global CSS/JS (embedded inline per file — no separate linked files needed).

### `index.html` — Homepage
The primary marketing and conversion page. Full-featured, highest visual impact.

**Sections (in order):**
1. `<header>` — Sticky nav with mobile hamburger menu
2. `#hero` — Full-viewport hero: bold headline, sub-headline, dual CTAs
3. `#stats` — Animated trust counters (parcels delivered, states covered, on-time rate)
4. `#services-preview` — 4 service cards, each linking to `services.html`
5. `#how-it-works` — 3-step numbered process (horizontal desktop / vertical mobile)
6. `#coverage` — Static SVG map of Nigeria with coverage zone highlights
7. `#why-nebur` — 6 differentiator blocks with icons
8. `#testimonials` — 3 customer testimonial cards
9. `#cta-banner` — Full-width conversion banner
10. `<footer>` — Links, contact info, social icons, app download placeholder

---

### `services.html` — Services (Detailed)
Dedicated page for all Nebur service offerings with full descriptions.

**Sections (in order):**
1. `<header>` — Same sticky nav as all pages
2. `#services-hero` — Page hero: "What We Deliver" headline + short intro paragraph
3. `#services-list` — Full service breakdown, one section per service:
   - **Last-Mile Delivery** — Door-to-door parcel delivery across Nigerian states
   - **Parcel Pickup & Drop-off** — Scheduled collections from home or business
   - **Express Delivery** — Same-day delivery within Lagos, Abuja, Port Harcourt
   - **Business Logistics (B2B)** — Bulk shipment solutions and B2B freight forwarding
   - **E-commerce Fulfilment** — Warehousing + dispatch for online sellers
   - **Cash-on-Delivery (COD)** — Payment collected at delivery, transferred to sender
4. `#pricing-note` — "Get a custom quote" section with CTA to `contact.html`
5. `#services-faq` — 5–6 common questions (accordion component, vanilla JS)
6. `<footer>` — Same footer as all pages

---

### `about.html` — About
Humanises the brand. Tells the Nebur story, introduces the founders, and communicates values.

**Sections (in order):**
1. `<header>` — Same sticky nav
2. `#about-hero` — Page hero: "We're Redefining Logistics in Nigeria"
3. `#our-story` — 2–3 paragraphs on how Nebur started, the problem it solves, and the vision
4. `#timeline` — Visual timeline (CSS-only, vertical line with milestone nodes):
   - 2023 — Company founded
   - 2024 — First 1,000 deliveries; Lagos operations live
   - 2024 — Abuja hub opened
   - 2025 — Express same-day service launched
   - 2026 — Pan-African expansion planning begins
5. `#founders` — Founder cards (name, role, short bio, optional LinkedIn link)
6. `#values` — 4 core value cards (Reliability, Speed, Transparency, Community)
7. `#team` — Optional: small team photo grid with names and roles
8. `#cta-banner` — "Ship with a team that cares" banner linking to `contact.html`
9. `<footer>` — Same footer

---

### `contact.html` — Contact
Conversion and communication page. Primary destination for all "Get a Quote" and "Contact Us" CTAs.

**Sections (in order):**
1. `<header>` — Same sticky nav
2. `#contact-hero` — Page hero: "Let's Talk Logistics" + short reassuring subtext
3. `#contact-form` — Quote / enquiry form (Netlify Forms integration)
4. `#founder-section` — Founder direct contact block (name, photo, email, WhatsApp link) — personal and trustworthy
5. `#offices` — Office address cards: Lagos HQ, Abuja Hub (styled address blocks)
6. `#contact-social` — Social media links: Instagram, X/Twitter, WhatsApp Business, LinkedIn
7. `<footer>` — Same footer

---

## Shared Navigation (All Pages)

The `<header>` must be identical across all four pages. The active page's nav link should carry `class="active"` and `aria-current="page"`.

```
Logo (links to index.html)  |  Services  |  About  |  Contact  |  [Track Parcel — CTA button]
```

- Desktop: horizontal inline nav
- Mobile: hamburger icon → full-width slide-down menu (`aria-expanded` toggled by JS)
- Sticky on scroll with a subtle `box-shadow` after a scroll threshold
- "Track Parcel" renders as a filled amber button, not a plain nav link
- `href="#"` with `data-future="tracking"` on the Track Parcel button (links to app later)

---

## Shared Footer (All Pages)

```
[Logo + Tagline]   [Navigation]   [Contact]                      [Social]
                    Home           hello@neburlogistics.ng          Instagram
                    Services       +234 xxx xxx xxxx                X / Twitter
                    About          Lagos, Nigeria                   WhatsApp Business
                    Contact                                          LinkedIn

[Download Our App — Coming Soon]  [App Store badge placeholder] [Play Store badge placeholder]

© 2025 Nebur Logistics. All rights reserved.
```

---

## Design Philosophy & Visual Identity

### Colour Palette

All colours must be declared as CSS custom properties inside a `:root {}` block at the top of every page's `<style>` tag.

| Token | Hex | Usage |
|---|---|---|
| `--color-navy` | `#0B1F3A` | Primary dark background, nav, footer |
| `--color-amber` | `#F59E0B` | Accent, CTAs, highlights, hover states |
| `--color-amber-dark` | `#D97706` | CTA hover / active state |
| `--color-white` | `#FFFFFF` | Cards, light section backgrounds |
| `--color-off-white` | `#F9F8F6` | Alternating section backgrounds |
| `--color-text` | `#111827` | Body text |
| `--color-text-muted` | `#6B7280` | Subtext, captions, secondary copy |
| `--color-border` | `#E5E7EB` | Card borders, dividers |

### Typography

- **Font Family:** Inter (Google Fonts CDN) — clean, highly legible, excellent on mobile
- **Loading snippet** (in every page `<head>`, before `<style>`):

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

- **Scale using `clamp()` for fluid, responsive sizing:**

| Element | `clamp()` value | Weight |
|---|---|---|
| Display / Hero | `clamp(2.5rem, 6vw, 4.5rem)` | 800 |
| H1 | `clamp(2rem, 4vw, 3rem)` | 700 |
| H2 | `clamp(1.5rem, 3vw, 2.25rem)` | 700 |
| H3 | `clamp(1.125rem, 2vw, 1.5rem)` | 600 |
| Body | `1rem` / line-height `1.6` | 400 |
| Small / Caption | `0.875rem` | 400 |

- Large headings: `letter-spacing: -0.02em` for a premium, modern feel
- Body text max-width: `65ch` for comfortable reading line length

### Aesthetic Style

- **Character:** Modern Nigerian Tech Brand — professional and confident with warmth; never cold or corporate
- **Section rhythm:** Consistent `padding: clamp(4rem, 8vw, 7rem) 0` on every `<section>`
- **Background texture:** Subtle CSS dot-grid (`radial-gradient`) on the hero and dark CTA sections for depth — no image files
- **Animation:** Scroll-triggered CSS fade-ins driven by a single `IntersectionObserver` instance in vanilla JS. No GSAP, no external libraries
- **Icons:** Inline SVG only — no icon font libraries (eliminates extra HTTP requests)
- **Cards:** `border-radius: 12px`, `box-shadow: 0 2px 16px rgba(0,0,0,0.07)`, white background on off-white sections

---

## File & Folder Structure

```
nebur-website/
├── index.html            # Homepage
├── services.html         # Detailed services page
├── about.html            # About page (founders, story, timeline, values)
├── contact.html          # Contact page (form, founder section)
├── assets/
│   ├── styles.css        # Shared CSS (design tokens, reset, layout, nav, footer, animations)
│   ├── icons/            # SVG icon source files
│   ├── images/           # Optimised WebP images — max 100KB each
│   └── nebur-logo.svg    # Master SVG logo
├── .gitignore
├── netlify.toml          # Netlify config (redirects, cache headers, security)
└── CLAUDE.md             # This file
```

> **CSS architecture:** Shared styles (design tokens, reset, layout, buttons, nav, footer, animations, shared responsive breakpoints) live in `assets/styles.css`, which is linked from every HTML page's `<head>` after the Google Fonts link. Page-specific styles remain in each HTML file's inline `<style>` tag. JavaScript stays embedded inline per file. There are no other separate linked `.css` or `.js` files.

---

## Contact Form — Netlify Forms Integration

Use Netlify's built-in form handling on `contact.html`. No backend or serverless function required.

```html
<form name="nebur-contact" method="POST" data-netlify="true" netlify-honeypot="bot-field">
  <input type="hidden" name="form-name" value="nebur-contact" />
  <p hidden><input name="bot-field" /></p>  <!-- Honeypot spam trap -->

  <input type="text"   name="full_name"         placeholder="Full Name"                    required />
  <input type="email"  name="email"              placeholder="Email Address"                required />
  <input type="tel"    name="phone"              placeholder="Phone Number (+234...)"       />
  <select              name="service_type"       required>
    <option value="">What service do you need?</option>
    <option value="last_mile">Last-Mile Delivery</option>
    <option value="express">Express / Same-Day</option>
    <option value="b2b">Business Logistics (B2B)</option>
    <option value="ecommerce">E-commerce Fulfilment</option>
    <option value="cod">Cash-on-Delivery</option>
    <option value="other">Other / Not Sure</option>
  </select>
  <input type="text"   name="pickup_address"     placeholder="Pickup Location (City / State)"    />
  <input type="text"   name="delivery_address"   placeholder="Delivery Location (City / State)"  />
  <input type="text"   name="parcel_weight"      placeholder="Approximate Weight (kg)"            />
  <textarea            name="message"            placeholder="Any additional details..."></textarea>

  <button type="submit">Send Enquiry</button>
</form>
```

Field names use snake_case throughout (`pickup_address`, `delivery_address`, `parcel_weight`, `service_type`) to map cleanly to a future booking API without renaming.

---

## `netlify.toml` Configuration

```toml
[build]
  publish = "."

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"

[[redirects]]
  from = "/track"
  to = "/#"
  status = 302
```

---

## Git Repository & Git Flow

### Branching Strategy

```
main        ← Production. Auto-deploys to Netlify. Never commit directly.
develop     ← Integration branch. All features merge here first, tested before going to main.
feature/*   ← Feature branches, branched from develop.
fix/*       ← Bug fix branches, branched from develop.
hotfix/*    ← Emergency fixes branched directly from main, merged back to both main and develop.
```

### Branch Naming Convention

```
feature/homepage-hero
feature/services-page
feature/about-timeline
feature/contact-form-netlify
fix/mobile-nav-overflow
fix/footer-link-alignment
hotfix/contact-form-submission-error
```

### Day-to-Day Workflow

```bash
# 1. Start from an up-to-date develop branch
git checkout develop
git pull origin develop

# 2. Create a feature branch
git checkout -b feature/your-feature-name

# 3. Build, commit often with clear messages
git add .
git commit -m "feat: add hero section with animated stat counters"

# 4. Push the branch
git push origin feature/your-feature-name

# 5. Open a Pull Request → develop (review + preview deploy on Netlify)
# 6. Merge into develop once approved
# 7. When develop is stable and QA'd, open PR: develop → main to trigger production deploy
```

### Commit Message Convention (Conventional Commits)

```
feat:     New feature or page section     e.g. feat: add services FAQ accordion
fix:      Bug fix                         e.g. fix: correct mobile menu z-index overlap
style:    CSS/visual change, no logic     e.g. style: update CTA button hover colour
content:  Copy or text updates            e.g. content: update homepage hero headline
chore:    Config, tooling, repo work      e.g. chore: add netlify.toml security headers
docs:     Documentation only              e.g. docs: update CLAUDE.md Git Flow section
```

### `.gitignore`

```
.DS_Store
Thumbs.db
*.log
.env
.netlify/
node_modules/
```

### Initial Repository Setup Commands

```bash
git init
git checkout -b main
git add .
git commit -m "chore: initial project scaffold with CLAUDE.md and folder structure"
git branch develop
git checkout develop
# Push to GitHub and connect Netlify to deploy from main
```

---

## Technical Requirements

### Performance (Critical for Nigeria)

- **Target:** Page load < 3 seconds on 4G; usable on 3G
- All images: WebP format, max 100KB each
- Prefer inline SVG over `<img>` tags for icons and illustrations
- Use `IntersectionObserver` for scroll animations — no scroll libraries
- No external CSS frameworks (no Bootstrap, no Tailwind CDN, no Material)
- No jQuery or animation libraries
- Defer non-critical scripts with `defer` attribute

### Mobile-First Responsive Design

- Minimum supported viewport: 360px (common budget Android device)
- All heading sizes use `clamp()` — no fixed `px` sizes for type
- Tap targets: minimum 44×44px for all buttons and links
- Mobile-only: sticky bottom "Get a Quote" button bar (hidden on desktop with CSS)
- Touch-friendly accordion on services FAQ (tap to expand)
- Test at: 360px, 480px, 768px, 1024px, 1280px

### Accessibility

- WCAG 2.1 AA compliant throughout
- Semantic HTML5: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Every `<img>` and inline SVG: descriptive `alt` or `aria-label`
- `aria-current="page"` on active nav link per page
- `aria-expanded` on hamburger button, toggled by JS
- `:focus-visible` ring style on all interactive elements
- Minimum contrast ratios: 4.5:1 body text, 3:1 large headings

### SEO — Per Page

| Page | `<title>` | Meta Description |
|---|---|---|
| index.html | Nebur Logistics — Fast Parcel Delivery in Nigeria | Nebur delivers parcels fast and reliably across Nigeria. Same-day, next-day, and B2B logistics solutions. Get a quote today. |
| services.html | Our Services — Nebur Logistics | Last-mile delivery, express shipping, B2B freight, and e-commerce fulfilment across Nigeria. See how Nebur can serve you. |
| about.html | About Us — Nebur Logistics | Learn the story behind Nebur, meet our founders, and discover the values driving Nigeria's modern logistics company. |
| contact.html | Contact Nebur — Get a Quote or Send an Enquiry | Reach Nebur Logistics by form, phone, or WhatsApp. Get a personalised shipping quote within 24 hours. |

- OpenGraph tags on all pages: `og:title`, `og:description`, `og:image`, `og:url`
- `<link rel="canonical">` on each page
- JSON-LD `LocalBusiness` structured data schema on `index.html`

---

## Content Guidelines

### Voice & Tone

- **Confident but warm** — trusted Nigerian brand, not cold corporate
- **Active voice** — "We deliver your parcels" not "Parcels are delivered by us"
- **Direct and clear** — no jargon; Nigerian users value plain, honest communication
- **Local presence** — reference real cities and states (Lagos, Abuja, Port Harcourt, Kano, Ibadan) to signal genuine local credibility

### Key Brand Messages

1. **Speed** — "Same-day and next-day delivery across Nigeria"
2. **Reliability** — "Track every parcel, every step of the way"
3. **Accessibility** — "For individuals, online sellers, and businesses of all sizes"
4. **Trust** — "Thousands of parcels delivered safely"
5. **Technology** — "Smart logistics built for Nigeria"

### Consistent CTAs Across All Pages

| Intent | CTA Text |
|---|---|
| Primary conversion | "Get a Quote" or "Start Shipping" |
| Secondary / exploratory | "Learn More" or "See Our Services" |
| Direct contact | "Contact Us" or "Talk to Us" |
| Package tracking | "Track Your Parcel" |

---

## Future-Proofing Notes (For Claude Code App Development)

This website is Phase 1 of a larger platform. Build with the following in mind from day one:

- **Nav "Businesses" link** — placeholder now (`href="#"`, `data-future="b2b-portal"`) for the future B2B client portal
- **Track Parcel button** — `href="#"` with `data-future="tracking"` — will link to live tracking application
- **Footer app badges** — include styled placeholder slots for App Store and Google Play badges with a "Coming Soon" label
- **CSS custom properties** — all design tokens declared as `--variables` so the design system can be adopted by a future React/Next.js app without rework
- **Semantic section IDs** — use clean IDs (`#hero`, `#services`, `#contact-form`) that translate naturally to React routes
- **Form field naming** — all contact form fields in snake_case for clean future backend API mapping

---

## Constraints — What Claude Must NOT Do

- Do not use Bootstrap, Tailwind CDN, Material UI, or any external CSS framework
- Do not link separate `.css` or `.js` files beyond `assets/styles.css` — shared styles go in `assets/styles.css`, page-specific styles stay inline in each HTML file's `<style>` tag, scripts stay inline per file
- Do not use jQuery, GSAP, Anime.js, or any JS library beyond vanilla
- Do not write Lorem Ipsum placeholder copy — use real, Nebur-specific content on every section
- Do not use generic AI aesthetics (purple gradients, featureless flat cards)
- Do not add backend server code, databases, or Node.js — this is a fully static site
- Do not auto-play video anywhere — too data-heavy for Nigerian mobile connections
- Do not over-animate — every animation must serve a clear UX purpose
- Do not commit directly to `main` — always follow the feature branch → develop → main Git Flow

---

## Inspirational References

| Site | What to Learn From |
|---|---|
| evri.com | Clean logistics UX, clear service hierarchy, strong CTAs |
| sendbox.co | Nigerian startup, local tone, modern product-led design |
| dhl.com | Trust signals, professional standards, structured service pages |
| jumia.com.ng | Nigerian market UX, mobile-first design decisions |
| stripe.com | Bold typography-led sections, excellent scroll pacing |

---

## Revision Log

| Date | Change | Reason |
|---|---|---|
| 2025-03-06 | Initial CLAUDE.md created | Project kickoff — single-page version |
| 2025-03-06 | Revised to multi-page architecture | Product decision: 4 pages (index, services, about, contact) |
| 2025-03-06 | Updated stack: Inter font, embedded CSS/JS, Netlify hosting | Owner specifications applied |
| 2025-03-06 | Added Git Flow strategy and Conventional Commits convention | Proper version control from day one |
| 2026-03-09 | Extracted shared CSS into `assets/styles.css` | Eliminate ~400 lines of duplicated CSS across all 4 pages; standardise `.social-link` class in contact.html footer |

---

*Always read this file fully before writing any code or making any structural or design decision for the Nebur website.*
