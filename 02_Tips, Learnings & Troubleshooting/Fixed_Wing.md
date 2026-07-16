# Fixed Wing — Flight Tips & Issues

### First transition tips for Stallion VTOL
> "Take her up pretty high on your first transition — 150–200ft — so you can recover if something doesn't seem right. Make sure you transition with a headwind or tailwind, no crosswind — it hates crosswind. Mine likes a tailwind on takeoff: much less power required and the transition is usually quicker. Whatever you do, don't accidentally hit the disarm switch — she will not re-arm in the air."

---

### Lark — landing hot / limited grass space
**Issue:** The Lark comes in fast on landing, challenging for small or obstructed grass areas.

**Community response:** The Lark is manageable but requires practice. If landing space is very limited, consider a VTOL model instead (Stallion, Stork VTOL) — they can land vertically anywhere.

---

### Pitch oscillations on fixed wing (dolphining)

**Problem:** MiniPlank oscillating on pitch after hand launch.


**Fix:** Cut pitch P-gain and feed-forward values in ArduPilot/iNAV. This is classic PID oscillation ("dolphining"). Also check that elevon mixing is correct — flaperon vs elevon configuration is a common confusion on flying wings.


## 📝 Sources
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)