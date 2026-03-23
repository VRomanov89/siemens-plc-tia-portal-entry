#### Lesson 6.1 — PLCSIM Simulation, Online Monitoring, Watch Tables, and the Diagnostics Buffer

**Type:** Demo
**Estimated duration:** 20 minutes
**Prerequisites:** Lesson 5.3 — [Lab] Refactor Motor Control into a Reusable FB

---

**What is taught:**
The instructor demonstrates TIA Portal's complete testing toolkit using the `MotorLab_S4` project and PLCSIM. The lesson covers: starting PLCSIM and downloading a project; what "going online" means in TIA Portal (the software connects to the running PLC — real or simulated — and begins receiving live data); the online LAD view with green contact highlighting and coil status; creating a watch table, adding variables by tag name or DB path, setting monitoring intervals, and the critical distinction between monitoring (read-only) and forcing (write to the PLC, overriding the program). The diagnostics buffer is covered in full — how to open it, what each entry means (timestamp, event type, event description), and how to read a CPU stop entry to identify what caused the fault. The lesson closes with a deliberate fault injection: a watchdog timeout triggered by an infinite loop to show what a fault looks like end-to-end — the CPU stops, the diagnostics buffer records the entry, and the instructor walks through the recovery procedure.

*Addresses Consensus Topics §2.1 #7 (PLCSIM simulation) and §2.1 #10 (diagnostics and online monitoring). Addresses Learner Request §3.2 #6 (PLCSIM behavior specifically vs. real hardware). Addresses Common Knowledge Gap §3.3 #3 (compile and download sequence not well understood).*

**What the student learns:**
Learners gain command of the tools professionals use to test and troubleshoot PLC programs — not just "how to start a simulation" but how to surgically observe program behavior, inject test conditions, and diagnose faults from the CPU's own event record. The forced fault demonstration is particularly valuable: most beginners have no mental model for what a CPU fault looks like or how to recover it, and encountering one on real hardware without preparation causes significant confusion.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Start a PLCSIM simulation, download a project, and establish an online connection in TIA Portal
- [ ] Use online LAD monitoring to observe rung evaluation and identify which contacts are passing power during live execution
- [ ] Create a watch table, add variables (including DB variables), and distinguish between monitoring mode and forcing mode
- [ ] Open the diagnostics buffer, interpret the entries, and identify the event that caused a CPU to stop
- [ ] Recover a faulted CPU by reading the diagnostics buffer, acknowledging the fault, and returning the CPU to RUN mode

**Key concepts introduced:**
- **Online connection:** The state where TIA Portal is actively communicating with a running PLC (real or PLCSIM) — indicated by the orange online toolbar and green/yellow status indicators in the Project Tree. In online mode, TIA Portal receives live scan data from the PLC.
- **Online LAD view:** The live program editor view when online — contacts and coils highlight in green when their evaluated state is TRUE, giving a real-time visual of rung evaluation that makes logical errors immediately visible.
- **Watch table:** A configurable monitoring panel where specific tags and DB variables can be tracked by name, showing their current values updated each scan. Variables can be forced (written) to test specific conditions without changing the physical I/O.
- **Force vs. Monitor:** Monitoring reads the current value from the PLC without affecting it. Forcing writes a value to the PLC, overriding what the program or physical hardware would otherwise write — useful for testing specific conditions but dangerous on real hardware if physical outputs are connected to live equipment.
- **Diagnostics buffer:** A ring buffer in the CPU that records timestamped entries for every significant system event — program download, CPU mode changes, hardware faults, communication errors, and CPU stops. The most recent 50–100 entries are accessible from TIA Portal's online tools. It is the first place to look when a CPU has stopped unexpectedly.
- **CPU stop conditions:** Events that cause the CPU to leave RUN mode and enter STOP — unhandled faults (missing fault OB), watchdog timeout, hardware configuration mismatch, and explicit STOP commands. A stopped CPU does not execute the user program and all outputs de-energize (or retain their last state, depending on output module configuration).

**Common pitfalls:**
- Leaving forces active after testing — forced values persist in the CPU until explicitly cleared; forgetting to remove a force that sets an output to TRUE can cause unexpected behavior (or physical hazards on real hardware) in subsequent test runs.
- Assuming PLCSIM behavior is identical to a real PLC in all respects — PLCSIM does not simulate input signal noise, propagation delays, physical wiring faults, or hardware-specific timing behaviors. Programs that work in PLCSIM may behave unexpectedly on hardware if they rely on assumptions that only hold in simulation.
- Reading the diagnostics buffer without understanding timestamps — entries are timestamped by the CPU's internal clock, which may not be synchronized; the relative order of entries is reliable, but absolute timestamps may be inaccurate until the CPU clock is set.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None (PLCSIM used throughout this lesson; same techniques apply verbatim to real hardware)
- Files: `MotorLab_S4` project from Section 5
- Reference: Siemens TIA Portal online and diagnostics manual (available on SIOS); S7-1200 system manual — Section 11 (diagnostics and error handling)

**Connects to:** Lesson 6.2 — Connecting to a Physical S7-1200: IP Address, PG/PC Interface, Download Workflow, and What Can Go Wrong | With the testing toolkit mastered in simulation, learners who have physical hardware are ready to apply the same online monitoring workflow to a real S7-1200 connected over Ethernet.
