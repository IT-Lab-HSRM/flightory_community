# 3D Printing 

## Table of Contents
1. [Filament Choice & Settings](#1-filament-choice--settings)
2. [Bed Adhesion, Warping & Surface Finish](#2-bed-adhesion-warping--surface-finish)
3. [Print Failures & Quality Issues](#3-print-failures--quality-issues)
4. [Painting & Protecting Prints](#4-painting--protecting-prints)
5. [Wall Count and Infill](#5-wall-count--infill)

---

## 1. Filament Choice & Settings

### Active foaming vs pre-foamed LW-PLA — what's the difference? (fb)
**This is one of the most common points of confusion in the community.**
- **Active foaming** (eSun ePLA-LW, Colorfabb LW-PLA, Bambu PLA Aero): expands at high temperature (~230°C+). Print at 50–60% flow ratio. Much lighter than regular PLA — the whole point of using it.
- **Pre-foamed** (Polymaker PolyLite LW, Overture Air): comes pre-expanded. Prints like regular PLA at ~95–100% flow. **Not meaningfully lighter** — the community consistently reports poor results and excessive weight.

> "Foaming LW-PLA is very good and surprisingly strong when dialed in. And much lighter than Polymaker." 
> 
> "Polymaker LW-PLA is not really lightweight. It's lighter than PLA but far from a foaming LW-PLA like Bambu Aero or eSun LW-PLA with foaming agent."

**Recommendation:** Use an active foaming filament. Dry it before printing — moisture significantly affects these filaments. 1 day in a dryer is ideal; 3–4 hours at 55°C as a minimum.

---

### Flow rate — what setting to use for active foaming LW-PLA? (dc)
**Answer:** Active foaming LW-PLA foams at 230°C+, so it expands to fill the same volume at ~50–60% flow. Setting flow to 100% makes it heavy like regular PLA — you lose the weight benefit. Typical range: 0.48–0.60. Start at 0.55 and adjust.

**Warning:** Pre-foamed filaments (Polymaker PolyLite LW, Overture Air) are NOT the same — they print at 0.95–1.00 flow, like normal PLA. Mixing up these settings is a very common mistake.

---

### LW-PLA heat creep causing under-extrusion (dc)
**Problem:** LW-PLA (especially pre-foamed variants) is vulnerable to heat creep. Manifests as what looks like under-extrusion and adhesion problems — the filament occasionally stops going through the nozzle before starting again.

**Fix:** Clean the hotend and replace the cooling fan. Lower-density filament is more susceptible.

---

### LW-PLA printing speed — can you go fast? (dc)
**Problem:** Wanting to print LW-PLA faster than the manufacturer recommends.

**Answer:** Stick to the manufacturer's recommendations. For most LW-PLA (eSun, Colorfabb), 30–50 mm/s is safe. Printing at 195 mm/s caused major layer adhesion failures.

**Fix:** Drop print speed to 30–50 mm/s max in your slicer's filament profile. Set "max volumetric speed" in the filament settings to around 4–6 mm³/s as an easy cap.

---

### LW-PLA stringing — is it normal? (dc) (fb)
**Problem:** Active foaming LW-PLA produces lots of strings during travel moves.

**Answer:** Yes, this is completely normal and unavoidable with foaming filaments. It cannot be fully eliminated. It has a distinct look, smell, and feel.

**Fix (dc):** Set seam position to "nearest" or "back" in OrcaSlicer so strings hide in less visible spots. Clean up strings after printing with a metal file, utility blade, or nail. Printing one part at a time greatly reduces cross-contamination stringing.

**Post-processing (fb):** Use a nail, fine file, or hobby knife to clean strings. They come off easily and most interior strings don't matter structurally.

---

### LW-PLA oozing / continuous dripping at nozzle (dc)
**Problem:** Nozzle continuously oozes filament, making a mess.

**Answer:** This is a characteristic of active foaming filaments — it cannot be prevented.

---

### Weak walls / under-extrusion after seam (dc)
**Problem:** Walls are thin or missing right after the seam, making parts weak.

**Cause:** Travel stringing pulls filament out of the nozzle before the next wall starts.

**Fixes tried by community:**
- Turn off retraction entirely
- Add 0.6–0.7 extra prime amount
- Reduce retraction speed/length (don't eliminate it completely)
- Set seam to "random" so under-extruded spots appear in different places each layer, and the foamed material covers it
- For eSun LW-PLA on non-Bambu printers: 35 mm/s, 0.55 flow, half retraction speed/length, 0.6 extra prime

---

### LW-PLA clogged / won't extrude after sitting unused (dc)
**Problem:** eSun LW-PLA worked before but now won't come out. When it does melt, it's very liquid and brittle when cooled.

**Possible causes:** Wet filament (absorbed moisture), wrong flow settings.

**Fix:** Dry the filament first (55°C for 3–4 hours). Then check flow ratio — it should be 0.50–0.60, NOT 1.0. Foaming filament that is too wet behaves erratically.

---

### Best LW-PLA brand recommendations (dc)
**Community consensus:**
- **Active foaming (recommended):** eSun LW-PLA, Colorfabb LW-PLA, Bambu PLA Aero — all three are comparable in print quality and weight. eSun is most economical if bought in multipacks from their store.
- **Pre-foamed (NOT recommended):** Polymaker PolyLite LW, Overture Air PLA — heavier, prints like regular PLA, no real weight benefit.
- **LW-ASA:** Colorfabb LW-ASA / Bambu ASA Aero — better UV and heat resistance than LW-PLA. Requires sealed enclosure and carbon filter (fumes are toxic). Hardens significantly with acrylic/enamel paint.

---

### LW-PLA heat sensitivity — will it melt in the sun? (fb)
**Problem:** Polylight LW-PLA wings deformed (dimples, concave spots) after being left outside in Texas summer heat (32–43°C / 90–110°F) for just 15 minutes.

**Solutions:**
- Switch to **LW-ASA** (Colorfabb, Bambu ASA Aero) — far better UV and heat resistance
- **Regular ASA** (non-foaming) also works — plane will be heavier but will survive heat and sun
- **Paint with white acrylic/enamel** — reduces heat absorption and helps, but does not fully solve the problem with standard LW-PLA
- Do not leave printed LW-PLA parts in direct sun, hot cars, or hot enclosed spaces

---

### Can I print in regular PLA, ABS, PETG, or CF variants? (dc) (fb)
**Answer:** Short answer: not recommended, but it can fly with adjustments.
- Regular PLA, ABS, PETG, PLA-CF, ASA-CF are typically 1.5–3x heavier than LW filament.
- With standard PLA, the plane is likely unflyable as a VTOL and harder to hand-launch as a fixed wing.
- At 3 walls + 15% infill with ASA-CF, the weight is far too high. Even with LW filaments, people use 2 walls max.

---

### Cooling settings for LW-PLA vs LW-ASA (dc)
- **LW-PLA:** Needs lots of cooling. Run with doors open / lid off. Fan at 35–100%.
- **LW-ASA:** Needs a sealed enclosure, very little cooling (~25% max). Zero cooling causes poor layer adhesion. DO NOT open the enclosure while printing (toxic fumes).

---

### LW-ASA print settings — tips from Voron/CoreXY users (fb)
**For enclosed CoreXY printers (Voron, Switchwire, Trident) printing Colorfabb LW-ASA:**
- Start at **35 mm/s** — eliminates many variables.
- ASA behaves like ABS: warps, smells toxic, doesn't like drafts — enclosure is essential.
- Goal: single-wall prints at 50–55% of the weight of a standard PLA part.
- Low temperature + double wall gives a better-looking result while learning.
- The filament should be porous and slightly softer than PLA, but should NOT feel like paper.
- Start with an out-of-the-box ASA profile, use Flightory's ASA Aero settings as a guide, then adjust flow rate.

---

### Bambu ASA Aero — top surface tearing/rough finish (dc)
**Problem:** Top layers look rough or torn, especially on wing surfaces.

**Fixes:**
- Increase top layer count to 3–5 layers
- Increase fan speed slightly for overhangs
- Reduce top surface speed by ~10 mm/s
- Disable ironing (re-melting makes it worse)
- Rotate top layer angle (in OrcaSlicer) to shorten bridge spans
- Sand flush after printing — ASA-LW is very easy to sand

---

### Bambu ASA Aero — wall generator setting (dc)
**Problem:** Some parts (especially Lark boom mount) show gaps or missing walls.

**Fix:** Change wall generator to **Arachne** in slicer settings, and set slice gap radius to 0.

---

### Print settings — presets are a starting point only (fb)
**Key community wisdom:** Successful 3D printing comes down to one thing: realizing that two identical machines running the same production job require different adjustments. Take the time to calibrate the filament for your specific machine.

**What to do:** Use Flightory's print settings page as a starting point, then tune flow rate, temperature, and speed for your specific printer and filament batch.

---

### Bambu Lab printers — using Flightory presets (fb)
- **PLA Aero and Colorfabb LW-PLA on P1S:** Flightory presets work directly with excellent results.
- **H2D:** Copy settings from X1C profile manually; adjust print temp and flow rate slightly.

Note: you receive STL files, not .3mf — you must slice them yourself, it's not automatic.

---

### Spektrum UltraFoam LW-PLA — settings guidance (fb)
**Reported settings:** 0.6 flow rate, 250°C. FUS1L came out at ~11g. Active foaming settings from Flightory's website should work as a starting point.

---

### Printing multiple parts at once (dc)
**Warning:** For LW-PLA/ASA, print one part at a time. Printing multiple parts causes stringing between objects, material loss when hopping between surfaces, and thin walls or gaps around seams. Single parts also avoid collision spaghetti if one part detaches.


## 2. Bed Adhesion, Warping & Surface Finish

### Parts detaching mid-print / wobbling (dc)
**Problem:** Parts start fine but detach from the bed mid-print, causing spaghetti on later layers.

**Fixes:**
- Use a 5–8 mm brim with **zero brim gap** (the gap defeats the purpose)
- Apply glue stick to the print bed before each print — cheap paper glue sticks work fine
- Clean the plate with dawn dish soap and hot water between prints
- Smooth PEI plate + thin glue stick layer = most reliable combination

---

### ASA / LW-ASA warping / corners lifting (dc)
**Problem:** ASA corners peel off the bed, parts warp — especially in cold rooms.

**Fixes:**
- Sealed enclosure is essential
- Bed temp at 100°C (max for Bambu P1S)
- Turn off chamber fan completely (modify start G-code)
- Use Polymaker ASA rather than Bambu ASA if you have adhesion issues
- Dry filament before printing (wet filament worsens warping)
- Large brim (10 mm) helps
- If the room temperature fluctuates a lot, try to keep the room warmer

---

### Part warping — minor corner dip (dc)
**Problem:** A small corner of a fuselage section dipped/warped slightly.

**Fix:** Minor warping can be filed down on the outer portion before joining. If severe, reprint. Can also fill with body filler (Bondo Glazing & Spot Putty or German equivalent polyester filler like Presto) and sand.

---

### ASA welding to the print plate / won't release (fb)
**Problem:** LW-ASA sticks so hard to the textured PEI plate that it tears the surface on removal.

**Fixes:**
- Apply a thin layer of **glue stick** before printing — acts as a release agent
- Let the plate **fully cool** before attempting removal — ASA releases much better cold
- Try a **smooth PEI plate** instead of textured for ASA
- Some community members use specialty adhesive spray (3DJake AdheEasy) on smooth PEI — works well but may need bed heated to 90°C post-print to release

---

### ASA-CF on Anycubic Kobra — poor results (fb)
**Problem:** ASA-CF printing poorly on Anycubic Kobra S1.

**Tip shared:** Use 3 walls + 15% infill for nose, 1 wall + 3% for fuselage, 1 wall + 7% for the bottom fuselage section where the carbon tail tube inserts.

## 3. Print Failures & Quality Issues

### Under-extrusion / voids in parts (fb)
**Causes:** Printing too fast, nozzle temperature too low, partially clogged nozzle, or using foaming settings on pre-foamed filament (or vice versa).

**Fixes:** For pre-foamed, print at ~100% flow. For active foaming, use 50–60% flow, 230–250°C, 30–50 mm/s. If too many voids remain, check if filament is dry, and increase temp by 5°C.

---

### Under-extrusion holes in parts — should I worry? (dc)
**Problem:** Printed parts show small holes from under-extrusion.

**Fix:** Adjust flow rate upward slightly (e.g., 0.98 → 1.20 flow ratio) to eliminate gaps. For small holes that remain: lightweight automotive body filler (Bondo Glazing & Spot Putty) works well. Don't worry about reprinting until you know the plane won't crash — epoxy/filler is enough for a first flight.

---

### Print slowing for overhangs then under-extruding when speed returns (fb)
**Problem:** Quality was good until the slicer slowed down for an overhang, then under-extruded when it resumed normal speed — leaving a weak band.

**Fix:** Set all speeds the same — remove variable speed for overhangs. This stopped the under-extrusion at speed transitions.

---

### Lines / ghosting above holes and cutouts (LW-ASA) (fb)
**Problem:** Wavy lines appear on wall surfaces just above where holes or cutouts rejoin.

**Fix:** This is called **ghosting** or **ringing** — caused by vibration from rapid direction changes. Reducing acceleration and jerk settings helps.

---

### Z-seam causing problems with carbon tube holes (dc)
**Problem:** A large Z-seam runs down every hole for carbon fiber tubes. Nothing fits — tubes broke three parts trying to force them in.

**Fix:** Use a long drill bit to drill through the holes with the correct diameter (4 mm, 6 mm, 10 mm) to clean out the seam material. Alternatively, wrap sandpaper around a tube the same size and ream it by hand. Do not use the drill spinning or the plastic may melt.

---

### Carbon fiber tube holes too tight / Spar holes not fully formed (dc) (fb)
**Problem:** Carbon fiber tubes won't go into the printed holes or wing spar holes are incomplete.

**Fixes:**
- Use a sharpened brass tube or correct drill bit of the correct diameter **by hand** (not powered) to clean/widen the hole slightly.
- Grind a bevel on the inside of a brass tube first to act as a cutter, or wrap sandpaper around a tube of the same diameter and ream manually.
- **Do NOT** attach the rod to a drill and push it in while spinning — the friction can melt the plastic and permanently fuse the rod halfway in.

---

### Print fails at ~87% every time (fuselage parts) (dc)
**Problem:** Dreamer NX printer with Flashprint slicer — prints stop at the same point with "print file error."

**Possible causes / fixes:** Check SD card health, prevent computer sleep if printing via USB, or check STL files for non-manifold edges (Windows 3D Viewer can auto-fix these).

---

### Printing hatch parts — sways / wobbles during print (dc)
**Problem:** Hatch pieces wobble during printing, causing poor quality on upper layers.

**Fix:** Use a brim and try turning off the fans. For tall, thin parts: print the split versions to halve the height. Reduce travel speed to minimise kinetic energy.

---

### Wings not aligning / misaligned print layers (dc)
**Problem:** After printing, wing sections don't align to each other.

**Fixes:** Use a brim without gap spacing, use bed adhesive, turn off chamber fan if enclosed, keep the printer somewhere warm if open, use a higher bed temperature, and dry the filament.

---

### Part orientation — how to orient for printing (dc)
**Always check the manual for recommended print orientation.** Wrong orientation is a common cause of print failures and weak parts.

---

### Klipper / BLTouch Z-offset keeps resetting (dc)
**Problem:** On Ender 3V3 SE with Klipper, BLTouch keeps resetting Z-offset.

**Partial fix reported:** Save the Z-offset value directly to the config file. Check Klipper forums for BLTouch-specific config.

---

### Creality K1C — no good LW-PLA preset in Creality Print (fb)
**Problem:** Creality Print doesn't have a dedicated LW-PLA preset; results are very poor.

**Fix:** Use **OrcaSlicer** instead — it has better LW filament support. Or manually create a profile based on Flightory's recommended settings.

---

### CF filament too brittle / breaking in extruder (fb)
**Problem:** CF filament breaks in the extruder before printing.

**Main cause:** Moisture. Dry the filament thoroughly before printing (55–65°C for 4+ hours).


## 4. Painting & Protecting Prints

### Can LW-PLA parts be painted without adding too much weight? (fb)
**Yes — lightly.**
> "Anything works on LW-PLA and LW-ASA — it's like canvas. It is chemically stable so most paints will not affect it."

**Lightweight options:**
- **Cerakote** — goes on very thin, minimal weight added, very durable.
- **Water-based spray paint** — one coat is sufficient (e.g., Blick water-based spray used on Moose: "matte finish is beautiful").
- **Acrylic enamel spray** — strengthens surface significantly, good UV protection.
- **High-pigment paints** — use less product to achieve coverage.

**Tip for finishing:** Sand parts smooth first to reduce the amount of paint needed for coverage.
> "Paint and filler add quite a bit of weight. Your best bet is sanding the parts smooth and then using a high-pigment paint to reduce the amount you need."

---

### What acrylic filler primer works in the USA? (fb)
**Community suggestions:**
- Any acrylic-based filler primer works — look for lightweight sandable primer spray cans.
- Sand to smooth first, then apply a thin coat of primer before painting.
- Rust-Oleum acrylic enamel and Duplicolor are both community-confirmed options.

---

### Will paint protect LW-PLA from melting in the sun? (fb)
**Partial fix only.** White or light-coloured paint helps by reflecting heat. But standard LW-PLA will still soften in sustained direct sun exposure even when painted. For reliable heat resistance, switch to LW-ASA or LW-PLA-HT.

## 5. Wall Count & Infill

### Recommended wall count and infill (fb)
**Community consensus for LW filaments:**
- **Walls:** 1 wall for main airframe (wings, fuselage). 2 walls for reinforced areas. 3 walls makes parts noticeably stronger but significantly heavier.
- **Infill:** 3–7% gyroid or similar. Use 15% only for small structural parts (nose, mounts).
- **Top/bottom layers:** 2 standard, up to 3–5 if surface quality is poor.

> "3 walls 15% infill with ASA-CF is way too much weight. Even with LW filaments, people use 2 walls max."


## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)
