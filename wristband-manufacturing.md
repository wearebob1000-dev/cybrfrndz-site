# CYBR FRNDZ Wristband — Manufacturing Spec & Business Plan

*Last updated: 2026-02-12*

---

## Product Overview

The CYBR FRNDZ Band is an RFID/NFC wristband that lets kids earn Respect Points (RP) by tapping wrists — no phone required. Taps are stored offline on the band and synced to the app when the kid gets home.

**Retail Price: $29.99**
**Target: Ages 6-14**

---

## Technical Architecture

### Option A: Simple NFC (Low Cost, MVP)
**How it works:** Each band has a unique NFC tag (NTAG216). Tapping two bands together doesn't work natively (NFC is reader → tag, not tag → tag). Instead:
- Each band stores a unique ID
- Kids tap their band to a **phone** or **school kiosk** to register interactions
- The kiosk/phone logs "Band A tapped at location X at time Y"
- When another kid taps at the same kiosk within 30 seconds, it counts as a "friend tap"

**Pros:** Dirt cheap ($1-3/unit), no battery, indestructible
**Cons:** Can't do direct band-to-band taps, needs a reader device nearby

### Option B: Active RFID with Microcontroller (Premium, Full Vision)
**How it works:** Each band has a low-power microcontroller + NFC transceiver that can both read AND write. Band-to-band taps work directly.
- Tap wrists → both bands exchange IDs and log the interaction
- Onboard flash memory stores 1000+ taps
- Sync to phone/tablet via NFC when at home
- Coin cell battery lasts 6+ months

**Pros:** True band-to-band magic, no phone needed at all
**Cons:** Higher cost ($8-15/unit), requires battery, more complex

### Recommended: Option A for MVP, Option B for V2

---

## Bill of Materials (BOM) — Option A (MVP)

| Component | Unit Cost (1K qty) | Unit Cost (10K qty) | Notes |
|-----------|-------------------|---------------------|-------|
| NTAG216 NFC chip | $0.15 | $0.08 | 888 bytes, ISO 14443A |
| NFC antenna (etched) | $0.10 | $0.06 | Copper etched coil |
| Silicone strap | $0.60 | $0.35 | Medical-grade, hypoallergenic, custom color |
| Strap housing/module | $0.30 | $0.18 | Injection-molded ABS, holds chip |
| Custom printing (logo) | $0.15 | $0.08 | Screen print or laser engrave |
| Packaging (box + insert) | $0.40 | $0.25 | Branded box, card insert |
| Assembly labor | $0.30 | $0.20 | Chip embed + seal + QC |
| **TOTAL BOM** | **$2.00** | **$1.20** | |

## BOM — Option B (Premium / V2)

| Component | Unit Cost (1K qty) | Unit Cost (10K qty) | Notes |
|-----------|-------------------|---------------------|-------|
| NRF52810 MCU | $1.50 | $0.90 | BLE + NFC, ultra-low-power, ARM Cortex-M4 |
| NFC antenna (etched) | $0.15 | $0.08 | Copper coil |
| 2Mbit SPI flash | $0.30 | $0.18 | Stores 1000+ tap records |
| CR2016 coin cell | $0.20 | $0.12 | 3V, 90mAh, 6-month life |
| Battery holder | $0.08 | $0.05 | SMD coin cell clip |
| PCB (2-layer) | $0.40 | $0.20 | 20mm round, FR4 |
| Silicone strap | $0.60 | $0.35 | Same as Option A |
| Waterproof housing | $0.50 | $0.30 | IP67, injection-molded |
| Custom printing | $0.15 | $0.08 | |
| LED indicator | $0.05 | $0.03 | RGB status LED |
| Packaging | $0.50 | $0.30 | Premium branded box |
| Assembly + firmware flash | $0.80 | $0.50 | SMT assembly + programming |
| **TOTAL BOM** | **$5.23** | **$3.09** | |

---

## Landed Cost (Shipped to US Warehouse)

| Cost Item | Option A (1K) | Option A (10K) | Option B (1K) | Option B (10K) |
|-----------|--------------|----------------|--------------|----------------|
| BOM | $2.00 | $1.20 | $5.23 | $3.09 |
| Shipping (sea freight) | $0.40 | $0.25 | $0.50 | $0.30 |
| Import duty (~3.5%) | $0.07 | $0.04 | $0.18 | $0.11 |
| QC/testing | $0.15 | $0.08 | $0.25 | $0.15 |
| **Landed cost** | **$2.62** | **$1.57** | **$6.16** | **$3.65** |

---

## Margin Analysis (Retail $29.99)

