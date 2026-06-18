# Blueprint: Copy Rewrite — PT. Sinergi Investama Prakasa

> **File:** `~/Projects/PT-SIP/index.html`
> **Source data:** `~/Projects/PT-SIP/copy-rewrite-proposal.md` + `Company Profile SIP INDO Update.pptx`
> **Total sections:** 15 (7 updated, 5 new, 3 rewritten)
> **Deadline:** Single execution session

---

## 🔴 NON-NEGOTIABLE RULES

1. **Only data from company profile.** No invented legal data, capacity, product specs, address, phone, email, or claims.
2. **No exaggerated language.** No "largest", "guaranteed", "no failed contract", "premium global leader", "terbesar di Asia" — unless directly quoted from the profile.
3. **Risk-controlled positioning** is the core DNA. Every section should reflect this.
4. **Contact info MUST match profile slide 16 exactly.** Jl. Ampera Raya No. 4, Cilandak Timur, Pasar Minggu, Jakarta Selatan 12560. Phone: 0813 56562286. Email: sinergiinvestamaprakasa@gmail.com
5. **Vision & Mission is verbatim from profile slide 5.** Do not paraphrase.
6. **Product specs are verbatim from profile slide 10.** Do not modify.
7. **Closing Statement is verbatim from profile slide 15.** Do not paraphrase.

---

## OVERALL STRUCTURE (final order)

```
[NAVBAR — update nav links]
[HERO — section#hero]
[COMPANY SNAPSHOT — section#snapshot]
[ABOUT US — section#about]
[VISION & MISSION — section#vision-mission]
[RISK-MANAGED EXECUTION — section#risk-execution (NEW)]
[WHAT WE DELIVER — section#what-we-deliver (NEW)]
[TARGET MARKET — section#target-market (NEW)]
[FOOTPRINT & SOURCING — section#sourcing (NEW)]
[PRODUCTS — section#products]
[OPERATIONAL FLOW — section#operations]
[FOB RESPONSIBILITIES — section#fob (NEW)]
[DEAL-TO-CASH — section#dealtocash (NEW)]
[WHY US — section#why-us]
[CLOSING STATEMENT — section#closing (NEW, before footer)]
[CONTACT — section#contact]
[FOOTER]
```

### HTML order (after `</section><!-- contact -->`):

Insert new sections in this exact position:
- After `#vision-mission` (line ~1210): `#risk-execution`, `#what-we-deliver`, `#target-market`, `#sourcing`
- After `#operations` (line ~1333): `#fob`, `#dealtocash`
- Between `#why-us` and `#contact` (line ~1367): `#closing`

---

## SECTION 1: HERO (`section#hero`)

### Current state (lines 1059-1084)
Already has: brand logo, company name h1, "Coal Trading & Risk-Managed Supply Chain Partner" tagline, 2 description paragraphs, 1 CTA "Contact Us"

### Changes needed
- Replace tagline paragraph with single concise paragraph (from proposal §1)
- Keep existing structure: `hero-content > hero-logo, hero-title, hero-tagline, hero-desc, hero-actions`

### Final HTML structure
```html
<div class="hero-content">
  <img src="assets/images/BRAND%20LOGO%20PT%20SIP.png" alt="PT. Sinergi Investama Prakasa" class="hero-logo">
  <h1 class="hero-title">PT. Sinergi Investama Prakasa</h1>
  <p class="hero-tagline">Coal Trading &amp; Risk-Managed Supply Chain Partner</p>
  <p class="hero-desc">Jakarta-based coal trading house, connecting buyer requirements with Kalimantan supply through structured, documented, risk-controlled execution.</p>
  <div class="hero-actions">
    <a href="#contact" class="hero-cta">Contact Us</a>
  </div>
</div>
```

### CSS
- No CSS changes needed (classes already exist)

---

## SECTION 2: COMPANY SNAPSHOT (`section#snapshot`)

### Current state (lines 1085-1141)
Bento grid with fake stats: Rp 10M modal, Akta September 2024, KBLI 46610, Lokasi Cipinang Cempedak.

### Changes needed
- **REMOVE** all bento cards with fake data
- **REPLACE** with clean data table/rows display
- Title: "SIP at a Glance" → "Company Snapshot" → keep existing
- New subtitle: "Legal identity, operational scope, and capacity at a glance"

