# REDESIGN BLUEPRINT — PT. Sinergi Investama Prakasa

> **File target:** `~/Projects/PT-SIP/index.html` (overwrite total)
> **Source assets:** `~/Projects/PT-SIP/assets/`
> **Deploy:** GitHub Pages → `https://aslansyuaib-cyber.github.io/sinergi-investama-prakasa/`
> **Stack:** Vanilla HTML/CSS/JS + GSAP + ScrollTrigger (CDN)

---

## 🔴 NON-NEGOTIABLE RULES

1. **Only data from company profile.** No invented legal data, capacity, specs, or claims.
2. **Contact info MUST match profile slide 16.** Address, phone, email — exact.
3. **No emoji, no lucu-lucu.** Batubara harus terasa industrial, solid, credible.
4. **Semua asset real** — Unsplash photos untuk background, real SVG map, brand logo dari company profile.
5. **Responsive** — mobile, tablet, desktop semua work.
6. **Deploy ke GitHub Pages** (push ke master branch).

---

## 1. ARSITEKTUR HALAMAN

### Section Order (scroll journey flow)

```
[NAVIGATION — fixed top bar]
[HERO — section#hero]
  ├─ Left: tagline + hook + CTA
  └─ Right: Mini Cargo Inquiry Panel
[PROBLEM HOOK — section#problem]
[CARGO CONTROL MATRIX — section#matrix]
  ├─ 4 pillar cards (Quality/Quantity/Timeline/Settlement)
  └─ Deskripsi tiap pillar
[WHAT SIP COORDINATES — section#coordinates]
  ├─ Positioning statement
  └─ Core competencies grid
[KALIMANTAN SOURCING CORRIDOR — section#corridor]
  ├─ SVG Indonesia map + animated connection lines
  └─ Sourcing corridor narrative
[COAL AVAILABILITY CHECKER — section#coal-checker]
  ├─ Per-grade card (GAR 4200/4500/5000/5500/5800/6300/6500)
  └─ Tiap card punya "Check Availability" CTA
[FROM INQUIRY TO SETTLEMENT — section#journey]
  ├─ 8-step horizontal scroll journey
  └─ Buyer Need → Spec Review → Sourcing → Cargo Plan → QC → Loading → Docs → Settlement
[DOCUMENTATION & FOB-READY — section#docs]
  ├─ FOB terms explanation
  ├─ Document checklist
  └─ Seller vs Buyer responsibility split
[SUBMIT COAL REQUIREMENT FORM — section#form]
  ├─ Combobox fields (GAR, Quantity/month, Delivery Term, Destination, Target Laycan, Payment Structure)
  └─ Submit → Telegram notification
[CONTACT & COMPANY DETAILS — section#contact]
  ├─ Address, phone, email
  ├─ Map embed
  └─ Footer
[FLOATING CARDS — persistent overlay]
  ├─ 4 cards (GAR, Quantity, Laycan, Docs)
  └─ Keyboard-navigable (← → to focus, Enter to expand)
```

### Navigation Flow
- Fixed navbar, transparent → solid on scroll
- Menu items: About, Matrix, Coal, Journey, Contact
- Mobile: hamburger menu

---

## 2. TEKNIS IMPLEMENTASI

### 2.1 Color System

```css
--navy-900: #0a0e17;
--navy-800: #0f1a2e;
--navy-700: #1e2d4d;
--navy-600: #2a3f66;
--gold-400: #c8a84e;
--gold-300: #d4b86a;
--gold-200: #e5c76b;
--blue-400: #4a9eff;
--blue-300: #6bb5ff;
--steel-400: #3a5a8a;
--steel-300: #5a7aaa;
--text-primary: #e8e6e3;
--text-secondary: #9a9a9a;
--glass-bg: rgba(15, 26, 46, 0.6);
--glass-border: rgba(200, 168, 78, 0.15);
```

### 2.2 Typography

- Headings: `'Inter', system-ui, sans-serif` (Google Fonts)
- Body: `system-ui, -apple-system, sans-serif`
- Sizes: responsive clamp() throughout

### 2.3 Key Components

#### Hero (section#hero)
- Split layout (55% left, 45% right on desktop, stack on mobile)
- Left: H1 tagline, 2 paragraph hook, 2 CTA buttons (Contact Us, Submit Requirement)
- Right: Mini Cargo Inquiry Panel — form ringkas (GAR dropdown, Quantity input, email)
- Background: `hero-barge.jpg` with dark overlay gradient

#### Cargo Control Matrix (section#matrix)
- Bento grid — 4 pillar cards
- Tiap card: icon, title, short desc, expandable detail
- Hover: scale + glow effect

#### Coal Availability Checker (section#coal-checker)
- Grid of grade cards (3 cols desktop, 2 tablet, 1 mobile)
- Tiap card: Grade name, GAR spec, typical use, "Check Availability" button
- Background: `coal-river.jpg` parallax

#### From Inquiry to Settlement (section#journey)
- Horizontal scroll container (CSS snap scroll or GSAP horizontal)
- 8 step cards connected by timeline line
- Active step highlighted with gold

