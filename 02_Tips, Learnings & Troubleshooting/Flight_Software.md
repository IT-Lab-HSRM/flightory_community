# Flight Software

## Table of Contents
0. [General](#0-General)
1. [iNAV](#1-inav)
2. [ArduPilot](#2-ardupilot)


## 0. General 

### RC firmware update — official instructions don't work
**Problem:** The official GitHub instructions for updating the RC transmitter firmware (EdgeTX) failed.

**Fix:** Use the **Wi-Fi update method** instead — connect the transmitter to your Wi-Fi network and update over the air. This worked when the USB method didn't.

---

### GPS calibration — go outside, away from buildings
**Tip:** GPS calibration requires an open sky with no buildings or metal structures nearby. Compass calibration is sensitive to electromagnetic interference — move away from electronics, power cables, and metal objects. The university courtyard worked well for this.


## 1. iNAV

### iNAV version — 6.1 vs 9.0 (fb)
**Recommendation:** Use the latest stable iNAV version (currently 9.x). iNAV 8 had a known pitch oscillation bug. Version 9 has better VTOL support and bug fixes.

---

### Servos not moving in iNAV (dc)
**Problem:** iNAV outputs tab shows servos moving but actual servos don't respond. Multimeter confirms power to the ports.

**Fix:** Test in **Manual flight mode** — the only mode where sticks directly control servo movement. In stabilised/auto modes, the FC decides servo inputs and won't move them much while stationary (to avoid I-term windup). Also: check the servo is connected to the correct output number as assigned in iNAV.

---

### How to set up arming in iNAV (dc)
**Fix:** In the iNAV Modes tab, choose a channel (e.g. CH5) for ARM. Use the "auto-assign" or similar feature to let iNAV detect which channel moves when you flip the switch on your radio. Set the range bars so ARM is active when the switch is in the desired position. Check the Receiver tab to confirm all channels are moving correctly with stick input.

---

### iNAV VTOL mixer — sharing configs (fb)
**Question:** Can you share iNAV mixer screenshots for Stallion VTOL (both plane and quad profiles)?

**Community answer:** Mixer settings are highly specific to your build's servo angles and motor geometry. Importing someone else's diff/config file is not recommended — wrong tilt motor angles can damage the booms. Use the config in the manual as your starting point and adjust from there.

---

### VTOL rear motor overpowering front motors in iNAV (dc)
**Problem:** Rear motor dominates, iNAV can't correct. VTOL unstable.

**Fix:** Follow Bardwell's iNAV VTOL mixer tutorial on YouTube. The mixer needs to be correctly configured for the specific geometry of a tricopter VTOL. Also check that tilt servos are at exactly 90° (not slightly off) — even a few degrees causes yaw issues.

---

### VTOL spins in place / rocks in all directions while hovering (iNAV) (dc)
**Problem:** Stallion VTOL extremely unstable in hover, rocks in all directions.

**Cause:** Default PIDs are tuned for a smaller, lighter aircraft (like T1). The Stallion is heavier and bigger, so PIDs are off.

**Fix:** Search community PID tuning threads. 

The spin in place can also be caused by: wrong tilt motor angles, rear motor not straight, or wrong motor spin directions.


## 2. ArduPilot

### FC ships with iNAV — flashing ArduPilot is not straightforward (hsrm) 
**Problem:** The SpeedyBee F405 Wing (and similar FCs) are sold as "ArduPilot compatible" but ship with iNAV. ArduPilot cannot be flashed directly — you have to go through the iNAV Configurator first. This is not documented anywhere.

**Fix:**
1. Open iNAV Configurator
2. Go to Firmware Flasher
3. Select ArduPlane as the target firmware
4. Flash from there — not from Mission Planner directly

---

### QuadPlane parameters missing from stable ArduPilot release (hsrm) 
**Problem:** 11 hours lost because QuadPlane/VTOL parameters simply didn't appear in the stable firmware release. ESCs remained in standby (constant beeping), motor control was impossible. Nothing in the documentation explains this.

**Fix:** If VTOL parameters are missing or motors won't respond despite correct wiring, try the **latest unstable/beta firmware** version. The parameters had been removed from the stable release and were only available in beta at the time. Took minutes to fix once the root cause was known.

> "The parameters had apparently just been removed from the stable release. Not documented anywhere. A day of work lost on something that took minutes to fix once we knew."

---

### Sensor calibration sequence for ArduPilot VTOL (hsrm) 
Order of operations that worked for the HSRM build:
1. Flash ArduPlane firmware via iNAV Configurator
2. Connect via USB-C to Mission Planner
3. Write all QuadPlane/VTOL parameters
4. Go outside for GPS lock and compass calibration
5. Assign and test servo outputs
6. Flash RC transmitter and receiver firmware (EdgeTX + ELRS)
7. Bind transmitter and receiver (shared passcode for ELRS)
8. Test control surfaces — ailerons, V-tail, tilt rotors
9. Test motors last

---

### Connecting ELRS/CRSF receiver to Matek F405 Wing V2 with Mission Planner / ArduPilot (fb)
**Problem:** Radio and receiver are bound but Mission Planner can't connect via MAVLink through a 2.4GHz ELRS receiver.

**Fix checklist:**
1. Cross RX→TX and TX→RX between receiver and FC
2. In ArduPilot, set the UART the receiver is on to RCIN (not Telemetry)
3. For MAVLink over ELRS, a separate UART is needed for the telemetry stream — ELRS RC and MAVLink can share a UART on newer ELRS firmware, but setup is complex
4. Check ELRS firmware supports MAVLink (requires ELRS 3.x+)

---

### Throttle visible in radio calibration but motors don't spin (dc)
**Problem:** Throttle channel moves in ArduPilot's radio calibration page, but motors don't respond.

**Answer:** In ArduPilot, the aircraft must be **armed** before throttle can be applied to motors. Use the left stick (not recommended) or a dedicated arm switch (recommended).
**Also check:** In Q-modes, check there are no remaining arming flags. GPS signal loss can block arming in some configurations.

---

### VTOL motor sequence (ArduPilot tricopter) (dc)
**Correct sequence for Stallion VTOL in ArduPilot:**
- Front Right → Motor A (Motor 1)
- Rear → Motor B (Motor 2)
- Front Left → Motor D (Motor 4)

---

### ArduPilot VTOL — one motor doesn't respond to throttle (dc)
**Problem:** Front right motor (Motor 1) only runs at arming min speed, doesn't increase with throttle. Responds correctly to pitch/roll.

**Common cause:** Motors and servos sharing the same hardware timer group — ArduPilot can't mix them on the same timer.

**Fix:** Ensure motors are on separate timer groups from servos. After fixing timer assignments, recalibrate.

---

### DShot1200 not recommended for VTOL (dc)
**Recommendation:** Use DShot 600 or DShot 300 on VTOL builds. DShot 1200 is unnecessarily fast and increases the risk of data loss from wire noise/interference.
"""


## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)
- (hsrm) **Own personal experience** Made during Wintersemester 24/25 (HochschuleRheinMain)