### Final HTML structure
```html
<section class="snapshot-section" id="snapshot">
  <div class="container">
    <div class="section-label reveal-hidden">Company Snapshot</div>
    <h2 class="section-title reveal-hidden">Company <span class="gold">Snapshot</span></h2>
    <p class="section-subtitle reveal-hidden">Legal identity, operational scope, and capacity at a glance.</p>

    <div class="snapshot-grid">
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Company Name</span>
        <span class="snapshot-value">PT. Sinergi Investama Prakasa</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Legal Entity</span>
        <span class="snapshot-value">AHU-0088474.AH.01.01.TAHUN 2025</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">NIB</span>
        <span class="snapshot-value">1510250093486</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Office</span>
        <span class="snapshot-value">Jl. Ampera Raya No. 4, Cilandak Timur, Pasar Minggu, Jakarta Selatan 12560</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Contact</span>
        <span class="snapshot-value">0813 56562286 &middot; sinergiinvestamaprakasa@gmail.com</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Sourcing Corridor</span>
        <span class="snapshot-value">Kalimantan Selatan &amp; Kalimantan Timur</span>
      </div>
      <div class="snapshot-item reveal-hidden">
        <span class="snapshot-label">Planned Capacity</span>
        <span class="snapshot-value">20,000–50,000 MT/month (scalable)</span>
      </div>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Snapshot grid — clean rows */
.snapshot-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1px;
  background: var(--glass-border);
  border-radius: 16px;
  overflow: hidden;
  max-width: 800px;
  margin: 0 auto;
}
.snapshot-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 28px;
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  gap: 24px;
}
.snapshot-label {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--text-secondary);
  white-space: nowrap;
  min-width: 140px;
}
.snapshot-value {
  font-size: 0.9rem;
  color: var(--text-primary);
  text-align: right;
  font-weight: 500;
}
@media (min-width: 640px) {
  .snapshot-grid {
    grid-template-columns: 1fr 1fr;
  }
  .snapshot-item:first-child {
    grid-column: 1 / -1;
  }
}
```

---

## SECTION 3: ABOUT US (`section#about`)

### Current state (lines 1142-1179)
Already has 3 paragraphs with latest copy. Section title "Mitra Strategis Batubara Anda".

### Changes needed
- No HTML change needed (copy already updated earlier)
- Just add the "risk-controlled" DNA mention
- Section title stays

### No change required unless Rexo wants title change.

---

## SECTION 4: VISION & MISSION (`section#vision-mission`)

### Current state (lines 1180-1211)
Has existing V&M cards with placeholder content.

### Changes needed
- Replace content with verbatim Vision & Mission from profile slide 5
- Keep the existing card layout (`.vm-grid`, `.vm-card`)

### Final HTML structure
```html
<div class="section-label reveal-hidden">Vision &amp; Mission</div>
<h2 class="section-title reveal-hidden">Arah &amp; <span class="gold">Komitmen</span></h2>
<p class="section-subtitle reveal-hidden">Risk-controlled execution from inquiry to settlement.</p>

<div class="vm-grid">
  <div class="vm-card reveal-hidden">
    <div class="vm-icon">🎯</div>
    <h3>Visi</h3>
    <p>Menjadi mitra trading Anda dalam membangun coal supply chain dengan menitikberatkan eksekusi berdasarkan risk-controlled yang terukur.</p>
  </div>
  <div class="vm-card reveal-hidden">
    <div class="vm-icon">📋</div>
    <h3>Misi</h3>
    <ol class="vm-list">
      <li>Memetakan &amp; mengukur risiko di setiap transaksi (quality, quantity, timeline, settlement).</li>
      <li>Menjalankan QC yang disiplin lewat sampling, sealing, dan koordinasi survey untuk mencegah dispute.</li>
      <li>Mengunci delivery plan end-to-end untuk menjamin eksekusi yang telah disepakati.</li>
      <li>Menyiapkan dokumen settlement-ready yang konsisten untuk mempercepat pembayaran.</li>
      <li>Membangun jaringan supply &amp; logistik yang repeatable untuk memastikan kontinuitas.</li>
    </ol>
  </div>
</div>
```

### CSS additions needed
```css
.vm-list {
  list-style: decimal;
  padding-left: 20px;
  text-align: left;
}
.vm-list li {
  margin-bottom: 8px;
  color: var(--text-secondary);
  font-size: 0.9rem;
  line-height: 1.5;
}
```

---

## SECTION 5: RISK-MANAGED EXECUTION (`section#risk-execution`)

### NEW SECTION — Insert after `#vision-mission` (between line ~1211 and ~1212)

