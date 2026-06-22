# Assembly

## Table of Contents
1. [Parts & Fit](#4-assembly--parts--fit)
2. [Carbon Fiber Tubes](#5-assembly--carbon-fiber-tubes)

## 1. Parts & Fit

### Fuselage segments too big for printer bed

**Problem:** Fuselage segments won't fit on the printer.

**Fix:** Split files are available. As described in the user manual, fuselage segments are available as whole sections AND split into left and right sides. Check the `FUSELAGE > R,L` folder in the file download.

---

### FUS ROOT glued to wrong part

**Problem:** FUS ROOT pieces accidentally glued to the fuselage instead of the wing.

**Clarification:** For the Stallion, FUS ROOT goes to the fuselage and WING ROOT goes to the wing (see manual pages 35 and 47). For the Talon, roots appear on both fuselage and wing in the instructions — check your specific model. Doubling up (gluing a root to both parts) can work and adds structural support for M6 bolts.

---

### Control horn placement direction

**Problem:** Unsure which way to orient control horns.

**Answer:** The straight edge of the control horn should be in line with the edge of the control surface. Holes should face toward the servo. 
**Tip:** Use hot glue instead of CA to attach control horns — easier to replace if they break without destroying the control surface.

---

### Servo won't fit in elevator slot — cable gets bent

**Problem:** Elevator servo can't be installed because the cable gets pinched.

**Fix:** Use a soldering iron at low temp (~250°C) to carefully melt a small cable notch into the plastic. Alternatively, use a small heated brass tube to make a clean hole. This is a standard technique for aftermarket modifications to printed parts.

---

### Pushrods — how to use them, do I cut them?

**Problem:** Pushrods seem too long.

**Answer:** Yes, cut the pushrods to the required length. The Z-shaped end clips into the control horn holes. 

---

### Servo deflection unequal — one side more than the other

**Problem:** Elevator at neutral is flush but has ~0.5" deflection one side and ~0.75" the other at full stroke.

**Fix:** Adjust the clocking of the servo arm forward from the 90° position. The servo arm angle at neutral is the key variable.

**Also:** In iNAV/ArduPilot you can adjust servo midpoint in the motor and output tab. Remember to enable live mode. Every servo is a few degrees off from factory — programming the neutral point is standard practice.

---

### Hinges — gap between aileron and wing

**Problem:** Nylon hinges leave a large gap between the aileron and wing surface.

**Fix:** Aim for as little gap as possible. Use thin CA/polyester sheet hinges (0.3mm) or TPU printed hinges instead of thick nylon hinges. These require no slot modification. Existing gaps can be sealed with "Blenderm" medical tape or similar modeling tape.

If needed, cut the hinges to size, to reduce gap between two parts.

**TPU hinge STL:** https://www.printables.com/model/995250-tpu-hinge-flightory-stallion

---

### Torsion springs — what to use for wing clips

**Problem:** Torsion springs with pin are hard to find.

**Community solution:** Small hair clips (bobby pins style) from dollar stores work perfectly. Look for ~1.75" barrette-style clips. Some also sourced them from Amazon.

---

### Motor screws won't tighten

**Problem:** M2 screws spin freely and won't grip the motor.

**Fix:** The motor likely uses M2.5 screws, not M2. Try M2.5 screws. Check Datasheet or contact the motor supplier to confirm correct screw size.

---

### Printed servo horn broke — glued with CA (superglue)

**Problem:** A printed servo horn snapped but is still glued in place with CA.

**Fix:** Use flush-cut nippers to carefully cut away the main body, a small drill to core out the tab, then a combination of nippers and hobby knife to surgically remove the rest. Minor damage to the surface can be repaired with CA and paint.

**Prevention:** Use hot glue for control horns instead of CA — much easier to replace.

---

### M3 threaded inserts — what size screws to use

**Problem:** Unsure what M3 screw length to use with M3x5mm OD threaded inserts.

**Answer:** The OD (outer diameter) refers to the insert's width, not the screw length. Use M3 screws long enough to pass through the part and into the insert. A set of mixed M3 lengths from Amazon works well.

---


## 2. Carbon Fiber Tubes

### What size tubes — 3 dimensions listed on Amazon

**Problem:** Carbon fiber tubes on Amazon have 3 dimensions (e.g. 8x6x500mm) — which is which?

**Answer:** The dimensions are OD x ID x Length. So 8x6x500mm = 8mm outside diameter, 6mm inside diameter, 500mm long, 2mm wall thickness. The Flightory BOM specifies OD and Length only — wall thickness doesn't matter much for this application.

---

### Where to buy carbon fiber tubes (USA)

**Recommendations:**
- **Windcatcher RC** — most recommended by community, good selection and pricing
- **ReadyMadeRC** — https://www.readymaderc.com/collections/hardware/build-hardware/carbon-fiber-strips-tubes-spars/carbon-fiber-tubes
- **Amazon** — available, buy 1m lengths and cut to size. Not always in stock.
- Buy 1000mm tubes and cut to the required length — exact lengths are not sold pre-cut.

---

### 6mm carbon rod unavailable — can I use 7mm?

**Problem:** Only 7mm carbon rods available locally.

**Fix:** Modify the hole in the STL using a slicer modifier (fastest) or import into Fusion 360 / FreeCAD and widen the hole. TinkerCAD or Meshmixer also work. This is a 30-second job with a STEP file, harder with an STL.

**Fix** For already printed parts: 
- Use a 7mm drill bit by hand (not powered) to widen the hole slightly 
- use a 7mm drill (powered), be extra carefull not to melt the plastic!
- Use a thin round file to widern the hole
- Wrap sandpaper around an object of similar/smaller diameter as the hole and ream manually

be sure to check progress in between! 

## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```



