# Components

## Table of Contents
1. [Component Choices & Optimisations](#1-Component-Choices--Optimisations)
2. [Sourcing & Alternatives](#2-Sourcing--Alternatives)

## 1. Component Choices & Optimisations

### Motors — upgraded for payload capacity (hsrm) 
Standard recommendation is Emax ECOII 2807 1300KV or T-Motor F90 1300KV. The HSRM team used more powerful motors: +23.4 g per unit but +621.9 W power each. The additional current draw is compensated by an upgraded battery.

**Note:** Higher-KV or higher-power motors require matching ESC current ratings and a higher-capacity battery. Check motor/prop thrust tables against your expected AUW before committing.

---

### Props — 8" 3-blade instead of 7" 2-blade (hsrm) 
**Why:** Three blades give better stability under load (important when carrying cargo), and the larger diameter adds thrust. The slight drag increase is negligible against the thrust gain.

**Consideration:** Larger props need more ground clearance and may require minor boom geometry changes depending on your build.

---

### ESC — 4-in-1 saves weight and space (hsrm) 
A 4-in-1 ESC is noticeably more compact than three individual ESCs and simplifies the wiring harness significantly. Worth it on a build where fuselage space and weight are both constrained.

**Note:** A 4-in-1 ESC current rating is per channel (per motor), not total. A 50A 4-in-1 on a 3-motor VTOL = 150A total capacity.

---

### Battery — upgraded for payload and flight time (hsrm) 
Standard: 4S Li-Ion max 4S3P 10.5 Ah. HSRM build: +90 g but +2,200 mAh capacity and +20C discharge rate.

**Tradeoff:** Heavier battery compensates for heavier motors and props while maintaining flight time. If not carrying payload, the standard battery is the better choice for AUW.

---

### Build time estimate (hsrm) 
For four people working in parallel across CAD modification, printing, assembly, electronics, and programming: allow significantly more time than the build guide implies, especially if:
- Any parts need CAD modification
- You encounter connector incompatibilities (likely)
- Firmware issues arise (likely)
- Any parts need reprinting

> "This was a genuinely challenging project that pushed us in directions we didn't expect."

## 2. Sourcing & Alternatives

### GPS alternatives (Matek M10Q-5883 out of stock)

**Recommendations:**
- Look for any **M10** chipset GPS (current generation, faster acquisition than older M8) with **QMC5883L or 5883** compass
- FlyFishRC Positioning M10QMC-5-8-83L Module (Amazon)
- SEQURE QMC5883L 10th Generation (Amazon)
- https://rotorriot.com/products/m10q-5883-gnss-gps-compass-module
---

### CA glue — thin vs medium vs thick
**Question:** Parts list says thin CA but links to medium.

**Community consensus:** Any CA viscosity works. Thin penetrates gaps well. Medium and thick give more working time and fill small gaps. Multiple community members successfully use thick CA.

---

### Print bed surface options
**Community recommendations:**
- **Smooth PEI + glue stick** — most recommended for LW-PLA
- **Textured PEI** — works for LW-ASA but releases poorly; needs glue stick or specialty adhesive spray
- **Adhesive spray** (3DJake AdheEasy) — strong adhesion, sometimes too strong — heat bed to 90°C after print to release
- **Painters tape on smooth PEI** — also works well

---

### Battery options — Li-ion vs LiPo
**Community advice:**
- Start with **LiPo** — known behavior, easy to find quality cells
- Li-ion offers longer flight times but has lower burst current — risky on high-draw VTOL builds
- Pre-made Li-ion packs from AliExpress frequently lie about capacity — DIY is the way if you want Li-ion
- Quality cell source: **nkon.nl** (Europe) — honest specs, competitive pricing for Samsung, EVE cells

---

### Painting / protecting LW-PLA parts

**Recommendations:**
- **Acrylic spray paint** — any acrylic will harden and strengthen the surface
- **Enamel spray** — stronger hardening effect than acrylic
- **Epoxy enamel** (e.g., Duplicolor, Rust-Oleum acrylic enamel) — best protection, also helps with UV resistance for outdoor flying
- Do NOT let the plane sit in direct sunlight — LW-PLA softens in heat


## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (hsrm) **Own personal experience** Made during Wintersemester 24/25 (HochschuleRheinMain)