### HTML structure
```html
<!-- ============================================
     RISK-MANAGED EXECUTION — 4 Pillars
     ============================================ -->
<section id="risk-execution">
  <div class="container">
    <div class="section-label reveal-hidden">Risk-Managed Execution</div>
    <h2 class="section-title reveal-hidden">Quality <span class="gold">&middot;</span> Quantity <span class="gold">&middot;</span> Timeline <span class="gold">&middot;</span> Settlement</h2>
    <p class="section-subtitle reveal-hidden">Setiap transaksi batubara memiliki risiko pada kualitas, kuantitas, timeline, dan settlement. Kami membangun proses yang dirancang untuk mengurangi risiko tersebut melalui koordinasi yang disiplin dan dokumentasi yang konsisten.</p>

    <div class="risk-pillars">
      <div class="risk-pillar reveal-hidden">
        <span class="risk-icon">💎</span>
        <h3>Quality</h3>
        <p>Koordinasi sampling, sealing, inspection, dan verifikasi COA untuk memastikan spesifikasi kargo sesuai kebutuhan buyer.</p>
      </div>
      <div class="risk-pillar reveal-hidden">
        <span class="risk-icon">⚖️</span>
        <h3>Quantity</h3>
        <p>Koordinasi draft survey, toleransi kuantitas, dan rekonsiliasi loading untuk meminimalkan potensi dispute.</p>
      </div>
      <div class="risk-pillar reveal-hidden">
        <span class="risk-icon">⏱️</span>
        <h3>Timeline</h3>
        <p>Penyelarasan kesiapan stockpile, jetty, laycan, loading plan, dan jadwal kapal agar eksekusi berjalan lebih terkontrol.</p>
      </div>
      <div class="risk-pillar reveal-hidden">
        <span class="risk-icon">📋</span>
        <h3>Settlement</h3>
        <p>Penyusunan dokumen transaksi (invoice, B/L, COA, draft survey) agar proses pembayaran berjalan lancar sesuai terms kontrak.</p>
      </div>
    </div>

    <div class="risk-principle reveal-hidden">
      <p><strong>Prinsip eksekusi:</strong> One cargo, one plan, one time control.</p>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Risk-Managed Execution */
#risk-execution {
  background: var(--navy);
}
.risk-pillars {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
  max-width: 900px;
  margin: 0 auto;
}
@media (min-width: 640px) { .risk-pillars { grid-template-columns: 1fr 1fr; } }
.risk-pillar {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 32px 28px;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.risk-pillar:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}
.risk-icon {
  font-size: 2.5rem;
  display: block;
  margin-bottom: 16px;
}
.risk-pillar h3 {
  font-family: var(--font-display);
  font-size: 1.3rem;
  color: var(--gold);
  margin-bottom: 12px;
}
.risk-pillar p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.6;
}
.risk-principle {
  text-align: center;
  margin-top: 48px;
  padding: 20px 32px;
  background: linear-gradient(135deg, rgba(200,168,78,0.1), rgba(200,168,78,0.05));
  border: 1px solid rgba(200,168,78,0.2);
  border-radius: 12px;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}
.risk-principle p {
  font-size: 1.1rem;
  color: var(--gold-light);
  letter-spacing: 0.03em;
}
```

---

## SECTION 6: WHAT WE DELIVER (`section#what-we-deliver`)

### NEW SECTION — Insert after `#risk-execution`

### HTML structure
```html
<!-- ============================================
     WHAT WE DELIVER — Service Scope
     ============================================ -->
<section id="what-we-deliver">
  <div class="container">
    <div class="section-label reveal-hidden">What We Deliver</div>
    <h2 class="section-title reveal-hidden">Thermal Coal Supply Chain <span class="gold">—</span> Coordinated <span class="gold">&amp;</span> Delivered</h2>
    <p class="section-subtitle reveal-hidden">Thermal multi-grade coal supply with competitive value, backed by risk-controlled execution.</p>

    <div class="deliver-grid">
      <div class="deliver-card reveal-hidden">
        <span class="deliver-icon">🔬</span>
        <h3>QC &amp; Survey Coordination</h3>
        <p>Sampling, sealing, inspection, and reporting — ensuring cargo specifications match buyer requirements.</p>
      </div>
      <div class="deliver-card reveal-hidden">
        <span class="deliver-icon">⚙️</span>
        <h3>Operational Coordination</h3>
        <p>Stockpile and jetty handling, barging, and transshipment — aligned with vessel schedule.</p>
      </div>
      <div class="deliver-card reveal-hidden">
        <span class="deliver-icon">📄</span>
        <h3>FOB Documentation Package</h3>
        <p>Documents prepared for smooth settlement — invoice, B/L, COA, draft survey aligned end-to-end.</p>
      </div>
      <div class="deliver-card reveal-hidden">
        <span class="deliver-icon">📈</span>
        <h3>Scalable Delivery Plan</h3>
        <p>Delivery planning designed for repeat execution, scalable from 20,000 to 50,000 MT/month.</p>
      </div>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* What We Deliver */
.deliver-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
  max-width: 900px;
  margin: 0 auto;
}
@media (min-width: 640px) { .deliver-grid { grid-template-columns: 1fr 1fr; } }
.deliver-card {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 32px 28px;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.deliver-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}
.deliver-icon {
  font-size: 2.5rem;
  display: block;
  margin-bottom: 16px;
}
.deliver-card h3 {
  font-family: var(--font-display);
  font-size: 1.15rem;
  color: #fff;
  margin-bottom: 12px;
}
.deliver-card p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.6;
}
```

