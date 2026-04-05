# Website Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rewrite all 4 pages of theai101.shop with Tailwind CSS, unified branding, and professional design patterns.

**Architecture:** Static HTML pages with Tailwind CSS v4 via CDN, DM Sans font, Lucide SVG icons. No build step. Each page is self-contained with shared nav/footer markup inlined. Vanilla JS for interactivity.

**Tech Stack:** HTML5, Tailwind CSS (CDN), DM Sans (Google Fonts), Lucide Icons (inline SVG), Vanilla JS

**Spec:** `docs/superpowers/specs/2026-04-05-website-redesign-design.md`

---

## Task 1: Landing Page (index.html) -- Full Rewrite

**Files:**
- Rewrite: `index.html`

**Context:** This is the main marketing page. Preserve all existing content (capabilities, features, testimonials, pricing tiers, process steps, deploy options, AI options, FAQ) but rewrite with Tailwind CSS classes, DM Sans font, Lucide icons, and the design system from the spec. Fix all broken HTML and garbled copy.

**Key content to preserve:**
- Hero: "Your AI Agent, Deployed in 48 Hours" with "Book a Call" CTA
- Stats: 48h deploy, 100% uptime, $0 local cost, 50+ integrations
- 8 capability cards (Email, Calendar, Social, Code, Research, Docs, Support, Business Ops)
- Cloud vs Local deploy comparison cards
- Cloud AI vs Self-Hosted AI options section
- 4-step process (Discovery Call, Build, Security Audit, Go Live)
- 3 managed care tiers (Pro, Premium featured, Ultra) with pricing
- 3 testimonials (Alex R., Sarah K., third person)
- FAQ accordion
- Final CTA with email contact
- `BOOKING_URL` JS constant at top for CTA links

**Design system:**
- Background: `bg-[#0B1120]`
- Cards: `bg-gray-900 border border-slate-800 rounded-xl`
- Font: DM Sans via Google Fonts
- Accent: indigo-500 for CTAs and highlights
- Success: green-500 for checkmarks
- Nav: Fixed, floated, glassmorphic (`bg-slate-900/80 backdrop-blur-xl`)
- Footer: `bg-slate-950`, 4-column grid
- All icons: Lucide SVG (no emojis)
- Transitions: `duration-200`
- Reduced motion: `motion-reduce:transition-none`

- [ ] **Step 1:** Write complete `index.html` with all sections using Tailwind CSS
- [ ] **Step 2:** Test in browser at all breakpoints (375px, 768px, 1024px, 1440px)
- [ ] **Step 3:** Commit

```bash
git add index.html
git commit -m "feat: rewrite landing page with Tailwind CSS and unified design system"
```

---

## Task 2: Cloud Page (cloud.html) -- Full Rewrite

**Files:**
- Rewrite: `cloud.html`

**Context:** Cloud-hosted VPS plans page. Preserve pricing data and billing toggle JS logic. Fix all broken HTML (unclosed tags, garbled copy, duplicate `?v=4?v=3` params).

**Key content to preserve:**
- Hero: "Your AI Agent in the Cloud"
- VPS pricing with billing toggle (Monthly/Yearly/2-Year)
- 3 tiers: Premium ($349.99/mo), Pro ($249.99/mo featured), Ultra ($549.99/mo)
- Feature checklists per tier with startup bonuses
- Billing toggle JS that shows/hides price spans
- Trust strip items
- Mobile menu open/close JS

**Design system:** Same as Task 1 (same nav, footer, color palette, typography).

**Additions beyond current page:**
- "What's Included" features grid (6 cards)
- FAQ accordion section (5-6 questions about cloud hosting)
- Final CTA section

- [ ] **Step 1:** Write complete `cloud.html` with Tailwind CSS, preserving pricing data and toggle logic
- [ ] **Step 2:** Verify billing toggle works correctly for all 3 periods
- [ ] **Step 3:** Commit

```bash
git add cloud.html
git commit -m "feat: rewrite cloud pricing page with Tailwind CSS and unified design"
```

