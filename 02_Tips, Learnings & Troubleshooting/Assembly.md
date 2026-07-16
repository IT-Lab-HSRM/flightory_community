# Assembly

## Table of Contents
1. [Parts & Fit](#1-parts--fit)
2. [Carbon Fiber Tubes & Holes](#2-carbon-fiber-tubes--holes)
3. [Weight & Build Tips](#3-weight--build-tips)


## 1. Parts & Fit

### Fuselage segments too big for printer bed (dc)
**Problem:** Fuselage segments won't fit on the printer.

**Fix:** Split files are available. As described in the user manual, fuselage segments are available as whole sections AND split into left and right sides. Check the `FUSELAGE > R,L` folder in the file download.

---

### FUS ROOT glued to wrong part (dc)
**Problem:** FUS ROOT pieces accidentally glued to the fuselage instead of the wing.

**Clarification:** For the Stallion, FUS ROOT goes to the fuselage and WING ROOT goes to the wing (see manual pages 35 and 47). For the Talon, roots appear on both fuselage and wing in the instructions — check your specific model. Doubling up (gluing a root to both parts) can work and adds structural support for M6 bolts.

---

### Control horn placement direction (dc)
**Problem:** Unsure which way to orient control horns.

**Answer:** The straight edge of the control horn should be in line with the edge of the control surface. Holes should face toward the servo. 

**Tip:** Use hot glue instead of CA to attach control horns — easier to replace if they break without destroying the control surface.

---

### Servo won't fit in elevator slot — cable gets bent (dc)
**Problem:** Elevator servo can't be installed because the cable gets pinched.

**Fix:** Use a soldering iron at low temp (~250°C) to carefully melt a small cable notch into the plastic. Alternatively, use a small heated brass tube to make a clean hole. This is a standard technique for aftermarket modifications to printed parts.

---

### Pushrods — how to use them, do I cut them? (dc)
**Problem:** Pushrods seem too long.

**Answer:** Yes, cut the pushrods to the required length. The Z-shaped end clips into the control horn holes. 

---

### Servo deflection unequal — one side more than the other (dc)
**Problem:** Elevator at neutral is flush but has ~0.5" deflection one side and ~0.75" the other at full stroke.

**Fix:** Adjust the clocking of the servo arm forward from the 90° position. The servo arm angle at neutral is the key variable.

**Also:** In iNAV/ArduPilot you can adjust servo midpoint in the motor and output tab. Remember to enable live mode. Every servo is a few degrees off from factory — programming the neutral point is standard practice.

---

### Hinges — gap between aileron and wing (dc)
**Problem:** Nylon hinges leave a large gap between the aileron and wing surface.

**Fix:** Aim for as little gap as possible. Use thin CA/polyester sheet hinges (0.3mm) or TPU printed hinges instead of thick nylon hinges. These require no slot modification. Existing gaps can be sealed with "Blenderm" medical tape or similar modeling tape. If needed, cut the hinges to size to reduce the gap between two parts.

**TPU hinge STL:** https://www.printables.com/model/995250-tpu-hinge-flightory-stallion

---

### Torsion springs — what to use for wing clips (dc)
**Problem:** Torsion springs with pin are hard to find.

**Community solution:** Small hair clips (bobby pins style) from dollar stores work perfectly. Look for ~1.75" barrette-style clips. Some also sourced them from Amazon.

---

### Motor screws won't tighten (dc)
**Problem:** M2 screws spin freely and won't grip the motor.

**Fix:** The motor likely uses M2.5 screws, not M2. Try M2.5 screws. Check Datasheet or contact the motor supplier to confirm correct screw size.

---

### Printed servo horn broke — glued with CA (superglue) (dc)
**Problem:** A printed servo horn snapped but is still glued in place with CA.

**Fix:** Use flush-cut nippers to carefully cut away the main body, a small drill to core out the tab, then a combination of nippers and hobby knife to surgically remove the rest. Minor damage to the surface can be repaired with CA and paint.

**Prevention:** Use hot glue for control horns instead of CA — much easier to replace.

---

### M3 threaded inserts — what size screws to use (dc)
**Problem:** Unsure what M3 screw length to use with M3x5mm OD threaded inserts.

**Answer:** The OD (outer diameter) refers to the insert's width, not the screw length. Use M3 screws long enough to pass through the part and into the insert. A set of mixed M3 lengths from Amazon works well.

## 2. Carbon Fiber Tubes & Holes

### Carbon fiber tubes won't go into the holes / Spar holes too tight (dc) (fb)
**This is one of the most frequently reported assembly issues.**

**Fixes (in order of preference):**
1. Use a **sharpened brass tube** of the correct diameter as a hand reamer — grind a bevel on the inside edge and use it manually or in a drill motor to clear the hole.
2. Use a **long drill bit** of the correct diameter **by hand** (not powered) — cleans out the Z-seam or print debris that often blocks the hole.
3. Use a thin round file or wrap sandpaper around an object of similar/smaller diameter as the hole and ream manually. Check progress frequently!
4. **PTFE / Teflon lubricant spray** — helps tubes slide through tight holes without damaging plastic.
5. **KY Jelly** — community-suggested lubricant, dries with little residue, doesn't attack plastic.

> "I used an appropriate sized brass tube, sharpened it by grinding a bevel on the inside diameter, and used it in a drill motor to clean out the holes. Worked perfect."

**Do NOT:** Spin the carbon rod in a powered drill into the hole — the friction and heat can melt the plastic and permanently fuse the rod halfway in place.

---

### What size tubes / Carbon tube dimensions explained (dc) (fb)
**Problem/Question:** Carbon fiber tubes on Amazon or the BOM have multiple dimensions listed (e.g. 8x6x500mm or just 8x500mm) — which is which?

**Answer:** The dimensions refer to **OD (outer diameter) x ID (inner diameter) x Length**. 
- The Flightory BOM typically specifies OD and Length only (e.g., 8x500mm means 8mm OD, 500mm long). 
- Inner diameter and wall thickness are not specified because they do not affect the outer fit — either wall thickness works fine for this application.
- Exact pre-cut lengths are not usually sold; buy 1000mm (1m) tubes and cut them to size.

---

### 6mm carbon rod unavailable — can I use 7mm? (dc)
**Problem:** Only 7mm carbon rods available locally.

**Fix:** Modify the hole in the STL using a slicer modifier (fastest) or import into Fusion 360 / FreeCAD and widen the hole. TinkerCAD or Meshmixer also work. This is a 30-second job with a STEP file, harder with an STL.

**Fix for already printed parts:** Use a 7mm drill bit by hand (not powered), use a thin round file, or use a powered 7mm drill with extra care not to melt the plastic.

---

### Where to buy carbon fiber tubes (USA) (dc)
**Recommendations:**
- **Windcatcher RC** — most recommended by community, good selection and pricing
- **ReadyMadeRC** — https://www.readymaderc.com/collections/hardware/build-hardware/carbon-fiber-strips-tubes-spars/carbon-fiber-tubes
- **Amazon** — available, buy 1m lengths and cut to size. Not always in stock.

## 3. Weight & Build Tips

### What AUW (all-up weight) should I target? (fb)
**Reference weights shared by community:**

| Build | Weight (without battery) | Notes |
|---|---|---|
| Stingray VTOL (Bambu LW-PLA + PETG) | ~876g (printed parts only) | Reasonable |
| Stallion VTOL (LW-PLA/LW-ASA) | ~1,400–1,500g | Standard build |
| Stallion VTOL RTF with 6S 3300mAh | ~2,030g | Flown successfully |
| Stallion VTOL (PETG) | ~2,603g | Too heavy, marginal flight |
| Stork VTOL (ABS/ASA, non-foaming) | ~3,000g | Very heavy, CG problems |

> "If you lift off [in hover] and throttle is over 60–70%, you are in too heavy an area."

---

### Stallion VTOL — FC mount vibration concern (fb)
**Question:** Will vibrations from VTOL pods travel through the wing spars to the FC and affect barometer/gyro?

**Community answer:** This is a valid concern but in practice people mount directly on spars without reported gyro issues. Use foam dampening pads under the FC as standard practice. The bigger risk is electromagnetic interference from ESC wiring — keep power wires away from FC and GPS.


## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)