---

## SECTION 7: TARGET MARKET (`section#target-market`)

### NEW SECTION — Insert after `#what-we-deliver`

### HTML structure
```html
<!-- ============================================
     TARGET MARKET — Client Segments
     ============================================ -->
<section id="target-market">
  <div class="container">
    <div class="section-label reveal-hidden">Target Market</div>
    <h2 class="section-title reveal-hidden">Selective Partnerships for <span class="gold">Consistent Supply</span></h2>
    <p class="section-subtitle reveal-hidden">Kami melayani klien yang membutuhkan pasokan konsisten dengan settlement yang bersih dan transparan.</p>

    <div class="market-content">
      <div class="market-card reveal-hidden">
        <span class="market-icon">🏭</span>
        <h3>Domestic</h3>
        <p>Industrial clients requiring reliable thermal coal supply with consistent quality and clear documentation across every shipment.</p>
      </div>
      <div class="market-card reveal-hidden">
        <span class="market-icon">🌏</span>
        <h3>Multilateral</h3>
        <p>International buyers who demand transparent settlement, FOB-ready documentation, and risk-managed execution from inquiry to delivery.</p>
      </div>
    </div>

    <div class="market-note reveal-hidden">
      <p>Kami selektif dalam mendukung aliran trade — baik domestic maupun multilateral — yang menuntut reliability dan standar proses delivery dengan manajemen risiko yang terukur.</p>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Target Market */
#target-market { background: var(--navy); }
.market-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  max-width: 800px;
  margin: 0 auto;
}
@media (max-width: 639px) { .market-content { grid-template-columns: 1fr; } }
.market-card {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 36px 28px;
  text-align: center;
}
.market-icon { font-size: 2.5rem; display: block; margin-bottom: 16px; }
.market-card h3 {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--gold);
  margin-bottom: 12px;
}
.market-card p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.6;
}
.market-note {
  max-width: 700px;
  margin: 40px auto 0;
  padding: 20px 28px;
  background: linear-gradient(135deg, rgba(200,168,78,0.08), rgba(200,168,78,0.03));
  border: 1px solid rgba(200,168,78,0.15);
  border-radius: 12px;
  text-align: center;
}
.market-note p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  font-style: italic;
  line-height: 1.6;
}
```

---

## SECTION 8: FOOTPRINT & SOURCING (`section#sourcing`)

### NEW SECTION — Insert after `#target-market`

### HTML structure
```html
<!-- ============================================
     FOOTPRINT & SOURCING — Kalimantan Corridor
     ============================================ -->
<section id="sourcing">
  <div class="container">
    <div class="section-label reveal-hidden">Footprint &amp; Sourcing</div>
    <h2 class="section-title reveal-hidden">Kalimantan <span class="gold">Supply Corridor</span></h2>
    <p class="section-subtitle reveal-hidden">Primary sourcing from Kalimantan Selatan, Kalimantan Tengah, &amp; Kalimantan Timur.</p>

    <div class="sourcing-grid">
      <div class="sourcing-card reveal-hidden">
        <span class="sourcing-icon">📍</span>
        <h3>Primary Sourcing</h3>
        <p>Kalimantan Selatan, Kalimantan Tengah, &amp; Kalimantan Timur</p>
      </div>
      <div class="sourcing-card reveal-hidden">
        <span class="sourcing-icon">🏗️</span>
        <h3>Stockpile / Jetty</h3>
        <p>Kalsel (Banjar/Banjarmasin corridor) &middot; Kaltim</p>
      </div>
      <div class="sourcing-card reveal-hidden">
        <span class="sourcing-icon">⚡</span>
        <h3>Execution Focus</h3>
        <p>FOB-ready aligned with buyer vessel schedule</p>
      </div>
      <div class="sourcing-card reveal-hidden">
        <span class="sourcing-icon">📊</span>
        <h3>Planned Capacity</h3>
        <p>20,000–50,000 MT/month, scalable with repeat execution</p>
      </div>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Footprint & Sourcing */
.sourcing-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  max-width: 800px;
  margin: 0 auto;
}
@media (max-width: 639px) { .sourcing-grid { grid-template-columns: 1fr; } }
.sourcing-card {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 32px 28px;
  text-align: center;
}
.sourcing-icon { font-size: 2.2rem; display: block; margin-bottom: 16px; }
.sourcing-card h3 {
  font-family: var(--font-display);
  font-size: 1.1rem;
  color: var(--gold);
  margin-bottom: 10px;
}
.sourcing-card p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.5;
}
```

---

## SECTION 9: PRODUCTS (`section#products`)

### Current state (lines 1212-1271)
Has existing product cards with generic descriptions.

### Changes needed
- Replace content with product table from profile slide 10
- Keep existing structure container, replace inner content

