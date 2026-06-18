# PRD — PT. Sinergi Investama Prakasa
## Company Profile Website

**Versi:** 1.0  
**Status:** Draft  
**Author:** Siti / Rexo

---

## 1. Ringkasan

Website company profile untuk PT. Sinergi Investama Prakasa (SIP Corp) — coal trading & sale company berbasis di Jakarta dengan supply chain di Kalimantan. Website bersifat **single-page landing** dengan storytelling scroll, dark premium theme, dan form pendataan prospek.

---

## 2. Tujuan

- Menampilkan profil perusahaan secara profesional dan meyakinkan
- Menjembatani calon buyer (domestik & multilateral) untuk menghubungi tim sales
- Mengumpulkan lead melalui form pendataan (nama, no. telp, email, komentar)
- Menunjukkan kapabilitas trading batubara multi-grade

---

## 3. Target Audiens

- Buyer batubara domestik (industri, PLTU)
- Buyer multilateral (export market)
- Calon mitra trading / investor

---

## 4. Referensi Visual & Tone

| Elemen | Arah |
|--------|------|
| **Tema** | Dark premium, cinematic, industrial-elegan |
| **Warna** | Navy blue `#0f1f33`–`#1a3a5c`, Gold `#c8a84e`–`#e5c76b` |
| **Font** | Inter (body), serif opsional untuk heading |
| **Hero** | Video background (coal mining / shipping) + overlay gradien |
| **Glassmorphism** | Card & navbar dengan `backdrop-filter: blur()` |
| **Layout** | Bento grid, floating cards, staggered animation |
| **Scroll** | Scroll-triggered parallax + cinematic reveals |

---

## 5. Arsitektur Halaman (Single Page)

```
┌──────────────────────────────────────────┐
│  NAVBAR (sticky, glass, gold accent)     │
├──────────────────────────────────────────┤
│  1. HERO                                 │
│     Video BG · Overlay · Tagline · CTA   │
├──────────────────────────────────────────┤
│  2. SNAPSHOT / COMPANY AT A GLANCE       │
│     Bento grid: AHU, NIB, lokasi, dll    │
├──────────────────────────────────────────┤
│  3. ABOUT US                             │
│     Parallax split · company desc        │
├──────────────────────────────────────────┤
│  4. VISION & MISSION                     │
│     Floating cards staggered reveal      │
├──────────────────────────────────────────┤
│  5. PRODUCTS / COAL GRADES               │
│     Tabel interaktif · bento cards       │
├──────────────────────────────────────────┤
│  6. OPERATIONAL FLOW                     │
│     Horizontal timeline · scroll snap    │
├──────────────────────────────────────────┤
│  7. WHY US                               │
│     4 pillars: Quality, Quantity, ...    │
├──────────────────────────────────────────┤
│  8. CONTACT + LEAD FORM                  │
│     Glassmorphism card · Nama, No.Telp,  │
│     Email, Komentar · Submit →           │
├──────────────────────────────────────────┤
│  FOOTER                                  │
│     Address · Contact · Social           │
└──────────────────────────────────────────┘
```

---

## 6. Fitur & Fungsionalitas

### 6.1 Form Pendataan (Wajib)
| Field | Tipe | Validasi |
|-------|------|----------|
| Nama | text | required |
| No. Telepon | tel | required, min 10 digit |
| Email | email | opsional |
| Komentar | textarea | required, min 10 char |

**Backend:** Data disimpan ke file JSON lokal (static) atau API endpoint. Untuk MVP cukup localStorage + notifikasi ke Telegram via Hermes.

### 6.2 Animasi & Interaksi
- **GSAP ScrollTrigger** — seluruh scroll animation
- **Parallax** — lapisan latar bergerak lebih lambat
- **Staggered reveal** — card muncul bergantian
- **Floating cards** — hover lift + glow effect
- **Counter animate** — angka statistik

### 6.3 Performa
- Lazy load video hero
- Optimasi gambar (WebP)
- Minimal dependencies

---

## 7. Alur Pengunjung

```
Land → Hero (wow) → Snapshot (percaya) → About (kenal)
→ Visi Misi (nilai) → Produk (spesifikasi) → Flow (proses)
→ Why Us (yakin) → Contact + Form (action)
```

**CTA utama:** "Hubungi Kami" di hero → smooth scroll ke form.

---

## 8. Tech Stack

| Layer | Pilihan |
|-------|---------|
| **HTML** | Semantic HTML5 |
| **CSS** | Vanilla CSS + CSS Variables |
| **Animasi** | GSAP + ScrollTrigger | atau | Lenis + AOS |
| **Form** | Static JSON + Hermes notification |
| **Deploy** | Static hosting (Netlify / Vercel / GitHub Pages) |

### Opsi Library Animasi

| Library | Pro | Kontra |
|---------|-----|--------|
| **GSAP + ScrollTrigger** | Kontrol penuh, cinematic, mature | Berbayar (GSAP) utk commercial, ScrollTrigger gratis |
| **Lenis + AOS** | Smooth scroll ringan, gratis | Efek terbatas, kurang wow |
| **Framer Motion (React)** | Modern, powerful | Butuh React, overkill utk landing |

**Rekomendasi: GSAP + ScrollTrigger** — paling cocok buat efek cinematic.

---

## 9. Milestone

| Fase | Output |
|------|--------|
| **Fase 1** | PRD + Blueprint ✅ |
| **Fase 2** | HTML skeleton + CSS framework + GSAP init |
| **Fase 3** | Hero section + Navbar |
| **Fase 4** | Semua section + form |
| **Fase 5** | Animasi + Parallax |
| **Fase 6** | CMS / data integration |
| **Fase 7** | Deploy |

---

## 10. Risiko & Mitigasi

| Risiko | Mitigasi |
|--------|----------|
| Video hero berat | Gunakan compressed MP4 + poster fallback |
| GSAP commercial license | ScrollTrigger gratis; ganti Lenis + AOS kalo budget masalah |
| Form data hilang | Backup ke JSON + Hermes notification |