---

## Task 3: Local Page (local.html) -- New Page

**Files:**
- Create: `local.html`

**Context:** New page for self-hosted/local AI agent option. Content derived from the "Self-Hosted (Local)" deploy card and "Self-Hosted AI" option card on the landing page.

**Content to include:**
- Hero: "Run Your AI Agent on Your Own Hardware" / "Full control, zero monthly fees. Own it forever."
- Trust strip: "No Vendor Lock-in" | "Your Data Stays Local" | "One-Time Setup"
- "What You Get" 2-column section: feature list + terminal/setup mockup
  - Features: Full agent deployment, all 300+ skills, dashboard access, documentation, lifetime updates, Mac Mini 64GB RAM/1TB SSD
- "How Local Works" 3-step process: Choose Hardware -> We Set It Up -> You Own It
- Local vs Cloud comparison table
- Pricing section (one-time setup fee card with "Book a Call" CTA)
- FAQ section (5-6 questions about local hosting, hardware, maintenance)
- Final CTA + Footer

**Design system:** Same as Tasks 1-2.

- [ ] **Step 1:** Write complete `local.html` with all sections
- [ ] **Step 2:** Test responsiveness
- [ ] **Step 3:** Commit

```bash
git add local.html
git commit -m "feat: add local hosting page with Tailwind CSS"
```

---

## Task 4: Dashboard Polish (dashboard.html)

**Files:**
- Modify: `dashboard.html`

**Context:** Polish only -- keep existing sidebar layout, page nav JS, stat cards, charts, tables. Add Tailwind CDN, swap font to DM Sans, fix CSS variable naming, unify accent colors.

**Changes:**
- Add Tailwind CDN script tag and DM Sans font link to `<head>`
- Rename `--purple-*` variables to semantic names (`--primary: #6366f1`, `--primary-hover: #818cf8`, etc.)
- Fix `--purple-primary: #22c55e` contradiction (green value in "purple" var) -> `--accent-green: #22c55e`
- Update `body` font-family to DM Sans
- Update sidebar header to use Nemoclaw crab logo + "Nemoclaw" text
- Ensure mobile sidebar toggle works
- Keep ALL existing JS functionality untouched

- [ ] **Step 1:** Add Tailwind CDN + DM Sans, rename CSS variables, fix color contradictions
- [ ] **Step 2:** Verify all dashboard pages still work (nav, charts, tables)
- [ ] **Step 3:** Commit

```bash
git add dashboard.html
git commit -m "fix: polish dashboard with DM Sans font and unified color variables"
```

---

## Task 5: Supporting Files Update

**Files:**
- Modify: `site.webmanifest`
- Modify: `sitemap.xml`

**Changes:**

Update `site.webmanifest`:
```json
{
  "name": "The AI 101",
  "short_name": "AI 101",
  "icons": [
    { "src": "/logo-192.png", "sizes": "192x192", "type": "image/png", "purpose": "maskable" },
    { "src": "/logo-512.png", "sizes": "512x512", "type": "image/png", "purpose": "maskable" }
  ],
  "theme_color": "#6366F1",
  "background_color": "#0B1120",
  "display": "standalone"
}
```

Update `sitemap.xml` -- add `local.html`, update dates:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://theai101.shop/</loc><lastmod>2026-04-05</lastmod><priority>1.0</priority></url>
  <url><loc>https://theai101.shop/cloud.html</loc><lastmod>2026-04-05</lastmod><priority>0.9</priority></url>
  <url><loc>https://theai101.shop/local.html</loc><lastmod>2026-04-05</lastmod><priority>0.9</priority></url>
  <url><loc>https://theai101.shop/dashboard.html</loc><lastmod>2026-04-05</lastmod><priority>0.7</priority></url>
</urlset>
```

- [ ] **Step 1:** Update both files
- [ ] **Step 2:** Commit

```bash
git add site.webmanifest sitemap.xml
git commit -m "chore: update manifest branding and sitemap with all pages"
```