| | Option A (1K) | Option A (10K) | Option B (1K) | Option B (10K) |
|--|--------------|----------------|--------------|----------------|
| Landed cost | $2.62 | $1.57 | $6.16 | $3.65 |
| Fulfillment (pick/pack/ship) | $3.50 | $3.00 | $3.50 | $3.00 |
| Payment processing (3%) | $0.90 | $0.90 | $0.90 | $0.90 |
| Customer support allocation | $0.50 | $0.50 | $0.50 | $0.50 |
| Returns/warranty (5%) | $1.50 | $1.50 | $1.50 | $1.50 |
| **Total COGS** | **$9.02** | **$7.47** | **$12.56** | **$9.55** |
| **Gross Profit** | **$20.97** | **$22.52** | **$17.43** | **$20.44** |
| **Gross Margin** | **69.9%** | **75.1%** | **58.1%** | **68.2%** |

---

## Manufacturing Partners (China)

### Recommended Suppliers
1. **CXJ RFID (rfidsilicone.com)** — 20+ years, OEM/ODM, custom silicone RFID bands, MOQ 500
2. **Shenzhen Chuangxinjia** — NFC wristbands, tags, cards. ISO certified.
3. **Alibaba verified suppliers** — Search "custom NFC silicone wristband" (look for Gold Supplier + Trade Assurance)

### Manufacturing Timeline
| Phase | Duration | Notes |
|-------|----------|-------|
| Sample design | 1-2 weeks | Send specs, get 3D renders |
| Prototype | 2-3 weeks | 5-10 samples for testing |
| Mold creation | 2-3 weeks | Custom strap mold (one-time $500-1500) |
| Production (1K) | 2-3 weeks | After mold approval |
| Shipping (sea) | 3-4 weeks | To US warehouse |
| **Total lead time** | **10-15 weeks** | First batch |

### One-Time Costs
| Item | Cost | Notes |
|------|------|-------|
| Custom mold (strap) | $500-1,500 | Reusable for all future runs |
| Custom mold (housing) | $300-800 | For chip module |
| Artwork/design files | $0 | We provide |
| Sample run | $100-200 | 5-10 units |
| **Total tooling** | **$900-2,500** | One-time |

---

## Launch Strategy

### Phase 1: MVP (Option A) — Month 1-3
- **Order:** 1,000 units Option A (simple NFC)
- **Investment:** ~$2,620 (BOM) + $1,500 (tooling) = **~$4,120**
- **Revenue at sellout:** $29,990
- **Gross profit:** ~$20,970
- **Go-to-market:** Pre-orders via cybrfrndz.com waitlist, school demos
- **Companion:** Free app (reads NFC, manages RP, room designer)

### Phase 2: Scale (Option A) — Month 4-6
- **Order:** 10,000 units
- **Investment:** ~$15,700
- **Revenue:** $299,900
- **Gross profit:** ~$225,200
- **Channels:** Amazon, school partnerships, retail

### Phase 3: Premium (Option B) — Month 6-12
- **Order:** 5,000 units Option B (active, band-to-band)
- **Investment:** ~$18,250
- **Revenue:** $149,950 (or raise price to $39.99 = $199,950)
- **Marketing:** "Now with REAL band-to-band tapping!"

---

## School Bulk Pricing

| Quantity | Price/Band | Discount |
|----------|-----------|----------|
| 1-49 | $29.99 | — |
| 50-199 | $24.99 | 17% off |
| 200-499 | $19.99 | 33% off |
| 500+ | $14.99 | 50% off |

At $14.99 with Option A at scale, margin is still **$13.42/unit (89.5%)** — school deals are pure profit.

---

## 6 Color SKUs

1. **Neon Blue** (cyan) — default
2. **Hot Pink** (magenta)
3. **Matrix Green**
4. **Ultraviolet** (purple)
5. **Electric Gold** (yellow)
6. **Cyber Coral** (pink)

Same mold, different silicone pigment — no extra tooling cost per color.

---

## Key Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Kids lose bands | $29.99 replacement, parent can deactivate lost band |
| Band-to-band not possible (Option A) | Kiosk/phone tap model, upgrade path to Option B |
| NFC chip failure | NTAG216 is battle-tested, <0.1% failure rate |
| Skin allergies | Medical-grade silicone, hypoallergenic, CPSIA compliant |
| Counterfeits | Unique encrypted IDs, server-side validation |
| COPPA compliance | No PII on band, parent consent required for account |

---

## Regulatory

- **CPSIA** (Children's Product Safety) — required for US kids products
- **FCC Part 15** — NFC is low-power, typically exempt or self-certified
- **CE marking** — for EU sales
- Testing cost: ~$1,000-2,000 for CPSIA + FCC (one-time)