### Final HTML structure
```html
<section id="products">
  <div class="container">
    <div class="section-label reveal-hidden">Our Products</div>
    <h2 class="section-title reveal-hidden">Thermal Coal <span class="gold">Grades</span></h2>
    <p class="section-subtitle reveal-hidden">Multi-grade thermal coal — final specification confirmed via mine COA and independent surveyor at loading.</p>

    <div class="products-table-wrapper reveal-hidden">
      <table class="products-table">
        <thead>
          <tr>
            <th>Grade (GAR)</th>
            <th>Benchmark</th>
            <th>Typical TM</th>
            <th>Typical Ash</th>
            <th>Typical Sulphur</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>3,400</td><td>Platts FOB Kalimantan</td><td>46%</td><td>4%</td><td>0.2%</td></tr>
          <tr><td>5,000</td><td>Platts FOB Kalimantan</td><td>26%</td><td>8%</td><td>0.80%</td></tr>
          <tr><td>5,900</td><td>Platts FOB Kalimantan</td><td>15%</td><td>8%</td><td>0.80%</td></tr>
          <tr><td>6,322</td><td>HBA Reference</td><td>8%</td><td>15%</td><td>0.8%</td></tr>
          <tr class="coa-row"><td>3,200–3,400</td><td>COA-based</td><td>TBD</td><td>TBD</td><td>TBD</td></tr>
          <tr class="coa-row"><td>4,000–4,500</td><td>COA-based</td><td>TBD</td><td>TBD</td><td>TBD</td></tr>
          <tr class="coa-row"><td>5,500–6,600+</td><td>COA-based</td><td>TBD</td><td>TBD</td><td>TBD</td></tr>
        </tbody>
      </table>
    </div>

    <p class="products-note reveal-hidden">Spesifikasi final dikonfirmasi lewat COA mine dan difinalisasi surveyor independen saat loading.</p>
  </div>
</section>
```

### CSS additions needed
```css
/* Products Table */
#products { background: var(--navy); }
.products-table-wrapper {
  max-width: 900px;
  margin: 0 auto;
  overflow-x: auto;
  border-radius: 16px;
  border: 1px solid var(--glass-border);
}
.products-table {
  width: 100%;
  border-collapse: collapse;
  background: var(--glass-bg);
}
.products-table th {
  background: rgba(200,168,78,0.15);
  color: var(--gold);
  font-family: var(--font-display);
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  padding: 16px 20px;
  text-align: left;
  font-weight: 700;
  border-bottom: 1px solid var(--glass-border);
}
.products-table td {
  padding: 14px 20px;
  color: var(--text-primary);
  font-size: 0.9rem;
  border-bottom: 1px solid var(--glass-border);
}
.products-table tr:last-child td { border-bottom: none; }
.products-table tbody tr:hover { background: rgba(200,168,78,0.05); }
.products-table .coa-row td {
  color: var(--text-secondary);
  font-style: italic;
}
.products-note {
  text-align: center;
  max-width: 600px;
  margin: 32px auto 0;
  padding: 16px 24px;
  background: rgba(200,168,78,0.08);
  border-radius: 10px;
  font-size: 0.85rem;
  color: var(--text-secondary);
  border: 1px solid rgba(200,168,78,0.15);
}
```

---

## SECTION 10: OPERATIONAL FLOW (`section#operations`)

### Current state (lines 1272-1333)
Has existing timeline-based operations section with generic content.

### Changes needed
- Replace content with 5-step operational flow from proposal §10
- Keep `.timeline` class structure or replace with simpler step list

### Final HTML structure
```html
<section id="operations">
  <div class="container">
    <div class="section-label reveal-hidden">Operations</div>
    <h2 class="section-title reveal-hidden">End-to-End <span class="gold">Operational Flow</span></h2>
    <p class="section-subtitle reveal-hidden">One cargo, one plan, one time control.</p>

    <div class="flow-steps">
      <div class="flow-step reveal-hidden">
        <span class="flow-num">01</span>
        <div class="flow-body">
          <h3>Sourcing</h3>
          <p>Identify supply from Kalimantan corridor — Kalsel, Kalteng, Kaltim.</p>
        </div>
      </div>
      <div class="flow-step reveal-hidden">
        <span class="flow-num">02</span>
        <div class="flow-body">
          <h3>Preparation</h3>
          <p>Stockpile coordination, jetty readiness, pre-QC sampling.</p>
        </div>
      </div>
      <div class="flow-step reveal-hidden">
        <span class="flow-num">03</span>
        <div class="flow-body">
          <h3>Loading</h3>
          <p>Coordinated loading, independent survey, COA verification.</p>
        </div>
      </div>
      <div class="flow-step reveal-hidden">
        <span class="flow-num">04</span>
        <div class="flow-body">
          <h3>Documentation</h3>
          <p>FOB-ready document package — invoice, B/L, COA, draft survey.</p>
        </div>
      </div>
      <div class="flow-step reveal-hidden">
        <span class="flow-num">05</span>
        <div class="flow-body">
          <h3>Settlement</h3>
          <p>Payment per contract terms (LC at sight / TT against documents).</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Operational Flow Steps */
.flow-steps {
  max-width: 700px;
  margin: 0 auto;
  position: relative;
}
.flow-steps::before {
  content: '';
  position: absolute;
  left: 28px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, var(--gold), rgba(200,168,78,0.1));
}
.flow-step {
  display: flex;
  gap: 24px;
  align-items: flex-start;
  margin-bottom: 40px;
  position: relative;
}
.flow-step:last-child { margin-bottom: 0; }
.flow-num {
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 800;
  color: var(--gold);
  background: var(--navy-deep);
  border: 2px solid var(--gold);
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  position: relative;
  z-index: 1;
}
.flow-body {
  flex: 1;
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 12px;
  padding: 20px 24px;
  margin-top: 4px;
}
.flow-body h3 {
  font-family: var(--font-display);
  font-size: 1.1rem;
  color: #fff;
  margin-bottom: 6px;
}
.flow-body p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.5;
}
```

