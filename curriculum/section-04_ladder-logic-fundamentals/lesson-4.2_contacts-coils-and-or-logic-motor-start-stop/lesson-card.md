#### Lesson 4.2 — Contacts, Coils, AND/OR Logic, and the Motor Start/Stop Circuit

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 4.1 — OB1, the Scan Cycle, and the LAD Editor

---

**What is taught:**
The instructor demonstrates the three fundamental LAD instructions — the normally open (NO) contact, the normally closed (NC) contact, and the output coil — explaining what each represents physically and how TIA Portal evaluates them during the scan. AND logic (series contacts) and OR logic (parallel branches) are demonstrated with simple single-rung examples. The lesson then builds the motor start/stop circuit step by step: a momentary START contact in series with a STOP NC contact driving the motor output coil, followed by adding a seal-in (latch) rung — the motor output contact in parallel with the START contact — so the motor stays energized after the START button is released. The completed circuit is tested in PLCSIM with online monitoring active so learners see the logic evaluate in real time.

*Addresses Consensus Topic §2.1 #5 (LAD basics — NO/NC contacts, coils, AND/OR logic) and §2.1 #2 (sequencing norm: motor start/stop as universal first exercise).*

**What the student learns:**
Learners leave able to write basic ladder logic using the three instructions that appear in virtually every rung of every PLC program they will ever read or write. The motor start/stop circuit with seal-in rung is the foundational pattern of industrial ladder logic — understanding it at the level of why each element exists, not just where to place it, is what makes the difference between copying and reasoning.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Place and configure a normally open contact, normally closed contact, and output coil in TIA Portal's LAD editor, assigning symbolic tags to each
- [ ] Construct AND logic using series contacts and OR logic using a parallel branch in a single network
- [ ] Build a motor start/stop circuit with a seal-in rung that latches the motor output after the START button is released
- [ ] Test a ladder logic program in PLCSIM using online monitoring and confirm expected output behavior by toggling input bits

**Key concepts introduced:**
- **Normally open (NO) contact:** Passes power (evaluates TRUE) when the assigned tag is TRUE (bit = 1). Represents a condition that must be active for the rung to energize — e.g., a pressed pushbutton, an active sensor.
- **Normally closed (NC) contact:** Passes power (evaluates TRUE) when the assigned tag is FALSE (bit = 0). Represents a condition that must be inactive — e.g., a stop button that is not pressed, a safety interlock that has not tripped.
- **Output coil:** Energizes (writes TRUE to the assigned tag) when the rung evaluates TRUE; de-energizes (writes FALSE) when the rung evaluates FALSE. The action side of a rung.
- **Seal-in rung (latch pattern):** A parallel branch containing the output coil's own tag in series with the start condition — once the output energizes, its own contact keeps the rung TRUE even after the momentary start signal goes away. This is the fundamental latching pattern in ladder logic.

**Common pitfalls:**
- Wiring a STOP pushbutton as a normally open contact in software — a physical NC stop button must be wired and addressed as NC in the real panel; in software, a normally wired NC stop button appears as an NC contact passing power at rest. Using an NO contact for stop means the motor will never stop when the button fails open — a safety error.
- Forgetting to add the seal-in rung — without it, the motor output de-energizes the moment the START button is released, which appears to work in simulation (since you can force inputs) but fails on real hardware with a momentary pushbutton.
- Assigning the same tag to multiple output coils — writing to the same output coil in two different networks causes the second network to always overwrite the first; only one coil per output tag is allowed (use Set/Reset coils for multi-network control).

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None (PLCSIM used for testing)
- Files: TIA Portal project from Section 3 with hardware config and tag table; instructor adds `DI_Motor1_Start`, `DI_Motor1_Stop`, `DO_Motor1_Run` tags if not already present
- Reference: Siemens TIA Portal LAD/FBD/STL programming guide — Chapter 3 (bit logic instructions)

**Connects to:** Lesson 4.3 — Timers (TON, TOF) and Counters (CTU, CTD) — Parameters and Practical Examples | With a working motor start/stop circuit in OB1, learners add timing and counting capability to make the program respond to duration and repetition — not just state.
