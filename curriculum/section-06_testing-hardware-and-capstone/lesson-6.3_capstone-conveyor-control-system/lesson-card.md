#### Lesson 6.3 — [Capstone] Conveyor Control System — Complete PLC Project

**Type:** Capstone
**Estimated duration:** 30 minutes
**Prerequisites:** Lesson 6.2 — Connecting to a Physical S7-1200: IP Address, PG/PC Interface, Download Workflow, and What Can Go Wrong

---

**What is taught:**
The learner receives a complete industrial problem statement and must independently design and build a full TIA Portal project — hardware configuration, tag table, FB-based program structure, global DB for configurable parameters, and a test verification procedure — with no instructor scaffolding during the build phase. After the attempt period, the instructor delivers a complete solution walkthrough, explaining not just what was built but why each structural decision was made: why the count target lives in a global DB rather than a hardcoded constant, how the E-Stop latch pattern differs from a simple series interlock, and how to verify the configurable parameter behavior without a program download.

*Addresses Coverage Gap §2.3 #7 (PLC-only capstone — no HMI). Addresses Learner Request §3.2 #4 ("give me a complete project, not just exercises"). Integrates all consensus topics: hardware configuration (§2.1 #3), tag tables (§2.1 #4), LAD fundamentals (§2.1 #5), timers and counters (§2.1 #6), block model (§2.1 #8), online monitoring (§2.1 #10).*

**What the student learns:**
This is the proof point. Learners demonstrate that they can take a real-world requirements document and translate it end-to-end into a working, professional-quality TIA Portal project — hardware config, structured code, configurable parameters, safety logic, and verified test results. The capstone deliberately requires integration across all prior sections: learners who skipped labs or followed along without understanding will encounter gaps here. The solution walkthrough closes any remaining gaps with targeted explanation.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Design and build a complete TIA Portal project from a multi-requirement industrial specification, including hardware configuration, tag table, and program structure
- [ ] Implement a latching E-Stop interlock that stops the system immediately, holds it off, and requires an explicit Reset to clear
- [ ] Configure a global Data Block parameter that controls program behavior at runtime without requiring a program download
- [ ] Verify all functional requirements against defined success criteria using PLCSIM watch tables or physical hardware I/O observation

**Key concepts introduced:**
- N/A — the capstone integrates and applies all concepts from Sections 1–6; no new concepts are introduced. Any gaps in prior knowledge surface here and are addressed in the solution walkthrough.

**Common pitfalls:**
- Hardcoding the count target as a constant in the FB instead of reading it from the global DB — hardcoded values require a program download to change, defeating the configurable parameter requirement.
- Implementing E-Stop as a simple series contact instead of a latching interlock — a simple series contact releases the E-Stop condition as soon as the button is released, which does not meet the "latches the system off until Reset is pressed" requirement.
- Not clearing the CycleComplete output on Reset — the conveyor will not start again if CycleComplete is still TRUE, since the run rung conditions on NOT CycleComplete.
- Using a level-sensitive input for the proximity sensor counter instead of a rising-edge detection — a slow-moving or stationary object over the sensor will count continuously instead of once per passage.
- Failing to test the E-Stop during a running conveyor cycle — E-Stop effectiveness must be verified while the conveyor is in motion, not just while it is stopped.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware (optional): Siemens S7-1200 CPU 1214C, 24VDC power supply, Ethernet cable, momentary pushbuttons (×4: Start, Reset, E-Stop, Proximity Sensor simulator), indicator lamp (×1: Cycle Complete), contactor or relay output (×1: Conveyor Motor)
- Files: New project `ConveyorCapstone` — built from scratch as part of the capstone
- Reference: None — all required knowledge is covered in Sections 1–6

---

**Problem statement:**

You are programming a conveyor control station at a packaging line end-of-line inspection point. The system must meet the following requirements:

**I/O specification (S7-1200 CPU 1214C, firmware V4.5):**

| Tag Name | Type | Address | Description |
|---|---|---|---|
| `DI_Conv_Start` | Bool | I0.0 | Momentary NO Start pushbutton |
| `DI_Conv_EStop` | Bool | I0.1 | E-Stop mushroom head, wired NC (TRUE = not pressed) |
| `DI_Conv_ProxSensor` | Bool | I0.2 | Proximity sensor — pulses TRUE briefly as each part passes |
| `DI_Conv_Reset` | Bool | I0.3 | Momentary NO Reset pushbutton |
| `DO_Conv_Motor` | Bool | Q0.0 | Conveyor motor contactor output |
| `DO_Conv_CycleDone` | Bool | Q0.1 | Cycle Complete indicator lamp |

**Functional requirements:**

1. **Start:** A momentary press of `DI_Conv_Start` starts the conveyor motor (`DO_Conv_Motor`) and latches it on
2. **Auto-stop:** The conveyor stops automatically when the proximity sensor count reaches the count target; the Cycle Complete indicator (`DO_Conv_CycleDone`) activates
3. **Configurable count target:** The count target is stored in a global DB (`Conveyor_Config`, variable `CountTarget`, data type Int, initial value 10) — it must be changeable by modifying the DB value at runtime without a program download
4. **Reset:** A momentary press of `DI_Conv_Reset` clears the part counter and the Cycle Complete indicator, allowing the next conveyor run to begin
5. **E-Stop:** `DI_Conv_EStop` going FALSE (button pressed, NC contact opens) immediately stops the conveyor regardless of state and latches the system off — the conveyor must not restart until Reset is pressed AND the E-Stop button is released
6. **E-Stop does not clear the counter:** Pressing Reset after an E-Stop clears the E-Stop latch and the counter simultaneously, resetting for the next cycle