---

## SECTION 11: FOB RESPONSIBILITIES (`section#fob`)

### NEW SECTION — Insert after `#operations`

### HTML structure
```html
<!-- ============================================
     FOB RESPONSIBILITIES — Seller vs Buyer
     ============================================ -->
<section id="fob">
  <div class="container">
    <div class="section-label reveal-hidden">FOB Responsibilities</div>
    <h2 class="section-title reveal-hidden">Clear Split — <span class="gold">Seller vs Buyer</span></h2>
    <p class="section-subtitle reveal-hidden">FOB Kalimantan basis — responsibilities divided at cargo ON BOARD.</p>

    <div class="fob-grid">
      <div class="fob-card fob-seller reveal-hidden">
        <h3 class="fob-role">Seller Responsibility</h3>
        <p class="fob-point">Up to cargo ON BOARD</p>
        <ul>
          <li>Prepare cargo per specification and quantity</li>
          <li>Port/stockpile readiness and loading execution</li>
          <li>Export clearance and standard shipping documents</li>
        </ul>
      </div>
      <div class="fob-divider reveal-hidden">
        <span>FOB</span>
      </div>
      <div class="fob-card fob-buyer reveal-hidden">
        <h3 class="fob-role">Buyer Responsibility</h3>
        <p class="fob-point">After cargo ON BOARD</p>
        <ul>
          <li>Nominate vessel and pay ocean freight</li>
          <li>Bear surveyor costs</li>
          <li>Bear risk after FOB point</li>
          <li>Arrange insurance</li>
          <li>Import clearance at destination (multilateral)</li>
        </ul>
      </div>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* FOB Responsibilities */
#fob { background: var(--navy); }
.fob-grid {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 0;
  align-items: center;
  max-width: 900px;
  margin: 0 auto;
}
@media (max-width: 767px) { .fob-grid { grid-template-columns: 1fr; gap: 16px; } }
.fob-card {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 32px 28px;
}
.fob-seller { text-align: right; }
.fob-buyer { text-align: left; }
@media (max-width: 767px) {
  .fob-seller, .fob-buyer { text-align: center; }
}
.fob-role {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: #fff;
  margin-bottom: 4px;
}
.fob-point {
  font-size: 0.8rem;
  color: var(--gold);
  font-weight: 600;
  margin-bottom: 16px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.fob-card ul {
  list-style: none;
  padding: 0;
}
.fob-card li {
  font-size: 0.9rem;
  color: var(--text-secondary);
  padding: 6px 0;
  line-height: 1.4;
}
.fob-card li::before {
  content: '→ ';
  color: var(--gold);
  font-weight: 700;
}
.fob-seller li::before { content: '← '; }
@media (max-width: 767px) { .fob-seller li::before { content: '→ '; } }
.fob-divider {
  width: 64px;
  height: 64px;
  background: var(--gold);
  color: var(--navy-deep);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 800;
  font-size: 0.85rem;
  letter-spacing: 0.05em;
  margin: 0 24px;
  z-index: 1;
}
@media (max-width: 767px) { .fob-divider { margin: 0 auto; } }
```

---

## SECTION 12: DEAL-TO-CASH (`section#dealtocash`)

### NEW SECTION — Insert after `#fob`