#### Submit Coal Requirement Form (section#form)
- Combobox fields: `<input>` + `<datalist>` for dropdown + manual input
- Fields:
  - Coal Grade (GAR): datalist [4200, 4500, 5000, 5500, 5800, 6300, 6500]
  - Quantity (MT/month): input number
  - Delivery Term: datalist [FOB, CIF, CNF, DES]
  - Destination: text input
  - Target Laycan: month picker
  - Payment Structure: datalist [L/C, T/T, L/C + T/T]
  - Name & Email: text input
- Submit → send to Telegram bot (bot token + chat ID diisi nanti)

#### Floating Cards
- Fixed position bottom-right (like sticky notes)
- 4 cards stacked with slight offset
- Keyboard navigation: ← → arrows to cycle focus, Enter to expand/collapse
- Cards: GAR, Quantity, Laycan, Docs
- Tiap card expanded: show mini detail with relevant CTA

### 2.4 Animations & Effects

- **GSAP + ScrollTrigger** (CDN)
  - Sections fade-in + slide-up on scroll
  - Parallax on background images
  - Stagger on card grids
  - Counter animation on stats
- **Scroll-triggered parallax:**
  - Coal texture overlay (subtle, CSS pseudo-element)
  - Barge silhouette (SVG, scroll-position driven)
  - Kalimantan map (map scrolls at different rate)

### 2.5 Assets

| File | Source | Usage |
|------|--------|-------|
| `assets/images/hero-barge.jpg` | Unsplash — 1920×1080 | Hero background, parallax layers |
| `assets/images/coal-river.jpg` | Unsplash — 1920×1080 | Coal Checker section bg |
| `assets/images/vessel-port.jpg` | Unsplash — 1920×1080 | Docs section bg |
| `assets/images/BRAND LOGO PT SIP.png` | Company profile | Navbar logo + hero |
| `assets/svg/indonesia-network.svg` | junwatu + custom overlay | Sourcing corridor section |
| `assets/svg/barge-silhouette.svg` | Custom | Parallax element |
| `assets/svg/vessel-silhouette.svg` | Custom | Parallax element |

### 2.6 External Libraries (CDN)

- GSAP: `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js`
- ScrollTrigger: `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js`
- Google Fonts (Inter): `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap`
- Telegram: native fetch API (no library needed)

---

## 3. FILE STRUCTURE

```
~/Projects/PT-SIP/
├── index.html              ← single-page landing (ALL code)
├── assets/
│   ├── images/
│   │   ├── hero-barge.jpg
│   │   ├── coal-river.jpg
│   │   ├── vessel-port.jpg
│   │   └── BRAND LOGO PT SIP.png
│   └── svg/
│       ├── indonesia-network.svg
│       ├── barge-silhouette.svg
│       └── vessel-silhouette.svg
├── .github/workflows/
│   └── deploy.yml          ← GitHub Actions deploy
├── PRD.md
├── copy-rewrite-proposal.md
├── blueprint.md             ← copy rewrite (existing)
└── redesign-blueprint.md    ← THIS FILE
```

**Semua kode di 1 file `index.html`** — embedded CSS + JS. No build step.

---

## 4. DEPLOYMENT

- Push ke `master` branch → GitHub Actions auto-deploy ke Pages
- URL: `https://aslansyuaib-cyber.github.io/sinergi-investama-prakasa/`

---

## 5. PENDING / PLACEHOLDER

- **Telegram bot token & chat ID** — diisi manual setelah deploy. Placeholder: `__TOKEN__` dan `__CHAT_ID__`
- **Unsplash photos** — sudah di-download, path fixed
- **Barge/vessel SVG** — simplified path dari custom draw (bisa disempurnakan nanti)

---

## 6. ESTIMASI EKSEKUSI

| Fase | Konten | Estimasi |
|------|--------|----------|
| 1 | Hero + Navigation + Form panel | ~400 baris |
| 2 | Problem + Matrix + SIP Coordinates | ~300 baris |
| 3 | Corridor (map) + Coal Checker | ~300 baris |
| 4 | Journey + Docs + Form + Contact | ~400 baris |
| 5 | Floating cards + Animations | ~200 baris |
| 6 | Responsive + Polish | ~200 baris |
| **Total** | | **~1,800-2,000 baris** |

---

## 7. EXECUTION FLOW (kanban task)

1. Setup HTML skeleton + CSS vars + Google Fonts
2. Section 1: Navbar + Hero + Mini Inquiry Panel
3. Section 2: Problem Hook + Matrix + Coordinates
4. Section 3: Kalimantan Corridor (SVG map embed) + Coal Checker
5. Section 4: Scroll Journey + Docs + Form + Contact/Footer
6. Section 5: Floating cards (keyboard nav)
7. Section 6: GSAP + ScrollTrigger animations
8. Section 7: Responsive CSS (mobile/tablet/desktop)
9. Deploy to GitHub Pages