**Program structure requirements:**
- A `Conveyor_Control` FB (FB1) containing all conveyor logic, with appropriately typed Input, Output, and Static interface variables
- The count target read from `Conveyor_Config.CountTarget` and passed into the FB as an Input variable each scan
- OB1 calls the FB once with a single instance DB (`ConveyorCtrl_DB`)
- All tags use the naming convention from Section 3; no absolute addressing in any program block

---

**Lab guide:**

1. Create a new TIA Portal project named `ConveyorCapstone`
2. Add an S7-1200 CPU 1214C (firmware V4.5) and compile the hardware configuration
3. Create the tag table `Conveyor_Tags` with all six I/O tags from the specification above
4. Create a global DB named `Conveyor_Config` with one variable: `CountTarget` (Int, initial value 10, non-retentive)
5. Create Function Block `Conveyor_Control` (FB1) with the following interface:
   - **Input:** `Start` (Bool), `EStop` (Bool), `ProxSensor` (Bool), `Reset` (Bool), `CountTarget` (Int)
   - **Output:** `MotorRun` (Bool), `CycleDone` (Bool)
   - **Static:** `Running` (Bool), `EStopLatch` (Bool), `PrevProx` (Bool), `PartCounter` (CTU)
6. Write the following networks inside the FB:
   - **Network 1 — E-Stop latch:** SET `#EStopLatch` when `#EStop` = FALSE (NC contact opens); RESET `#EStopLatch` when `#Reset` = TRUE AND `#EStop` = TRUE (button released)
   - **Network 2 — Conveyor run:** (`#Start` OR `#Running`) in series with NOT `#CycleDone` in series with NOT `#EStopLatch` → `#Running` coil (seal-in latch)
   - **Network 3 — Motor output:** `#Running` → `#MotorRun` output coil
   - **Network 4 — Proximity rising edge:** Detect rising edge on `#ProxSensor` using `#PrevProx` for edge memory; on rising edge, pulse the CTU CU input
   - **Network 5 — Part counter:** CTU with CU = rising edge from Network 4, R = `#Reset`, PV = `#CountTarget`; Q → `#CycleDone` output coil
   - **Network 6 — Reset Running:** `#Reset` contact → RESET coil on `#Running` (clears the latch on reset)
7. In OB1, call `Conveyor_Control` (FB1) with instance DB `ConveyorCtrl_DB`, wiring all physical I/O tags and `Conveyor_Config.CountTarget` to the FB pins
8. Compile the full project and download to PLCSIM (or physical hardware)
9. Create a watch table monitoring: `DI_Conv_EStop`, `DI_Conv_ProxSensor`, `DO_Conv_Motor`, `DO_Conv_CycleDone`, `ConveyorCtrl_DB.PartCounter.CV`, `Conveyor_Config.CountTarget`
10. Execute the verification test sequence in the success criteria below

**Solution walkthrough:** Delivered by instructor after the attempt period. Covers the complete project structure, explains the E-Stop latch design decision vs. a simple series interlock, explains why `CountTarget` is passed as a pin input rather than read directly from the DB inside the FB, and walks through the verification test sequence.

---

**Deliverables:**
- [ ] Complete TIA Portal project `ConveyorCapstone` with hardware configuration, tag table, global DB, and `Conveyor_Control` FB
- [ ] Project compiles without errors or warnings
- [ ] All functional requirements verified against the success criteria below using PLCSIM watch tables, or demonstrated on physical hardware with real I/O

---

**Success criteria:**

*Functional verification — perform each test in sequence:*

- [ ] **Start and latch:** Press `DI_Conv_Start` momentarily → `DO_Conv_Motor` energizes and remains energized after releasing the button
- [ ] **Proximity counting:** Toggle `DI_Conv_ProxSensor` TRUE→FALSE 10 times (simulating 10 part passes) → `ConveyorCtrl_DB.PartCounter.CV` increments by exactly 1 per rising edge (not continuously while TRUE)
- [ ] **Auto-stop at target:** After 10 proximity pulses → `DO_Conv_Motor` de-energizes; `DO_Conv_CycleDone` activates; pressing `DI_Conv_Start` does not restart the conveyor
- [ ] **Configurable target:** In the watch table, modify `Conveyor_Config.CountTarget` to 5 (no program download); press Reset; run a new cycle → conveyor stops after 5 proximity pulses
- [ ] **Reset:** Press `DI_Conv_Reset` → `DO_Conv_CycleDone` de-energizes; `ConveyorCtrl_DB.PartCounter.CV` resets to 0; conveyor can be restarted with `DI_Conv_Start`
- [ ] **E-Stop during run:** Start the conveyor and begin counting; set `DI_Conv_EStop` = FALSE (button pressed) → `DO_Conv_Motor` de-energizes immediately; pressing `DI_Conv_Start` does not restart the conveyor
- [ ] **E-Stop latch:** While `DI_Conv_EStop` = FALSE, press `DI_Conv_Reset` → conveyor does not restart (E-Stop still active)
- [ ] **E-Stop clear:** Set `DI_Conv_EStop` = TRUE (button released) then press `DI_Conv_Reset` → E-Stop latch clears; counter resets; conveyor can be restarted
- [ ] **Program structure:** `Conveyor_Control` FB contains no global tag references (`#` variables only); `Conveyor_Config.CountTarget` is wired to the FB's `CountTarget` input pin in OB1; instance DB `ConveyorCtrl_DB` is the only instance DB for FB1

**Connects to:** Section 6 Conclusion — Where to go from here.
