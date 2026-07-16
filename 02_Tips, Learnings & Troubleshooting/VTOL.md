# VTOL — Hover & Transition Issues

### Stallion VTOL wobbles badly when switching back to landing/hover mode (fb)
**Problem:** Takeoff and forward flight smooth, but switching back from FBWA to hover mode at low speed causes wobbling and instability — consistently reproducible.

**Likely causes and fixes:**
- **Don't transition in stabilised mode (Angle/Horizon)** — use Acro mode for the transition
- Make sure the nose is pointed into the wind during transitions — crosswind makes it much worse
- Reduce throttle to ~75% before transitioning back to hover (less propwash beating the wings)
- Gain altitude before transitioning — at least 150–200 ft so you can recover if something goes wrong

> "Don't transition in stabilised mode (angle or horizon). Use only acro mode."

> "Take her up pretty high on your first transition — 150–200ft — so you can recover if something doesn't seem right."

---

### VTOL drifts backward after lift-off (dc)
**Problem:** After fixing motor sequence, VTOL lifts off but immediately moves backward.

**Likely cause:** Ground effect / too close to the ground causes erratic behavior. The FC is fighting the air turbulence reflecting off the surface.

**Fix:** Give it more throttle to get higher altitude quickly. Also verify tilt servos are at exactly 90° — even slight misalignment causes drift.

---

### VTOL front motors / ESCs overheating in hover (dc)
**Problem:** Front two motors and ESCs very hot after 2-minute hover. Fine in manual (fixed wing) flight.

**Likely cause:** PIDs not tuned — motors working too hard to stabilise. Over-correction in hover causes sustained high current draw.

**Fix:** Tune PIDs for hover mode (Q-Stabilize / Q-Hover). Community references Bardwell's VTOL tutorial. Start with reduced P and feed-forward values.

---

### VTOL wobbling / oscillating on pitch during hover (fb)
**Problem:** Stallion VTOL oscillates heavily on pitch in hover mode.

**Causes:**
- Wrong motor/prop direction or FC configuration — a plane trying to rotate during hover is a dead giveaway
- PID tuning needed — especially if weight is significantly different from standard build
- In iNAV 8 this was a known bug; in iNAV 9 it's more likely to be wrong PIDs or CG

---

### Stallion VTOL can't lift off — needs 100% throttle (fb)
**Likely causes (in priority order):**
1. **Wrong battery voltage for the motors** — 1300KV needs 5S–6S
2. **Too heavy** — non-foaming filament, too many walls/infill, heavy electronics
3. **ESC calibration needed** — recalibrate ESCs after changing battery
4. **Wrong props** — too small or wrong pitch for the motor/battery combination

---

### VTOL transition — tilt motors not completing 90° transition (dc)
**Problem:** After transition command, tilt motors stop at 45° instead of completing to 90°.

**Answer:** In iNAV, VTOL mode transitions are not automatic — requires a 3-position switch operating 0° (hover), 45° (transition), 90° (fixed wing). Ensure switch is configured correctly and servo travel limits allow full 90° movement.

---

### VTOL rear motor — different prop size OK? (fb)
**Question:** Can the rear motor use a different prop size than the two front motors?

**Answer:** The FC controls each motor individually to maintain level flight. If the rear motor can generate enough thrust to keep the tail up, a different prop size should work. Run it on a separate ESC so the FC can control it independently for pitch authority.

---

### Stork VTOL — 3kg total weight with ABS/ASA and CG issues (fb)
**Problem:** Stork VTOL printed in ABS/ASA reached 3kg total. To balance CG, needed a 6S 4P 21700 battery pack, which won't fit with the battery cover.

**Root cause:** Non-foaming filament is 2x+ heavier than intended. The airframe is designed for LW filament.

**Options:**
- Reprint key weight-saving parts in LW-ASA or LW-PLA
- Accept the heavier build and use a battery that fits (may sacrifice CG)
- Extend the battery compartment or design a custom mount

---

### FC vibration from VTOL motors affecting gyro/baro (fb)
**Question:** Will vibrations from VTOL props travel through wing spars to the FC?

**Answer:** Use foam/rubber dampening pads under the FC as standard practice. This is common on all multirotors. The baro is more affected by pressure changes than vibration — cover it with foam. In practice, community members haven't reported major issues mounting on spars.

## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)