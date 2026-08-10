# Flight & Crash Issues

## Table of Contents
1. [Pre-Flight Safety](#1-Pre-Flight-Safety)
2. [Crash Issues](#2-motors--servos)
3. [Crash Repair ](#3-gps--receiver)
4. [Post Crash Checklist](#4-post-crash-checklist)

## 1. Pre-Flight Safety

## Pre-flight checklist — essential before any Flight. 

It's highly recommended to write your personal Pre-flight checklist fitting your Drone Model. 
That way Crashes / Issues can be minimized.

**Minimum crew recommended:** At least two people — pilot and spotter/technician. Camera coverage of every flight is strongly recommended for post-incident reconstruction.


## 2. Crash Issues

### Plane loops/noses dives immediately after hand launch (dc)

**Problem:** Pico Talon pitched sharply up after hand launch and nosed into the ground.

**Possible causes:**
- CG too far back (tail heavy)
- Wrong flight mode for maiden (do NOT use AutoTune on maiden — use FBWA or Stabilize)
- FC over-correcting the wrong direction (check gyro orientation in iNAV)
- Pitch/roll response swapped (elevon mixing issue on flying wings)

**Note:** Talons are particularly sensitive to CG and launch technique.

---

### VTX overheating causing potential RF interference (hsrm)
**Problem:** During the fourth flight test, the VTX was already hot before takeoff. A suspected signal interruption between transmitter and receiver occurred shortly after — possibly caused by RF noise from the overheated VTX.

**Fix:** Never take off with an already-hot VTX. Verify signal link quality in Mission Planner before arming. If RC signal quality is degraded, cool down and recheck before attempting flight.

--- 

### Drone yaws uncontrollably after takeoff — GPS mismatch (hsrm)
**Problem:** Immediately after takeoff in QHover, the drone yawed hard in one direction without any stick input and accelerated forward uncontrollably.

**Suspected cause:** GPS position mismatch. The FC attempted to correct to a position it believed it was at, but had never actually confirmed — because the pre-flight GPS check was disabled for test purposes and the FC may not have had a valid GPS lock at the moment of takeoff.

**Fix:**
- Always enable the pre-flight GPS check in ArduPilot — do not disable it even for short tests
- Verify GPS lock (solid green LED, 8+ satellites) before arming
- Never arm or take off without a confirmed GPS fix in position-hold modes (QHover, QLoiter)
- If GPS is not ready, use QStabilize mode instead — it does not rely on GPS position hold

---

### Motors cut out mid-flight — battery thermal/voltage issue (hsrm)
**Problem:** During a landing the motors cut out completely at ~2 m, causing the drone to fall straight down. Battery was found warm post-crash with cells unevenly discharged (~0.1 V difference between cells).

**Cause:** Battery delivering insufficient voltage under load — cells unevenly depleted, causing voltage sag to drop below the ESC's cutoff threshold.

**Fix:**
- Implement battery voltage logging (SD card in FC) so voltage history is available for analysis after any incident
- Monitor cell balance regularly — uneven discharge indicates a degrading pack
- Set a conservative low-voltage cutoff in ArduPilot (`BATT_LOW_VOLT`, `BATT_CRT_VOLT`) so the system warns before voltage becomes critical
- Replace any battery showing uneven cell discharge under load


## 3. Crash Repair 

### Crash repair — cutting damaged section (dc)

**Fix:** Use a hotwire foam cutter to cut the broken section off just before the nearest part line, then sand down the edge. Reprint only the damaged part.

Link: https://www.amazon.com/Cooltop-Styrofoam-Electric-Cutting-Cleaning/dp/B096SB93LQ/

---

### Repair sequence after structural crash damage
From the repair carried out after Flight Test 3:

1. Remove and label all electrical connections before starting any structural work
2. Remove damaged parts — cut or grind carefully to avoid damaging surrounding structure
3. Print or order replacement parts before disassembling further than necessary
4. Rebuild structurally first (fuselage, tail), then reinstall electronics
5. Run a full ground check of all motors, servos, and RC channels before closing the aircraft up
6. Do a CG check after reassembly — crash repairs can shift weight distribution

---

### Repair Guide Tail Replacement Stallion VTOL

Also see: 01_HSRM StallionVTOL_Our_Project/P2_repairguide.md

## 4. Post Crash Checklist

### Post Crash Checklist - essential after any incident (hsrm)
**Two crashes occurred in the same session.** The second crash happened in part because the team flew again after the first crash without a complete systems check.

**Rule:** After any crash or anomaly, do not fly again until:
1. Root cause of the incident is identified
2. All damage is assessed and documented
3. All affected systems are tested and confirmed functional
4. GPS lock is confirmed
5. All pre-flight checklist items are complete

### Document everything immediately after a crash (hsrm)
After any crash, before touching the drone:
1. Take photos of the drone in its crashed position
2. Note exact sequence of events while memory is fresh
3. Review any available video footage before discussing — video reconstruction is more reliable than memory
4. Check battery voltage and cell balance
5. Inspect all structural connections, motor mounts, and propellers before moving the aircraft


## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)
- (hsrm) **Own personal experience** Made during Wintersemester 24/25 (HochschuleRheinMain)

