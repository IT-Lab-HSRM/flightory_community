# Flight Software

## Table of Contents
1. [iNAV](#10-flight-software--inav)
2. [ArduPilot](#11-flight-software--ardupilot)

## 1. iNAV

### Servos not moving in iNAV

**Problem:** iNAV outputs tab shows servos moving but actual servos don't respond. Multimeter confirms power to the ports.

**Fix:** Test in **Manual flight mode** — the only mode where sticks directly control servo movement. In stabilised/auto modes, the FC decides servo inputs and won't move them much while stationary (to avoid I-term windup). Also: check the servo is connected to the correct output number as assigned in iNAV.

---

### How to set up arming in iNAV

**Fix:** In the iNAV Modes tab, choose a channel (e.g. CH5) for ARM. Use the "auto-assign" or similar feature to let iNAV detect which channel moves when you flip the switch on your radio. Set the range bars so ARM is active when the switch is in the desired position. Check the Receiver tab to confirm all channels are moving correctly with stick input.

---

### VTOL rear motor overpowering front motors in iNAV

**Problem:** Rear motor dominates, iNAV can't correct. VTOL unstable.

**Fix:** Follow Bardwell's iNAV VTOL mixer tutorial on YouTube. The mixer needs to be correctly configured for the specific geometry of a tricopter VTOL. Also check that tilt servos are at exactly 90° (not slightly off) — even a few degrees causes yaw issues.

---

### VTOL spins in place / rocks in all directions while hovering (iNAV)

**Problem:** Stallion VTOL extremely unstable in hover, rocks in all directions.

**Cause:** Default PIDs are tuned for a smaller, lighter aircraft (like T1). The Stallion is heavier and bigger, so PIDs are off.

**Fix:** Search community PID tuning threads. 

The spin in place can also be caused by: wrong tilt motor angles, rear motor not straight, or wrong motor spin directions.


## 2. ArduPilot

### Throttle visible in radio calibration but motors don't spin

**Problem:** Throttle channel moves in ArduPilot's radio calibration page, but motors don't respond.

**Answer:** In ArduPilot, the aircraft must be **armed** before throttle can be applied to motors. Use the left stick (not recommended) or a dedicated arm switch (recommended).
**Also check:** In Q-modes, check there are no remaining arming flags. GPS signal loss can block arming in some configurations.

---

### VTOL motor sequence (ArduPilot tricopter)

**Correct sequence for Stallion VTOL in ArduPilot:**
- Front Right → Motor A (Motor 1)
- Rear → Motor B (Motor 2)
- Front Left → Motor D (Motor 4)

---

### ArduPilot VTOL — one motor doesn't respond to throttle

**Problem:** Front right motor (Motor 1) only runs at arming min speed, doesn't increase with throttle. Responds correctly to pitch/roll.

**Common cause:** Motors and servos sharing the same hardware timer group — ArduPilot can't mix them on the same timer.

**Fix:** Ensure motors are on separate timer groups from servos. After fixing timer assignments, recalibrate.

---

### DShot1200 not recommended for VTOL
**Recommendation:** Use DShot 600 or DShot 300 on VTOL builds. DShot 1200 is unnecessarily fast and increases the risk of data loss from wire noise/interference.

---


## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```