# Files & CAD - STL / STEP Modifications

---

### STEP files not importing into Fusion 360

**Fix:** Use "Insert Component" (not "Import"). This allows importing multiple STEP files into one assembly. Confirmed working with Flightory STEP files.

**Alternative:** FreeCAD can also import STEP files.

---

### What file formats does Flightory provide?

**Answer:** Most parts are STL files. STEP files are available for some parts (primarily fuselage sections for Stallion). Wing parts are STL only. For full CAD assemblies, contact Flightory directly via email — they may be able to provide additional STEP files on request.

---

### Stallion VTOL — do I need both the base and VTOL files?

**Answer:** Yes. The VTOL pack is an extension — it does not include all parts needed to print the complete aircraft. You need:
1. Stallion base model files
2. Stallion VTOL extension files

---

### Modifying STL files to change hole dimensions
**Options (easiest to hardest):**
1. **Slicer modifier** (Bambu Studio / OrcaSlicer) — add a modifier object over the hole, fastest method
2. **TinkerCAD / Meshmixer** — free, no-code, browser-based
3. **Fusion 360** — import as mesh, convert to body
4. **FreeCAD** — reliable for STEP and STL
5. **Solidworks** — possible but STLs are difficult; use STEP files where available


## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```
