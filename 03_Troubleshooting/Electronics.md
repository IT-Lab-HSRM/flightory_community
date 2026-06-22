# Electronics

## Table of Contents
1. [Flight Controller & ESC](#6-electronics--flight-controller--esc)
2. [Motors & Servos](#7-electronics--motors--servos)
3. [GPS & Receiver](#8-electronics--gps--receiver)
4. [VTX & Camera](#9-electronics--vtx--camera)

## 1. Flight Controller & ESC


### Motors not spinning in iNAV — arming disabled

**Problem:** Motors go through boot beep sequence but won't spin. iNAV shows "Arming_Disabled_RC_link."

**Fixes:**
- Check arming flags in iNAV — look at bottom status bar
- RC link error = the flight controller doesn't see a radio receiver signal
- Make sure receiver is bound and connected via correct UART
- In iNAV Receiver tab, set correct UART and CRSF as connection type
- Cross RX→TX and TX→RX between FC and receiver
- Try ArduPilot if iNAV is unfamiliar — easier for first builds according to community

---

### ESC not communicating with FC — motors won't spin

**Problem:** 4-in-1 ESC connected but FC can't control motors.

**Root cause:** FC wasn't communicating with ESC. Missing telemetry/communication wire, or motor +/- wired backwards.

**Fix:** Check that FC is talking to ESC via correct pins. Swap positive and negative motor wires if motors don't spin. With a 4-in-1 ESC, ensure the communication cable is properly connected, not just the power wires.

---

### UART settings not saving in iNAV

**Problem:** UART 5 saves but after reboot the setting disappears.

**Fix (self-discovered):** Was using the slider as an on/off switch incorrectly. Check the iNAV documentation for the correct way to enable UARTs. Conflicting inputs can prevent saves.

---

### ESC (Lumenier/BLHeli_32) won't connect to BLHeli Suite

**Problem:** BLHeli Suite can't read or connect to ESCs.

**Fix:** Download BLHeli Suite from the correct source: https://sequremall.com/pages/blhelisuite32 and make sure you have the correct version. Also requires a **charged LiPo connected to the ESC** during configuration — USB power alone is not enough. Enable BLHeli passthrough in ArduPilot first.

---

### FC smokes / burns during full throttle test

**Problem:** SpeedyBee F405 Wing smoked during motor test at full thrust with 4S battery.
**Likely causes:**
- Capacitor wired incorrectly (should be on battery pads, not elsewhere)
- Poor solder joints — any exposed brass or cold joints can cause shorts
- Having FC connected to PC via USB while also connected to battery can cause issues

**Fix:** Check all solder joints — exposed brass means a bad joint. Use paste flux to improve soldering. If the gyro chip is damaged the FC may be fried. An SMD soldering station can replace the IC if you have the skills.

---

### Motors pulsing when disarmed (SpeedyBee F405 + 4-in-1 ESC)

**Problem:** Motors pulse continuously when disarmed. ESC calibration appears to work but pulsing returns.

**Fix:** Set `Q_M_SAFE_DISARM` to 1 to stop pulsing when disarmed. If pulsing continues when armed, switch between DShot 300 and DShot 600 and redo ESC calibration. Community member resolved this by toggling between the two DShot settings.

---

### SpeedyBee F405 Wing — DFU mode shows as "Unknown Device"

**Problem:** Holding BOOT button puts FC into DFU but Windows shows "Unknown Device." ImpulseRC Driver Fixer doesn't help.

**Fix:** The FC needs to show as "STM32 Bootloader" in Device Manager. Delete the unknown device, then use **Zadig** to install the correct WinUSB driver. Then retry flashing.

---

### OSD disappears above 20–30% throttle

**Problem:** OSD flickers and disappears at higher throttle. Video feed unaffected.

**Cause:** Unfiltered voltage from the ESC causing noise on the OSD chip.

**Fix:** Add electrolytic capacitors to the ESC power pads. 470µF at 16V is a start (got the glitch threshold up to 40%). For a permanent fix on 4S, use 1000–1500µF rated at 25V or 35V (to handle full battery voltage safely). A solid common ground for all components also helps.

---

### Multiple BEC in parallel burned one immediately

**Problem:** Three BECs connected in parallel to the battery — one immediately burned out.

**Cause:** Multiple BECs in parallel fight each other on the output side due to slight voltage differences between them.

**Fix:** Don't connect multiple BECs in parallel directly. Use a single BEC with enough current capacity. For 6 small digital servos (EMAX ES08 size), a single 3–5A BEC is more than sufficient — actual current draw is much lower than stall current.

---

### Wire gauge for VTOL builds
**Community guidance:**
- Battery to FC/PDB: minimum **12 AWG** for VTOL, 14–16 AWG for non-VTOL
- Motor to ESC: the wires that come with the ESC (typically 16 AWG) are fine — it's 3-phase and current is spread. 18 AWG is NOT enough for the recommended motors.
- Reference: https://oscarliang.com/wires-connectors/

---


## 2. Motors & Servos

### What servo can I use instead of the recommended one?

**Answer:** Any servo with similar weight and torque rating will work. If the dimensions differ, you may need to modify the mounting bracket. Community-confirmed alternatives for Stallion:
- Orbit Eris Digital Servo — 4.7kg, 0.10s, 8.5g metal gear
- Corona SB9029 — 2.2kg, 0.10s, 12.5g

Available at: https://alofthobbies.com/

---

### Motor not lifting VTOL — underpowered

**Problem:** 1300kv motor with 7" propeller can't lift a 2.25 kg VTOL.

**Fix:** Use PropCalc (https://www.ecalc.ch/xcoptercalc.php) to check your power/thrust figures before building. For VTOL, aim for at minimum 1:1 thrust-to-weight ratio at hover throttle. Check motor KV and prop size are matched to your battery voltage.

---

### Motor spinning wrong direction

**Fix:** Swap any two of the three motor phase wires to reverse rotation. For ESC-motor connections, use bullet connectors so you can easily swap wires without resoldering.

---

### Broken servo / servo spinning continuously

**Problem:** One servo spins continuously and won't hold position after centering attempt.

**Answer:** The servo is likely broken. Servos should spin to a stop position, not continuously. Replace it.

---

### ESC/motor smoking at 40% throttle

**Problem:** Motor and ESC started smoking at ~40% throttle.

**Possible causes:**
- Short circuit somewhere — check all wiring for exposed solder pads and missing insulation
- Cheap ESC with poor real-world ratings
- Propeller hitting something and stalling the motor causes instant ESC burnout

**Fix:** Ensure all wiring is properly insulated with heatshrink. Add a capacitor on the battery pads. Verify ESC amperage rating matches motor requirements.

---


## 3. GPS & Receiver

### GPS satellites = 0 indoors

**Problem:** GPS shows 0 satellites when testing indoors.

**Answer:** Normal — GPS often can't get a fix indoors due to building construction blocking signal. A GPS cold start can take 10–30 minutes on first use while it builds its almanac. After the first fix, subsequent lock-ons are much faster if the module has battery backup. Take it outside for proper testing.

---


### GPS connector mismatch (SpeedyBee F405 Wing + Matek M10Q-5883)

**Problem:** FC uses JST-SH 1.0 but GPS uses JST-GH 6-pin — connectors don't match.

**Fix:** Insert wires into the GPS-side JST-GH connector and solder the other end directly to the FC. SpeedyBee intentionally provides a GPS cable with bare contacts for this reason. Pin order matters — verify pin-out against both manuals.

---

### GPS freezing FC / servo outputs dropping to 0

**Problem:** Plugging in GPS causes all servo outputs and receiver channels to show 0 in Mission Planner. Unplugging GPS restores everything.

**Cause:** Incorrect wiring — GPS pin order differs between brands. Ready-made cables can have wrong polarity.

**Fix:** Verify pin-out carefully against both the FC and GPS manuals. Don't assume a ready-made cable is correct.

---

### Receiver not being detected by FC (Radiomaster Pocket + Matek R24D)

**Problem:** Transmitter and receiver are bound, but FC shows no channel movement.

**Explanation:** "Bound" only means the radio and receiver are talking to each other — it doesn't mean the FC sees the receiver yet.

**Fix:** Cross RX→TX and TX→RX between receiver and FC. In iNAV, set the correct UART and choose CRSF as the protocol in the Receiver tab.

---

### ELRS receiver connected but arming disabled (Arming_Disabled_RC_Link)

**Problem:** DJI O3 used as receiver on F405 Wing with iNAV — arming flag persists.

**Fix:** Set the UART that the O3 is connected to for "SmartPort" / serial RX in iNAV configuration. Reference: https://speedybee.zendesk.com/hc/en-us/articles/23350373093787
After fixing the RC link error, set up arming via a switch: go to the Receiver section in iNAV, use the channel auto-assign feature, and flip the switch you want to use for arming.

---

### TX16S external module power loop above 100mW

**Problem:** Radiomaster Nomad TX module gets stuck in power loop when set above 100mW.

**Answer:** The JR Bay interface is limited to ~100mW. This is a legacy hardware limitation — not a fault. For higher power levels (250mW, 1W, etc.), an **external battery via XT30** is required. The TX16S battery cover has a pre-marked knockout slot for the power lead.

---


## 4. VTX & Camera

### Walksnail Avatar VTX not powering on

**Problem:** Walksnail Avatar HD Kit V2 doesn't power up. USB connection does nothing, no folders appear.

**Answer:** The VTX must be powered from the flight battery, not USB. USB will not power it.

**Fix:** Connect VTX power directly to battery pads on the FC (not a BEC output). Some FC BECs don't provide enough current to boot the VTX reliably.

---

### GM3 gimbal not moving

**Problem:** Walksnail video works but gimbal won't move.

**Fix:** The GM3 gimbal only works when oriented in the same direction as the VTX module. If the gimbal is flipped (e.g. to hang downward), it stops working. Flip both the gimbal AND the VTX module together to maintain orientation.

---

### VTX overheating on the ground

**Problem:** Walksnail electronics get very hot when not flying (no airflow).

**Fix:** Add a small 5V fan. The SpeedyBee F405 Wing has 4 x LED strip 5V pads that can power a small fan (up to ~0.5A draw). A 20x20mm or 25x25mm 5V fan is sufficient — just light airflow over the VTX heatsink is enough.

**Alternative:** Connect a 24V fan to the balance lead of a 6S battery, or a 12V fan to the 3S portion of the balance lead.

---

### DJI O3 OSD layout in goggles doesn't match Mission Planner setup

**Problem:** OSD layout keeps jumping around and doesn't correspond to what's set in Mission Planner.

**Fix:** Install WTFOS on both goggles and CADDX unit, then use the MPS DisplayPort on the UART. This resolved the issue.

---

### Lost video signal at 1 mile (Walksnail)

**Problem:** Video signal lost while flying ~1 mile away from home.

**Answer:** 1 mile (~1.5 km) is within the typical real-world range limit of Walksnail with stock antennas. There are many variables: interference, obstacles, antenna orientation. The community notes that losing signal at 1.5 km with stock setup is not unusual.

**Fix for reported crash:** The VTX was set to only 25mW instead of 700mW. Always verify your VTX power level before flying.

---


## 📝 Sources
```
Source: Discord Group, link: https://discord.com/channels/1235173288150437929/1277936960970690603
```