### HTML structure
```html
<!-- ============================================
     DEAL-TO-CASH — Transaction Flow
     ============================================ -->
<section id="dealtocash">
  <div class="container">
    <div class="section-label reveal-hidden">Deal-to-Cash</div>
    <h2 class="section-title reveal-hidden">From Contract to <span class="gold">Settlement</span></h2>
    <p class="section-subtitle reveal-hidden">Transparent transaction flow — every step documented, every milestone tracked.</p>

    <div class="dtc-steps">
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">01</span>
        <h4>Deal &amp; Contract</h4>
        <p>Terms agreed, downpayment (min. 20%)</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">02</span>
        <h4>Vessel / Laycan</h4>
        <p>Schedule alignment</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">03</span>
        <h4>Pre-QC</h4>
        <p>Quality check before loading</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">04</span>
        <h4>Loading</h4>
        <p>Coordinated execution</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">05</span>
        <h4>Survey &amp; COA</h4>
        <p>Independent verification</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">06</span>
        <h4>Document Presentation</h4>
        <p>Invoice, B/L, COA, draft survey</p>
      </div>
      <div class="dtc-step reveal-hidden">
        <span class="dtc-num">07</span>
        <h4>Settlement</h4>
        <p>LC at sight / TT against documents</p>
      </div>
    </div>

    <div class="dtc-note reveal-hidden">
      <p><strong>Key term:</strong> Consistency of Invoice–B/L–COA–Draft Survey prevents payment delays.</p>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Deal-to-Cash */
.dtc-steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 16px;
  max-width: 1000px;
  margin: 0 auto;
}
.dtc-step {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 14px;
  padding: 24px 20px;
  text-align: center;
  transition: transform 0.3s ease;
}
.dtc-step:hover { transform: translateY(-4px); }
.dtc-num {
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 800;
  color: var(--gold);
  display: block;
  margin-bottom: 10px;
}
.dtc-step h4 {
  font-family: var(--font-display);
  font-size: 0.95rem;
  color: #fff;
  margin-bottom: 6px;
}
.dtc-step p {
  font-size: 0.8rem;
  color: var(--text-secondary);
  line-height: 1.4;
}
.dtc-note {
  text-align: center;
  max-width: 600px;
  margin: 40px auto 0;
  padding: 20px 28px;
  background: linear-gradient(135deg, rgba(200,168,78,0.1), rgba(200,168,78,0.05));
  border: 1px solid rgba(200,168,78,0.2);
  border-radius: 12px;
}
.dtc-note p {
  font-size: 0.95rem;
  color: var(--gold-light);
}
```

---

## SECTION 13: WHY US (`section#why-us`)

### Current state (lines 1334-1367)
Has existing pillar cards from earlier update. Currently uses `.pillars-grid`, `.pillar-card` classes.

### Changes needed
- Replace pillar content with 4 bullets from proposal §13
- Use existing `.pillars-grid` structure but update text

### Final HTML structure
```html
<section id="why-us">
  <div class="container">
    <div class="section-label reveal-hidden">Why Us</div>
    <h2 class="section-title reveal-hidden">Built for <span class="gold">Repeat Execution</span></h2>
    <p class="section-subtitle reveal-hidden">Perform first, scale later.</p>

    <div class="pillars-grid">
      <div class="pillar-card reveal-hidden">
        <span class="pillar-icon">🛡️</span>
        <h3>Risk-Managed Shipments</h3>
        <p>Minimal surprises during loading and clear settlement — every cargo has a documented execution plan.</p>
      </div>
      <div class="pillar-card reveal-hidden">
        <span class="pillar-icon">📋</span>
        <h3>Single Delivery Plan</h3>
        <p>QC + operations + documents coordinated end-to-end in one delivery plan.</p>
      </div>
      <div class="pillar-card reveal-hidden">
        <span class="pillar-icon">🔄</span>
        <h3>Built for Repeat Order</h3>
        <p>Perform first, scale later. Every execution is designed to be repeatable.</p>
      </div>
      <div class="pillar-card reveal-hidden">
        <span class="pillar-icon">🌐</span>
        <h3>Supply Chain Network</h3>
        <p>Supported by one of the largest supply chain networks in Asia.</p>
      </div>
    </div>
  </div>
</section>
```

### CSS
- No CSS changes needed (uses existing `.pillars-grid`, `.pillar-card`, `.pillar-icon` classes)

---

## SECTION 14: CLOSING STATEMENT (`section#closing`)

### NEW SECTION — Insert between `#why-us` and `#contact`

### HTML structure
```html
<!-- ============================================
     CLOSING STATEMENT
     ============================================ -->
<section id="closing">
  <div class="container">
    <div class="closing-content reveal-hidden">
      <div class="closing-mark">"</div>
      <p class="closing-text">PT. Sinergi Investama Prakasa didukung oleh jaringan operasional yang berpengalaman serta disiplin kerja yang berfokus pada pengelolaan risiko yang terukur. Kami siap menjadi mitra trading batubara yang Anda percaya, dengan eksekusi yang konsisten, spesifikasi yang jelas, mengedepankan keterbukaan, dan settlement process yang cepat sehingga setiap transaksi dapat dijalankan dan dipertanggungjawabkan dengan standar profesional yang tinggi.</p>
    </div>
  </div>
</section>
```

