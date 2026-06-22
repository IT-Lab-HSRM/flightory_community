# VTOL — Hover & Transition Issues

---

### VTOL drifts backward after lift-off

**Problem:** After fixing motor sequence, VTOL lifts off but immediately moves backward.

**Likely cause:** Ground effect / too close to the ground causes erratic behavior. The FC is fighting the air turbulence reflecting off the surface.

**Fix:** Give it more throttle to get higher altitude quickly. Also verify tilt servos are at exactly 90° — even slight misalignment causes drift.

---

### VTOL front motors / ESCs overheating in hover

**Problem:** Front two motors and ESCs very hot after 2-minute hover. Fine in manual (fixed wing) flight.

**Likely cause:** PIDs not tuned — motors working too hard to stabilise. Over-correction in hover causes sustained high current draw.

**Fix:** Tune PIDs for hover mode (Q-Stabilize / Q-Hover). Community references Bardwell's VTOL tutorial. Start with reduced P and feed-forward values.

---

### VTOL transition — tilt motors not completing 90° transition

**Problem:** After transition command, tilt motors stop at 45° instead of completing to 90°.

**Answer:** In iNAV, VTOL mode transitions are not automatic — requires a 3-position switch operating 0° (hover), 45° (transition), 90° (fixed wing). Ensure switch is configured correctly and servo travel limits allow full 90° movement.



## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```


