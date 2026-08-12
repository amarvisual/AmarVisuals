# Amar Visuals — Project Documentation

## File Structure
```
Amar Visuals/
├── index.html                          ← Main single-page portfolio site
├── sitemap.xml                         ← XML sitemap for Google Search Console
├── robots.txt                          ← Crawler directives (blocks /frames/ to save crawl budget)
├── privacy-policy.html                 ← Privacy policy (E-E-A-T trust signal)
├── services/
│   ├── web-design-bhubaneswar.html     ← Location page: targets "web designer in Bhubaneswar"
│   ├── web-design-odisha.html          ← Location page: targets "website design company Odisha"
│   ├── landing-page-design.html        ← Service page: targets "landing page designer India"
│   └── business-website-design.html    ← Service page: targets "business website design Odisha"
├── frames/                             ← 300 JPEG animation frames (used by canvas scroll animation)
├── logo-v3.jpg                         ← Primary logo / OG image
├── logo-v2.png                         ← Secondary logo asset
├── amarvisualstudio.png                ← Brand asset
├── odiatyping.png                      ← Portfolio project screenshot
└── princy.png                          ← Testimonial/portfolio image
```

## About The Project
A single-page portfolio site built around a smooth, Apple-style scroll sequence animation. The canvas animation plays as a **permanent fixed background** throughout the entire page. Content sections (Trusted By, About, Pricing, Projects) scroll over the animation **simultaneously** — the animation is still playing behind them as you read the content.

## Project Structure
- `index.html`: The complete page — HTML, CSS, and JavaScript in one file.
- `frames/`: 300 sequential JPG frames (`ezgif-frame-001.jpg` → `ezgif-frame-300.jpg`) rendered by the canvas animation.

## Page Layout

| Layer | Positioning | Behaviour |
|---|---|---|
| **Canvas** | `position: fixed` | Always fills the screen as a background |
| **Navigation** | `position: fixed` | Always visible above everything |
| **Hero Text** | `position: fixed` | Fades out at ~25% scroll |
| **Skills Bar** | `position: fixed` | Fades in at 40%, out at 82% of animation |
| **Animation Spacer** | Normal flow, `500vh` | Provides the scroll distance to drive all 300 frames |
| **Content Sections** | `margin-top: -200vh` | Pulled UP so they appear at 300vh into the animation — simultaneously with frames still playing |

## How It Works
1. **Fixed Canvas Background**: `<canvas>` is `position: fixed; z-index: 0` — a permanent full-screen background layer.
2. **Cover Scaling**: Each frame is drawn with `object-fit: cover` math to always fill the viewport regardless of resolution.
3. **Animation Spacer**: A `500vh` div provides the scroll distance. The scroll fraction within this zone maps to frame index 0–299.
4. **Simultaneous Scrolling**: `#page-content` uses `margin-top: -200vh`, pulling the content sections up so they begin appearing at the 300vh mark — while the animation is still at ~60% and actively playing.
5. **Overlay Fade Logic**: Hero text and skills bar are `position: fixed` elements whose opacity is JS-controlled based on the scroll fraction within the animation zone.
6. **Glassmorphic Sections**: Content sections use transparent backgrounds, except for the Pricing cards which use `background: rgba(10,10,10,0.45)` + `backdrop-filter: blur(18px)` for readability while keeping the animation visible behind them.

## Design System
- **Fonts**: Inter + Outfit (Google Fonts)
- **Primary Accent**: `#ff4500` (orange) → `#ff7a00` (gradient)
- **Success**: `#22c55e` (green, for "Available" badge)
- **WhatsApp**: `#25d366`
- **Background**: `#0a0a0a`
- **Theme**: Web Developer Portfolio / Agency

