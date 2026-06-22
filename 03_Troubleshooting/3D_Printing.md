# 3D Printing


## Table of Contents
1. [Filament & Settings](#1-3d-printing--filament--settings)
2. [Bed Adhesion & Warping](#2-3d-printing--bed-adhesion--warping)
3. [Print Failures & Quality Issues](#3-3d-printing--print-failures--quality-issues)




## 1. Filament & Settings

### LW-PLA heat creep causing under-extrusion

**Problem:** LW-PLA (especially pre-foamed variants) is vulnerable to heat creep. Manifests as what looks like under-extrusion and adhesion problems — the filament occasionally stops going through the nozzle before starting again.

**Fix:** Clean the hotend and replace the cooling fan. Lower-density filament is more susceptible.

---

### LW-PLA printing speed — can you go fast?

**Problem:** Wanting to print LW-PLA faster than the manufacturer recommends.

**Answer:** Stick to the manufacturer's recommendations. For most LW-PLA (eSun, Colorfabb), 30–50 mm/s is safe. Printing at 195 mm/s caused major layer adhesion failures.

**Fix:** Drop print speed to 30–50 mm/s max in your slicer's filament profile. Set "max volumetric speed" in the filament settings to around 4–6 mm³/s as an easy cap.

---

### LW-PLA stringing — is it normal?

**Problem:** Active foaming LW-PLA produces lots of strings during travel moves.

**Answer:** Yes, this is completely normal and unavoidable with foaming filaments. It cannot be fully eliminated.

**Fix:** Set seam position to "nearest" or "back" in OrcaSlicer so strings hide in less visible spots. Clean up strings after printing with a metal file, utility blade, or nail. Printing one part at a time greatly reduces cross-contamination stringing.

---

### LW-PLA oozing / continuous dripping at nozzle

**Problem:** Nozzle continuously oozes filament, making a mess.

**Answer:** This is a characteristic of active foaming filaments — it cannot be prevented.

---

### Weak walls / under-extrusion after seam

**Problem:** Walls are thin or missing right after the seam, making parts weak.

**Cause:** Travel stringing pulls filament out of the nozzle before the next wall starts.

**Fixes tried by community:**
- Turn off retraction entirely
- Add 0.6–0.7 extra prime amount
- Reduce retraction speed/length (don't eliminate it completely)
- Set seam to "random" so under-extruded spots appear in different places each layer, and the foamed material covers it
- For eSun LW-PLA on non-Bambu printers: 35 mm/s, 0.55 flow, half retraction speed/length, 0.6 extra prime
---

### Flow rate — what setting to use for active foaming LW-PLA?

**Answer:** Active foaming LW-PLA foams at 230°C+, so it expands to fill the same volume at ~50–60% flow. Setting flow to 100% makes it heavy like regular PLA — you lose the weight benefit. Typical range: 0.48–0.60. Start at 0.55 and adjust.

**Warning:** Pre-foamed filaments (Polymaker PolyLite LW, Overture Air) are NOT the same — they print at 0.95–1.00 flow, like normal PLA. Mixing up these settings is a very common mistake.

---

### LW-PLA clogged / won't extrude after sitting unused

**Problem:** eSun LW-PLA worked before but now won't come out. When it does melt, it's very liquid and brittle when cooled.

**Possible causes:** Wet filament (absorbed moisture), wrong flow settings.

**Fix:** Dry the filament first (55°C for 3–4 hours). Then check flow ratio — it should be 0.50–0.60, NOT 1.0. Foaming filament that is too wet behaves erratically.

---

### Best LW-PLA brand recommendations

**Community consensus:**
- **Active foaming (recommended):** eSun LW-PLA, Colorfabb LW-PLA, Bambu PLA Aero — all three are comparable in print quality and weight. eSun is most economical if bought in multipacks from their store.
- **Pre-foamed (NOT recommended):** Polymaker PolyLite LW, Overture Air PLA — heavier, prints like regular PLA, no real weight benefit.
- **LW-ASA:** Colorfabb LW-ASA / Bambu ASA Aero — better UV and heat resistance than LW-PLA. Requires sealed enclosure and carbon filter (fumes are toxic). Hardens significantly with acrylic/enamel paint.

---

### Can I print in regular PLA, ABS, or PETG?

**Answer:** You can, but it will be 1.5–2x heavier. With standard PLA the plane is likely unflyable as a VTOL, and harder to hand-launch as a fixed wing. PETG is not recommended. PLA-CF adds weight without sufficient benefit for this application.

---

### Cooling settings for LW-PLA vs LW-ASA
- **LW-PLA:** Needs lots of cooling. Run with doors open / lid off. Fan at 35–100%.
- **LW-ASA:** Needs a sealed enclosure, very little cooling (~25% max). Zero cooling causes poor layer adhesion. DO NOT open the enclosure while printing. (toxic fumes)
---

### Bambu ASA Aero — top surface tearing/rough finish

**Problem:** Top layers look rough or torn, especially on wing surfaces.

**Fixes:**
- Increase top layer count to 3–5 layers
- Increase fan speed slightly for overhangs
- Reduce top surface speed by ~10 mm/s
- Disable ironing (re-melting makes it worse)
- Rotate top layer angle (in OrcaSlicer) to shorten bridge spans
- Sand flush after printing — ASA-LW is very easy to sand
---

### Bambu ASA Aero — wall generator setting

**Problem:** Some parts (especially Lark boom mount) show gaps or missing walls.

**Fix:** Change wall generator to **Arachne** in slicer settings, and set slice gap radius to 0.

---

### Printing multiple parts at once
**Warning:** For LW-PLA/ASA, print one part at a time. Printing multiple parts causes stringing between objects, material loss when hopping between surfaces, and thin walls or gaps around seams. Single parts also avoid collision spaghetti if one part detaches.

---


## 2. Bed Adhesion & Warping

### Parts detaching mid-print / wobbling

**Problem:** Parts start fine but detach from the bed mid-print, causing spaghetti on later layers.

**Fixes:**
- Use a 5–8 mm brim with **zero brim gap** (the gap defeats the purpose)
- Apply glue stick to the print bed before each print — cheap paper glue sticks work fine
- Clean the plate with dawn dish soap and hot water between prints
- Smooth PEI plate + thin glue stick layer = most reliable combination
---

### ASA / LW-ASA warping / corners lifting

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

### Part warping — minor corner dip

**Problem:** A small corner of a fuselage section dipped/warped slightly.

**Fix:** Minor warping can be filed down on the outer portion before joining. If severe, reprint. Can also fill with body filler (Bondo Glazing & Spot Putty or German equivalent polyester filler like Presto) and sand.

---


## 3.Print Failures & Quality Issues

### Print fails at ~87% every time (fuselage parts)

**Problem:** Dreamer NX printer with Flashprint slicer — prints stop at the same point with "print file error."

**Possible causes / fixes:**
- Check SD card health or try a different card
- If printing via USB, ensure the computer doesn't go to sleep during the print
- Check STL files for non-manifold edges (Windows 3D Viewer can auto-fix these)

---

### Z-seam causing problems with carbon tube holes

**Problem:** A large Z-seam runs down every hole for carbon fiber tubes. Nothing fits — tubes broke three parts trying to force them in.

**Fix:** Use a long drill bit to drill through the holes with the correct diameter (4 mm, 6 mm, 10 mm) to clean out the seam material. Alternatively, wrap sandpaper around a tube the same size and ream it by hand. Do not use the drill spinning or the plastic may melt.

---

### Carbon fiber tube holes too tight

**Problem:** Carbon fiber tubes won't go into the printed holes.

**Fixes:**
- Use the correct drill bit by hand (not powered) to widen the hole slightly
- Wrap sandpaper around a tube of the same diameter and ream manually
- Clean out any residue or print debris from inside the hole
- **Do NOT** attach the rod to a drill and push it in while spinning — the friction can melt the plastic and permanently fuse the rod halfway in

---

### Printing hatch parts — sways / wobbles during print

**Problem:** Hatch pieces wobble during printing, causing poor quality on upper layers.

**Fix:** Use a brim and try turning off the fans. For tall, thin parts: print the split versions to halve the height. Reduce travel speed to minimise kinetic energy being thrown around by the print head.

---

### Wings not aligning / misaligned print layers

**Problem:** After printing, wing sections don't align to each other.

**Fixes:**
- Use a brim without gap spacing
- Use bed adhesive
- If printer is enclosed, turn off chamber fan
- If printer is open, put it somewhere warm
- Higher bed temperature
- Dry the filament — wet filament can contribute to warping/misalignment

---

### Under-extrusion holes in parts — should I worry?

**Problem:** Printed parts show small holes from under-extrusion.

**Fix:** Adjust flow rate upward slightly (e.g., 0.98 → 1.20 flow ratio) to eliminate gaps. For small holes that remain: lightweight automotive body filler (Bondo Glazing & Spot Putty) works well. Don't worry about reprinting until you know the plane won't crash — epoxy/filler is enough for a first flight.

---

### Part orientation — how to orient for printing
**Always check the manual for recommended print orientation.** Wrong orientation is a common cause of print failures and weak parts. Example: Talon 1400 hatch piece failed until oriented correctly per the manual.

---

### Klipper / BLTouch Z-offset keeps resetting

**Problem:** On Ender 3V3 SE with Klipper, BLTouch keeps resetting Z-offset.

**Partial fix reported:** Save the Z-offset value directly to the config file. Community didn't have a complete solution — check Klipper forums for BLTouch-specific config.



## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```


