# Electronics & Avionics Troubleshooting Guide

## Table of Contents
1. [Flight Controller & ESC](#1-flight-controller--esc)
2. [Motors & Servos](#2-motors--servos)
3. [GPS & Receiver](#3-gps--receiver)
4. [Power & Battery](#4-power--battery)
5. [VTX & Camera](#5-vtx--camera)

## 1. Flight Controller & ESC

### SpeedyBee F405 Wing Mini — bricked after flashing iNAV (fb)
**Problem:** After flashing iNAV (target SPEEDYBEEF405WING), the FC stopped connecting. SpeedyBee app shows "Failed to Communicate with FC." No COM port or DFU visible in iNAV Configurator.

**Fix:** Disconnect the GPS module completely from the FC, then reflash. The GPS appears to interfere with the DFU/connection process on this board.

**Also:** Use **Zadig** to install the correct USB driver (STM32 Bootloader) in Windows if DFU mode isn't being recognised.

---

### SpeedyBee F405 Wing — DFU mode shows as "Unknown Device" (dc)
**Problem:** Holding BOOT button puts FC into DFU but Windows shows "Unknown Device." ImpulseRC Driver Fixer doesn't help.

**Fix:** The FC needs to show as "STM32 Bootloader" in Device Manager. Delete the unknown device, then use **Zadig** to install the correct WinUSB driver. Then retry flashing.

---

### JHEMCU F405 clone — is it compatible? (fb)
**Question:** Can I use a JHEMCU F405 clone instead of the SpeedyBee (which is out of stock)?

**Answer:** Yes, Any F405-class FC flashed with the correct iNAV or ArduPilot target will work the same way.

---

### 4-in-1 ESC current rating — is 50A enough for VTOL? (fb)
**Question:** ESC rated 50A but total current draw at transition showed 93A — is the ESC undersized?

**Clarification:** A 4-in-1 ESC rated 50A means 50A **per motor/channel**, not total. So a 3-motor VTOL on a 50A 4-in-1 = 150A total capacity. The 93A reading is the **total draw across all motors**, which means each motor was pulling ~31A — well within the 50A per-channel rating.

---

### ESC cutting out during transition / crash (fb)
**Problem:** ESC triggered protection cutout at 93A during VTOL-to-fixed-wing transition, causing loss of power and crash. ESC rebooted mid-air (startup beeps heard after crash).

**Possible causes:**
  * **Underpowered/wrong battery voltage** — 1300KV motors designed for 5S–6S being run on 4S won't produce enough thrust and motor will draw more current trying to compensate
  * **Weight** — overweight build means motors work harder at transition
  * **Loose battery connector** — a slightly loose XT60 can cause momentary power interruption that triggers ESC protection
  * **Wiring gauge** — undersized wires cause voltage sag under load


---

### External PDB with current meter for F405 Wing (fb)
**Question:** What external PDB can be used with SpeedyBee F405 Wing to see total amp draw in OSD?

**Answer:** There isn't really a clean external PDB solution that connects a current meter to the F405 Wing. The **F405 Wing already has a built-in PDB with current sensing** — use that. Connect your battery through the FC's power input and configure the current sensor in the flight software.

---

### F405 battery monitoring settings (Matek F405 Wing V2 vs V1) (fb)
**Question:** Are the battery monitoring settings in Mission Planner the same for V2 as V1?

*Note:* ArduPilot docs at: https://ardupilot.org/plane/docs/common-matekf405-wing.html
*(V2 settings not confirmed, check directly with Matek or ArduPilot forums for V2-specific BATT_AMP_PERVLT and BATT_VOLT_MULT values.)*

---

### Motors not spinning in iNAV — arming disabled (dc)
**Problem:** Motors go through boot beep sequence but won't spin. iNAV shows "Arming_Disabled_RC_link."

**Fixes:**
  * Check arming flags in iNAV — look at bottom status bar
  * RC link error = the flight controller doesn't see a radio receiver signal
  * Make sure receiver is bound and connected via correct UART
  * In iNAV Receiver tab, set correct UART and CRSF as connection type
  * Cross RX→TX and TX→RX between FC and receiver
  * Try ArduPilot if iNAV is unfamiliar — easier for first builds according to community

---

### ESC not communicating with FC — motors won't spin (dc)
**Problem:** 4-in-1 ESC connected but FC can't control motors.

**Root cause:** FC wasn't communicating with ESC. Missing telemetry/communication wire, or motor +/- wired backwards.

**Fix:** Check that FC is talking to ESC via correct pins. Swap positive and negative motor wires if motors don't spin. With a 4-in-1 ESC, ensure the communication cable is properly connected, not just the power wires.

---

### UART settings not saving in iNAV (dc)
**Problem:** UART 5 saves but after reboot the setting disappears.

**Fix (self-discovered):** Was using the slider as an on/off switch incorrectly. Check the iNAV documentation for the correct way to enable UARTs. Conflicting inputs can prevent saves.

---

### ESC (Lumenier/BLHeli_32) won't connect to BLHeli Suite (dc)
**Problem:** BLHeli Suite can't read or connect to ESCs.

**Fix:** Download BLHeli Suite from the correct source: https://sequremall.com/pages/blhelisuite32 and make sure you have the correct version. Also requires a **charged LiPo connected to the ESC** during configuration — USB power alone is not enough. Enable BLHeli passthrough in ArduPilot first.

---

### FC smokes / burns during full throttle test (dc)
**Problem:** SpeedyBee F405 Wing smoked during motor test at full thrust with 4S battery.

**Likely causes:**
  * Capacitor wired incorrectly (should be on battery pads, not elsewhere)
  * Poor solder joints — any exposed brass or cold joints can cause shorts
  * Having FC connected to PC via USB while also connected to battery can cause issues

**Fix:** Check all solder joints — exposed brass means a bad joint. Use paste flux to improve soldering. If the gyro chip is damaged the FC may be fried. An SMD soldering station can replace the IC if you have the skills.

---

### Motors pulsing when disarmed (SpeedyBee F405 + 4-in-1 ESC) (dc)
**Problem:** Motors pulse continuously when disarmed. ESC calibration appears to work but pulsing returns.

**Fix:** Set `Q_M_SAFE_DISARM` to 1 to stop pulsing when disarmed. If pulsing continues when armed, switch between DShot 300 and DShot 600 and redo ESC calibration. Community member resolved this by toggling between the two DShot settings.

---

### OSD disappears above 20–30% throttle (dc)
**Problem:** OSD flickers and disappears at higher throttle. Video feed unaffected.

**Cause:** Unfiltered voltage from the ESC causing noise on the OSD chip.

**Fix:** Add electrolytic capacitors to the ESC power pads. 470µF at 16V is a start (got the glitch threshold up to 40%). For a permanent fix on 4S, use 1000–1500µF rated at 25V or 35V (to handle full battery voltage safely). A solid common ground for all components also helps.

---

### Multiple BEC in parallel burned one immediately (dc)
**Problem:** Three BECs connected in parallel to the battery — one immediately burned out.

**Cause:** Multiple BECs in parallel fight each other on the output side due to slight voltage differences between them.

**Fix:** Don't connect multiple BECs in parallel directly. Use a single BEC with enough current capacity. For 6 small digital servos (EMAX ES08 size), a single 3–5A BEC is more than sufficient — actual current draw is much lower than stall current.


## 2. Motors & Servos

### What servo can I use instead of the recommended one? (dc)
**Answer:** Any servo with similar weight and torque rating will work. If the dimensions differ, you may need to modify the mounting bracket. Community-confirmed alternatives for Stallion:
  * Orbit Eris Digital Servo — 4.7kg, 0.10s, 8.5g metal gear
  * Corona SB9029 — 2.2kg, 0.10s, 12.5g
* Available at: https://alofthobbies.com/

---

### Motor not lifting VTOL — underpowered (dc)
**Problem:** 1300kv motor with 7" propeller can't lift a 2.25 kg VTOL.

**Fix:** Use PropCalc (https://www.ecalc.ch/xcoptercalc.php) to check your power/thrust figures before building. For VTOL, aim for at minimum 1:1 thrust-to-weight ratio at hover throttle. Check motor KV and prop size are matched to your battery voltage. *(See also section 4 regarding 4S vs 6S batteries for 1300KV motors).*

---

### Motor spinning wrong direction (dc)
**Fix:** Swap any two of the three motor phase wires to reverse rotation. For ESC-motor connections, use bullet connectors so you can easily swap wires without resoldering.

---

### Broken servo / servo spinning continuously (dc)
**Problem:** One servo spins continuously and won't hold position after centering attempt.
**Answer:** The servo is likely broken. Servos should spin to a stop position, not continuously. Replace it.

---

### ESC/motor smoking at 40% throttle (dc)
**Problem:** Motor and ESC started smoking at ~40% throttle.

**Possible causes:**
  * Short circuit somewhere — check all wiring for exposed solder pads and missing insulation
  * Cheap ESC with poor real-world ratings
  * Propeller hitting something and stalling the motor causes instant ESC burnout

**Fix:** Ensure all wiring is properly insulated with heatshrink. Add a capacitor on the battery pads. Verify ESC amperage rating matches motor requirements.

## 3. GPS & Receiver

### GPS not connecting — Matek M10Q-5883 + SpeedyBee F405 Wing + iNAV (fb)
**Problem:** GPS LED on, but iNAV shows 0 satellites, 0 total messages, Fix type: None. Ports configured with UART3 → Sensors → GPS, protocol UBLOX.

**Most likely cause:** TX/RX wires crossed incorrectly, or cable pinout incompatible between the two connectors.

**Checklist:**
  1. Confirm GPS TX → FC RX and GPS RX → FC TX (cross the wires)
  2. Verify the cable pinout against both the FC and GPS documentation — ready-made cables often have wrong pin order between JST-SH and JST-GH connectors
  3. Make sure "GPS for navigation and telemetry" is enabled in iNAV Configuration tab
  4. Test outdoors — GPS won't lock indoors

---

### GPS connector mismatch (SpeedyBee F405 Wing + Matek M10Q-5883) (dc)
**Problem:** FC uses JST-SH 1.0 but GPS uses JST-GH 6-pin — connectors don't match.

**Fix:** Insert wires into the GPS-side JST-GH connector and solder the other end directly to the FC. SpeedyBee intentionally provides a GPS cable with bare contacts for this reason. Pin order matters — verify pin-out against both manuals.

---

### GPS satellites = 0 indoors (dc)
* **Problem:** GPS shows 0 satellites when testing indoors.
* **Answer:** Normal — GPS often can't get a fix indoors due to building construction blocking signal. A GPS cold start can take 10–30 minutes on first use while it builds its almanac. After the first fix, subsequent lock-ons are much faster if the module has battery backup. Take it outside for proper testing.

---

### GPS freezing FC / servo outputs dropping to 0 (dc)
* **Problem:** Plugging in GPS causes all servo outputs and receiver channels to show 0 in Mission Planner. Unplugging GPS restores everything.
* **Cause:** Incorrect wiring — GPS pin order differs between brands. Ready-made cables can have wrong polarity.
* **Fix:** Verify pin-out carefully against both the FC and GPS manuals. Don't assume a ready-made cable is correct.

---

### Receiver not being detected by FC (Radiomaster Pocket + Matek R24D) (dc)
* **Problem:** Transmitter and receiver are bound, but FC shows no channel movement.
* **Explanation:** "Bound" only means the radio and receiver are talking to each other — it doesn't mean the FC sees the receiver yet.
* **Fix:** Cross RX→TX and TX→RX between receiver and FC. In iNAV, set the correct UART and choose CRSF as the protocol in the Receiver tab.

---

### ELRS receiver connected but arming disabled (Arming_Disabled_RC_Link) (dc)
* **Problem:** DJI O3 used as receiver on F405 Wing with iNAV — arming flag persists.
* **Fix:** Set the UART that the O3 is connected to for "SmartPort" / serial RX in iNAV configuration. Reference: https://speedybee.zendesk.com/hc/en-us/articles/23350373093787
* After fixing the RC link error, set up arming via a switch: go to the Receiver section in iNAV, use the channel auto-assign feature, and flip the switch you want to use for arming.

---

### TX16S external module power loop above 100mW (dc)
* **Problem:** Radiomaster Nomad TX module gets stuck in power loop when set above 100mW.
* **Answer:** The JR Bay interface is limited to ~100mW. This is a legacy hardware limitation — not a fault. For higher power levels (250mW, 1W, etc.), an **external battery via XT30** is required. The TX16S battery cover has a pre-marked knockout slot for the power lead.


## 4. Power & Battery

### 4S battery not enough for Stallion VTOL with 1300KV motors (fb)
**Problem:** Stallion VTOL with T-Motor F90 1300KV motors on 4S battery can't lift off — needed 100% throttle just to get a few inches up.

**Answer:** 1300KV is designed for 5S–6S. On 4S it doesn't have enough RPM to generate sufficient thrust, regardless of prop size.

**Fixes:**
  * Switch to **6S battery** (most recommended — night and day difference)
  * Or use **5S battery** as a minimum
  * Or change to higher-KV motors suited for 4S

---

### Battery for flight time estimation (fb)
**Rule of thumb:** If you know your cruising amp draw and battery capacity, divide capacity by amp draw for approximate hours.

**Example:** 10,000mAh battery at 4A cruise = ~2.5 hours. Check motor manufacturer specs for estimated cruise current at your voltage/prop combination.

---

### Batteries in wings — is it possible? (fb)
**Answer:** It has been done on other platforms (FX-78, Firefly-6 VTOL) but not practical for Flightory models. The wing profiles are too narrow for even 21700 cells, and the wings aren't designed to carry that structural load. A 3–4+ metre wingspan would be needed before wing batteries make sense.

---

### Wire gauge for VTOL builds (dc)
**Community guidance:**
  * Battery to FC/PDB: minimum **12 AWG** for VTOL, 14–16 AWG for non-VTOL
  * Motor to ESC: the wires that come with the ESC (typically 16 AWG) are fine — it's 3-phase and current is spread. 18 AWG is NOT enough for the recommended motors.
  * Reference: https://oscarliang.com/wires-connectors/


## 5. VTX & Camera

### Walksnail Avatar VTX not powering on (dc)
**Problem:** Walksnail Avatar HD Kit V2 doesn't power up. USB connection does nothing, no folders appear.

**Answer:** The VTX must be powered from the flight battery, not USB. USB will not power it.

**Fix:** Connect VTX power directly to battery pads on the FC (not a BEC output). Some FC BECs don't provide enough current to boot the VTX reliably.

---

### GM3 gimbal not moving (dc)
**Problem:** Walksnail video works but gimbal won't move.

**Fix:** The GM3 gimbal only works when oriented in the same direction as the VTX module. If the gimbal is flipped (e.g. to hang downward), it stops working. Flip both the gimbal AND the VTX module together to maintain orientation.

---

### VTX overheating on the ground (dc)
**Problem:** Walksnail electronics get very hot when not flying (no airflow).

**Fix:** Add a small 5V fan. The SpeedyBee F405 Wing has 4 x LED strip 5V pads that can power a small fan (up to ~0.5A draw). A 20x20mm or 25x25mm 5V fan is sufficient — just light airflow over the VTX heatsink is enough.

**Alternative:** Connect a 24V fan to the balance lead of a 6S battery, or a 12V fan to the 3S portion of the balance lead.

---

### DJI O3 OSD layout in goggles doesn't match Mission Planner setup (dc)
**Problem:** OSD layout keeps jumping around and doesn't correspond to what's set in Mission Planner.

**Fix:** Install WTFOS on both goggles and CADDX unit, then use the MPS DisplayPort on the UART. This resolved the issue.

---

### Lost video signal at 1 mile (Walksnail) (dc)
**Problem:** Video signal lost while flying ~1 mile away from home.

**Answer:** 1 mile (~1.5 km) is within the typical real-world range limit of Walksnail with stock antennas. There are many variables: interference, obstacles, antenna orientation. The community notes that losing signal at 1.5 km with stock setup is not unusual.

**Fix for reported crash:** The VTX was set to only 25mW instead of 700mW. Always verify your VTX power level before flying.

## 📝 Sources
- (dc) **Discord Group:** [Discord Flightory Group](https://discord.com/channels/1235173288150437929/1277936960970690603) 
- (fb) **Facebook Group:** [facebook.com/groups/flightory/](https://www.facebook.com/groups/flightory/)
