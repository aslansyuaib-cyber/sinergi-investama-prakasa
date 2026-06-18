# BLUEPRINT — PT. Sinergi Investama Prakasa
## Technical Implementation Guide

**Versi:** 1.0  
**Based on:** PRD v1.0  
**Stack:** Vanilla HTML/CSS/JS + GSAP

---

## 1. Folder Structure (Final)

```
PT-SIP/
├── index.html             # Single page landing
├── prd.md                 # Product Requirements Doc
├── blueprint.md           # ← this file
├── assets/
│   └── images/            # Logo, branding, optimised images
│   └── video/             # Hero background video
├── css/
│   ├── main.css           # Global styles + variables
│   ├── hero.css           # Hero section
│   ├── bento.css          # Bento grid layouts
│   ├── glass.css          # Glassmorphism components
│   └── form.css           # Contact form styles
├── js/
│   ├── main.js            # Init + DOM ready
│   ├── hero.js            # Video + parallax hero
│   ├── animations.js      # GSAP ScrollTrigger configs
│   ├── bento.js           # Bento grid layout logic
│   ├── form.js            # Form handler + validation
│   └── counter.js         # Stat counter animation
├── data/
│   └── leads.json         # Submitted form data (local)
├── sections/              # Per-section partials (for dev)
└── components/            # Reusable UI components
```

---

## 2. Component Tree

```
BODY
├── NAVBAR (glassmorphism, sticky)
│   ├── Logo
│   ├── Nav links (scroll-to)
│   └── CTA button
│
├── SECTION #hero
│   ├── Video background (MP4 + poster)
│   ├── Gradient overlay (navy → transparent)
│   ├── Headline + subheadline
│   ├── CTA button (→ #contact-form)
│   └── Scroll indicator (animated chevron)
│
├── SECTION #snapshot
│   ├── Bento grid header
│   └── Cards (AHU, NIB, NPWP, Lokasi, dll)
│
├── SECTION #about
│   ├── Split layout (text + image)
│   ├── Parallax background layer
│   └── Company description
│
├── SECTION #vision-mission
│   ├── Section header (gold accent)
│   └── Floating cards (staggered)
│       ├── Visi card
│       └── Misi list (5 items)
│
├── SECTION #products
│   ├── Bento grid header
│   ├── Coal grade table (stylized)
│   └── Grade cards (floating)
│
├── SECTION #operations
│   ├── Horizontal timeline
│   └── Scroll-snap cards
│
├── SECTION #why-us
│   ├── 4 pillar cards (Quality, Quantity, Timeline, Settlement)
│   └── Floating + glow on hover
│
├── SECTION #contact
│   ├── Glassmorphism card
│   ├── Form fields (name, phone, email, comment)
│   ├── Submit button
│   ├── Company address + contact
│   └── Map placeholder
│
└── FOOTER
    ├── Logo
    ├── Quick links
    ├── Contact info
    └── Copyright
```

---

## 3. Animation Blueprint (GSAP + ScrollTrigger)

### 3.1 Hero
```
Trigger: #hero
Effect: 
  - Video scale in (1.1 → 1) on load
  - Text fade-up staggered (0.3s apart)
  - Parallax: overlay moves slower on scroll
```

### 3.2 Snapshot Bento
```
Trigger: #snapshot
Effect:
  - Cards stagger in from bottom (0.15s delay each)
  - Hover: lift +5px + gold border glow
```

### 3.3 About Split
```
Trigger: #about
Effect:
  - Text slides in from left
  - Image parallax (slight movement)
```

### 3.4 Vision Misi
```
Trigger: #vision-mission
Effect:
  - Cards float in from random directions
  - Stagger 0.2s
  - Persistent subtle float animation (idle)
```

### 3.5 Products Table
```
Trigger: #products
Effect:
  - Rows fade in sequentially
  - Highlight row on hover
```

### 3.6 Timeline
```
Trigger: #operations
Effect:
  - Horizontal scroll snap
  - Cards appear as they enter viewport
```

### 3.7 Why Us Cards
```
Trigger: #why-us
Effect:
  - Cards flip/scale in staggered
  - Glow border on hover
```

### 3.8 Contact
```
Trigger: #contact
Effect:
  - Glass card fades up
  - Form fields slide in from bottom (staggered)
```

---

## 4. Breakpoints

| Device | Width | Notes |
|--------|-------|-------|
| Mobile | < 640px | Single column, stacked sections |
| Tablet | 640–1024px | 2-column bento |
| Desktop | > 1024px | Full bento grid + parallax |

---

## 5. Dependencies

| Library | Version | CDN |
|---------|---------|-----|
| GSAP | 3.12+ | `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js` |
| ScrollTrigger | 3.12+ | `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js` |
| (opsional) Lenis | 1.x | Hanya fallback kalo GSAP bermasalah |

---

## 6. Data Flow — Form

```
User input → validate (JS) → 
  ├─ success → simpan ke localStorage + JSON
  └─ notify via Hermes → Telegram
```

### Lead Data Format
```json
{
  "id": "SIP-20260618-001",
  "name": "",
  "phone": "",
  "email": "",
  "message": "",
  "timestamp": "2026-06-18T21:00:00Z"
}
```

---

## 7. Deployment

| Opsi | Command | Catatan |
|------|---------|---------|
| GitHub Pages | Push ke repo → enable Pages | Gratis |
| Netlify | Drag folder / CLI | Auto HTTPS |
| Vercel | `vercel` CLI | Gratis |

Rekomendasi: **GitHub Pages** — paling simpel, ga perlu config.
