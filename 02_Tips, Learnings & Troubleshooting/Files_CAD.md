# Files, Slicers & Printer Compatibility

### Do Flightory STL files import directly into Bambu Studio? (fb)
**Yes** — STL files open in Bambu Studio like any other STL. You slice them yourself using the recommended settings profile (downloadable from Flightory's print settings page). It is NOT automatic like Bambu's own ecosystem files.

---

### What file formats does Flightory provide? (dc)
**Answer:** Most parts are STL files. STEP files are available for some parts (primarily fuselage sections for Stallion). Wing parts are STL only. For full CAD assemblies, contact Flightory directly via email — they may be able to provide additional STEP files on request.

---

### STEP files not importing into Fusion 360 (dc)
**Fix:** Use "Insert Component" (not "Import"). This allows importing multiple STEP files into one assembly. Confirmed working with Flightory STEP files.

**Alternative:** FreeCAD can also import STEP files.

---

### Modifying STL files to change hole dimensions (dc)
**Options (easiest to hardest):**
1. **Slicer modifier** (Bambu Studio / OrcaSlicer) — add a modifier object over the hole, fastest method
2. **TinkerCAD / Meshmixer** — free, no-code, browser-based
3. **Fusion 360** — import as mesh, convert to body
4. **FreeCAD** — reliable for STEP and STL
5. **Solidworks** — possible but STLs are difficult; use STEP files where available

---

### Printer requirements — minimum bed size (fb)
Most Flightory fuselage and wing parts require at least a **220x220mm** bed. Some larger parts (wing halves on larger models) need 256x256mm or bigger. Always check part dimensions in the slicer before starting a print run.

---

### A1 Mini — can it print Stallion VTOL parts? (fb)
**Answer:** Most parts will NOT fit on the A1 Mini (180x180mm build plate). You would need to break parts down into smaller sections, which the files don't always support by default. A larger printer (P1S, X1C, or similar 256mm+ plate) is strongly recommended.

---

### Stallion VTOL — do I need both the base and VTOL files? (dc)
**Answer:** Yes. The VTOL pack is an extension — it does not include all parts needed to print the complete aircraft. You need:
1. Stallion base model files
2. Stallion VTOL extension files

---

### Is there a BOM with file descriptions for the Stallion? (fb)
**Answer:** The manual and website provide a parts list, but mapping every file to the build can be tricky from filename and folder structure alone. The community recommends going through the manual page by page and matching parts as you assemble. For VTOL, the VTOL extension pack changes which motor mounts and boom parts you need — cross-reference both manuals.

## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)