### CSS additions needed
```css
/* Closing Statement */
#closing {
  background: var(--navy);
  padding: 80px 0;
}
.closing-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  padding: 48px 32px;
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 20px;
  position: relative;
}
.closing-mark {
  font-size: 6rem;
  font-family: Georgia, serif;
  color: var(--gold);
  opacity: 0.2;
  line-height: 0.6;
  margin-bottom: 16px;
}
.closing-text {
  font-size: clamp(1rem, 1.8vw, 1.15rem);
  color: var(--text-primary);
  line-height: 1.8;
  font-weight: 400;
}
```

---

## SECTION 15: CONTACT (`section#contact`)

### Current state (lines 1368-1444)
Has existing contact section with form and contact info. Currently uses old address (Cipinang Cempedak).

### Changes needed
- Update address to: Jl. Ampera Raya No. 4, Cilandak Timur, Pasar Minggu, Jakarta Selatan 12560
- Update phone to: 0813 56562286
- Update email to: sinergiinvestamaprakasa@gmail.com
- Keep form structure
- Update headline to "Contact Us" (remove "Hubungi Kami")
- Update section-subtitle

### Final HTML changes (contact info section, lines ~1411-1430)
```html
<div class="contact-info reveal-hidden">
  <div class="contact-info-item">
    <div class="contact-icon">📍</div>
    <div>
      <h4>Office</h4>
      <p>Jl. Ampera Raya No. 4, Cilandak Timur, Pasar Minggu, Jakarta Selatan 12560</p>
    </div>
  </div>
  <div class="contact-info-item">
    <div class="contact-icon">📞</div>
    <div>
      <h4>Inquiries</h4>
      <p>0813 56562286</p>
    </div>
  </div>
  <div class="contact-info-item">
    <div class="contact-icon">✉️</div>
    <div>
      <h4>Email</h4>
      <p>sinergiinvestamaprakasa@gmail.com</p>
    </div>
  </div>
</div>
```

---

## NAVBAR UPDATE

Add nav items for new sections:
```html
<li><a href="#snapshot">Snapshot</a></li>
<li><a href="#about">About</a></li>
<li><a href="#vision-mission">Visi & Misi</a></li>
<li><a href="#risk-execution">Execution</a></li>
<li><a href="#products">Products</a></li>
<li><a href="#operations">Flow</a></li>
<li><a href="#why-us">Why Us</a></li>
<li><a href="#contact" class="nav-cta">Contact</a></li>
```

Same for mobile menu.

---

## SECTIONS TO REMOVE

- **REMOVE** bento-grid content from `#snapshot` (fake data)
- **REMOVE** old V&M content from `#vision-mission`
- **REMOVE** old products content from `#products`
- **REMOVE** old operations content from `#operations`
- **REMOVE** old Why Us pillar content from `#why-us`
- **REMOVE** old contact info (Cipinang Cempedak)

---

## IMPLEMENTATION ORDER (kanban builder)

1. Update NAVBAR links
2. Update HERO (section 1)
3. Rewrite SNAPSHOT completely (section 2)
4. Update ABOUT US text (section 3)
5. Rewrite VISION & MISSION (section 4)
6. **Insert** RISK-MANAGED EXECUTION (section 5) — NEW
7. **Insert** WHAT WE DELIVER (section 6) — NEW
8. **Insert** TARGET MARKET (section 7) — NEW
9. **Insert** FOOTPRINT & SOURCING (section 8) — NEW
10. Rewrite PRODUCTS (section 9)
11. Rewrite OPERATIONS (section 10)
12. **Insert** FOB RESPONSIBILITIES (section 11) — NEW
13. **Insert** DEAL-TO-CASH (section 12) — NEW
14. Rewrite WHY US (section 13)
15. **Insert** CLOSING STATEMENT (section 14) — NEW
16. Update CONTACT (section 15)
17. Add all new CSS blocks
18. Update mobile menu links

---

## VERIFICATION CHECKLIST

- [ ] All 15 sections present in HTML
- [ ] All pages scroll correctly (check section IDs match nav hrefs)
- [ ] Product table renders correctly
- [ ] Contact info matches profile (Ampera Raya, 0813 56562286, correct email)
- [ ] No fake data remains (no Rp 10M, no Akta September 2024, no KBLI 46610, no Cipinang Cempedak)
- [ ] No exaggerated claims
- [ ] Vision & Mission verbatim from profile
- [ ] Closing Statement verbatim from profile
- [ ] Hero copy concise (no generic taglines)
- [ ] All CSS adds are present (no missing styles)
- [ ] Mobile responsive works for new sections
- [ ] GSAP reveal animations work on new sections