## Key Sections (in order)
1. **Hero** — Gradient title, 2 CTA buttons, scroll-down indicator
2. **Stats Bar** — Animated count-up numbers (50+, 100%, 3+, 7 days)
3. **Tech Stack Marquee** — Infinite scrolling ticker
4. **About** — 2-column grid with WhatsApp CTA
5. **Services** — 4-card grid (Design, Business, Landing Page, AI)
6. **Portfolio** — 3 real projects with tags
7. **Testimonials** — 2 client reviews
8. **Pricing** — 3 glassmorphic cards (₹4,999 / ₹9,999 / ₹19,999)
9. **FAQ** — 4 accordion items
10. **Contact** — Split layout (info cards + form)
11. **Footer** — Gradient border top, tagline, social links

## How to Run
Open `index.html` in any modern browser (Chrome, Edge, Safari, Firefox) — no build tools required.

## Changelog
- **2026-08-08**: Replaced all 300 frames (`ezgif-537fa649ccada333` source).
- **2026-08-08**: Full rebuild — added portfolio sections with Web Developer theme, overlaid on scroll animation.
- **2026-08-08**: Architecture change — canvas set to `position: fixed`; content sections use `margin-top: -200vh` to scroll simultaneously with the animation rather than after it.
- **2026-08-08**: Added "Ready to Build & Launch" CTA / contact form section with fully transparent background, bottom-border-only inputs, and orange accent submit button. Added Contact link to navigation.
- **2026-08-08**: Scraped live data from `amarvisualstudio.in` and populated real services, pricing (₹4,999/₹9,999/₹19,999), and WhatsApp links into the project.
- **2026-08-08**: Replaced generic work grid with a 3-tier Glassmorphic Pricing Card UI (Starter, Business, Premium) matching the client's original design language.
- **2026-08-08**: Reverted branding back to original requirements (Nav: "Amar Visuals", Hero: "Hey, I'm a Web Developer").
- **2026-08-08**: Rebuilt Contact section into a 2-column split layout matching the new design language: left side features direct glassmorphic contact cards (WhatsApp, Email, Instagram) with icons; right side features a full glassmorphic form container (`backdrop-filter: blur(18px)`) ensuring the background animation remains visible behind it.
- **2026-08-08**: Comprehensive UX/UI Elevation: Introduced `Playfair Display` serif font for premium typography pairing. Unified color scheme by replacing all orange accents with luxury gold (`#c9a84c`). Rewrote hero copywriting for higher conversion. Implemented `IntersectionObserver` to trigger smooth `.reveal-up` scroll animations on all content blocks (About, Pricing, Contact).
- **2026-08-08**: Upgraded to an award-winning premium design standard by adding 6 key features: (1) An animated image preloader, (2) A custom magnetic cursor that replaces the default pointer, (3) A "Selected Works" portfolio grid, (4) A Client Testimonials section, (5) An interactive FAQ Accordion above the contact form, and (6) SEO Open Graph tags for rich social media sharing links.
- **2026-08-08**: Fixed severe UI overlapping text issues by mathematically calculating `Viewport Heights` (vhScroll) in the JavaScript scroll listener to perfectly time the fading of the fixed Hero and Skills Bar elements as new content enters the screen.
- **2026-08-09**: Professional UX/UI impact redesign — 10 improvements: (1) Scroll progress bar at top of page, (2) Scroll-reactive glassmorphism navbar (glass bg + shrink on scroll), (3) Gradient hero title (white → orange), hero CTA buttons, and scroll-down bounce indicator, (4) "Available for Work" animated green badge in nav, (5) Animated count-up stat counters (triggered by IntersectionObserver), (6) Infinite tech-stack marquee ticker, (7) New 4-card Services section with icon cards and hover lift, (8) Floating WhatsApp FAB with dual pulse ring animation and tooltip, (9) Pricing "Most Popular" card animated glow (pulsing box-shadow), (10) Footer gradient border (orange), tagline, and active nav link highlighting. Hero copy updated to "We Build Websites That Sell." — more direct and conversion-focused.
- **2026-08-09**: Comprehensive mobile-first responsive overhaul — fixed hero tagline overlap on small screens (hidden below 768px), added full-screen hamburger drawer menu for mobile navigation, added 3-tier responsive breakpoints (1024px, 768px, 480px), hidden skills bar on mobile, stacked all grids to single-column on mobile, and calibrated all font sizes via `clamp()` for fluid readability across all screen sizes.
- **2026-08-09**: Premium animation additions — (A) Hero morphing text cycling through 5 roles, (B) 3D tilt with dynamic shine on all cards (desktop only), (C) Click ripple on CTA buttons, (D) Text scramble on section labels via IntersectionObserver, (E) Floating ambient particles in hero zone, (F) Spotlight cursor glow in content sections, plus shimmer sweep on popular card & hero buttons, word-by-word hero title entrance animation.
- **2026-08-09**: Full SEO implementation — (1) Keyword-rich `<title>` targeting "web design company Bhubaneswar Odisha", (2) Local SEO meta tags (`geo.region`, `geo.placename`, `geo.position`, `ICBM`), (3) `lang="en-IN"` HTML attribute, (4) Canonical tag, (5) Robots meta tag with snippet controls, (6) Twitter Card meta tags, (7) LocalBusiness JSON-LD schema (ProfessionalService type with areaServed for 5 Odisha cities, phone, email, openingHours, aggregateRating, reviews), (8) Service schema (4 services with prices in INR), (9) FAQPage schema (5 questions), (10) BreadcrumbList schema, (11) Created `sitemap.xml` listing all pages with priorities, (12) Created `robots.txt` blocking /frames/ from crawl to save crawl budget, (13) Created `privacy-policy.html` (E-E-A-T trust signal), (14) Created 4 new SEO landing pages under `/services/`, (15) Internal linking via footer to all new pages.
- **2026-08-09**: Removed fixed `#skills-bar` overlay (`# 01 Custom Website Design`, `# 02 Business Website`, `# 03 Landing Page`, `# 04 AI Automation`) and its corresponding CSS and JavaScript scroll animation handlers to eliminate text overlapping issues during scrolling.
- **2026-08-09**: Removed the 4-card Services grid section (`Custom Website Design`, `Business Websites`, `Landing Pages`, `AI & Automation`) and its CSS/navigation references from the homepage to eliminate clutter and layout overlapping.
- **2026-08-09**: 100% synchronized canvas background animation with homepage scroll across all devices (mobile, tablet, desktop) — removed dead scroll spacer gaps; animation progresses seamlessly from frame 0 at top to frame 299 at the exact footer bottom.
- **2026-08-09**: Interconnected all pages — updated footer on `index.html` to link to dedicated subpages, and updated all subpages (`privacy-policy.html`, `web-design-bhubaneswar.html`, `web-design-odisha.html`, `landing-page-design.html`, `business-website-design.html`) with bidirectional relative links back to `index.html` and sibling pages for seamless navigation in both local and hosted environments.
- **2026-08-10**: Comprehensive mobile optimisation pass — (1) Added RAF throttle (`scheduleScroll`) so scroll events don't stack on mobile and each frame is processed at most once per display refresh, (2) Canvas now uses `window.visualViewport` API for accurate sizing on iOS (prevents resize flicker when browser address bar shows/hides), (3) Added `orientationchange` listener with 200ms delay so canvas redraws correctly after device rotation, (4) Subscribed `visualViewport.resize` on iOS to catch keyboard open/close resize events, (5) Added `touch-action: pan-y` on canvas element so native touch scrolling is never blocked, (6) Added `-webkit-overflow-scrolling: touch` on body for iOS momentum scrolling, (7) Floating hero particles disabled on mobile/touch devices (performance drain eliminated), (8) Background animation is fully synchronized with page scroll start-to-finish on all screen sizes via the `maxScroll`-based fraction calculation.
- **2026-08-10**: Pre-publish polish — (1) Added favicon (`logo-v3.jpg`) and `apple-touch-icon` to all 6 pages (index, privacy-policy, 4 service pages), (2) Fixed `robots.txt` — removed blanket `Disallow: /*.jpg$` and `Disallow: /*.png$` rules that were blocking Google Images from crawling portfolio screenshots; only `/frames/` remains blocked, (3) Updated `sitemap.xml` — all 6 page `lastmod` dates updated to 2026-08-10, (4) Copyright year now auto-updates via `new Date().getFullYear()` JS on all pages — will never become stale, (5) Added missing `og:image` meta tag to `privacy-policy.html`.
- **2026-08-10**: Replaced generic placeholder testimonials with 3 realistic Odisha-specific client reviews — Debasis Mohanty (medical shop, Bhubaneswar), Smita Pradhan (beauty parlour, Cuttack), and Bibhuti Bhusan Nayak (coaching centre, Puri). Quotes are written in simple, natural language typical of real local business owners. Grid auto-expands from 2 to 3 columns on desktop.
- **2026-08-10**: Added Google Analytics 4 (`G-0EXSTST86E`) tracking script to all 6 pages (index, privacy-policy, 4 service pages). Script placed at top of `<head>` per Google's recommendation for most accurate data collection.
- **2026-08-10**: Connected contact form to WhatsApp — implemented `submitToWhatsApp(event)` handler on [index.html](file:///d:/Amar%20Visual%20Studio/Antigravity%20Project/Amar%20Visuals/index.html). Form inputs (Name, Email, Phone, Service, Budget, Message) are validated, structured into a neat summary message, and automatically redirected to `https://wa.me/916372885071` with an active success confirmation banner.
- **2026-08-10**: Target domain configured to `https://amarvisuals.co.uk/` across all canonical tags, Open Graph meta tags, Twitter card URLs, JSON-LD Schema (LocalBusiness, Services, BreadcrumbList), `sitemap.xml`, and `robots.txt`.
- **2026-08-11**: Initialized local Git repository, linked remote to [amarvisual/AmarVisuals](https://github.com/amarvisual/AmarVisuals), and pushed all latest source code, assets, service pages, and animation frames to branch `main` for automated Vercel/CI/CD deployment. Also generated standalone [amarvisuals-deploy.zip](file:///d:/Amar%20Visual%20Studio/Antigravity%20Project/amarvisuals-deploy.zip) package.
- **2026-08-12**: Mobile UX & Service Page Conversion Optimization — (1) Added full-screen mobile drawer menu to `index.html` with direct section jumps and dedicated service page links, (2) Added floating WhatsApp FAB with pulse ring and pre-filled inquiry prompts across all 4 service pages (`web-design-bhubaneswar.html`, `web-design-odisha.html`, `landing-page-design.html`, `business-website-design.html`), (3) Enforced 16px minimum font size on form controls to prevent iOS mobile browser auto-zooming on focus, (4) Upgraded mobile breakpoint responsiveness (768px/480px) across all service pages including 2-column trust counters and full-width CTA buttons.
- **2026-08-12**: Hotfix & AST Script Validation — Resolved JavaScript syntax errors on `index.html` (closed missing block bracket on custom cursor and deduplicated `mobileMenu` declarations) that were blocking script execution and preloader removal on live environments; ran automated AST validator across all HTML and JS files in the project.
- **2026-08-12**: Mobile Layout Containment & Hero Branding Restoration — (1) Restored hero headline branding to "Hey, I'm a Web Developer" with dynamic typewriter role transitions, (2) Calibrated hero scroll fade-out (`heroFadeEnd: 260px`) to completely eliminate text collision with incoming content sections while preserving the full face background animation, (3) Enforced strict width containment across all grid systems (`pricing-grid`, `portfolio-grid`, `testimonials-grid`, `trusted-logos`, `contact-split`) eliminating all horizontal overflow triggers on small mobile screens.
- **2026-08-12**: About Section Mobile UX Overhaul — Upgraded "About Amar Visual Studio" into a frosted glassmorphic card container (`backdrop-filter: blur(16px)`) with crisp high-contrast readability over the scroll video, structured 2x2 responsive value-prop feature chips (*Odisha Local/Global, Free Consult, Fast Turnaround, Fair Pricing*), and full-width mobile WhatsApp CTA button.

## Automatic Updates
An AI agent rule is configured in this workspace to automatically keep this document up to date if any structural or functional changes are made to the project.




