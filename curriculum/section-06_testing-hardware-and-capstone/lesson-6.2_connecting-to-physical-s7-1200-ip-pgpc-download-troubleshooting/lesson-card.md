#### Lesson 6.2 — Connecting to a Physical S7-1200: IP Address, PG/PC Interface, Download Workflow, and What Can Go Wrong

**Type:** Demo
**Estimated duration:** 20 minutes
**Prerequisites:** Lesson 6.1 — PLCSIM Simulation, Online Monitoring, Watch Tables, and the Diagnostics Buffer

---

**What is taught:**
The instructor connects a physical S7-1200 to a PC for the first time, walking through the complete workflow from unboxing to running program. Step one: configuring the PG/PC interface in TIA Portal — selecting the correct network adapter, why USB-to-Ethernet adapters frequently fail with TIA Portal, and how to verify the correct adapter is selected. Step two: a new out-of-box S7-1200 ships with no IP address — the instructor demonstrates the "accessible devices" scan that finds the PLC by MAC address even without an IP, then assigns a static IP address that places the PLC on the same subnet as the PC. Step three: the download workflow in full detail — compile hardware configuration, compile software, the download dialog (what each option means, what "overwrite all" does), CPU mode selector switch position during download, and what the status LEDs on the CPU indicate during and after download. Step four: what can go wrong — a deliberate walkthrough of each common failure: Windows Firewall blocking TIA Portal, IP address subnet mismatch, wrong network adapter selected, TIA Portal version incompatible with CPU firmware — each with the exact error message it produces and the fix.

*Addresses Coverage Gap §2.3 #2 (physical hardware connection workflow — the most critical gap found in all research). Addresses the #1 learner frustration across all forums (§3.1 #1 — cannot connect TIA Portal to the physical PLC). Directly answers the #1 learner request (§3.2 #1 — "show me connecting to a real PLC, not just simulation").*

**What the student learns:**
Learners leave with a repeatable, step-by-step mental model for connecting to any S7-1200 from any PC — including the diagnostic steps for every common failure. This lesson contains more actionable troubleshooting content than any free resource currently available for Siemens beginners. Learners who have spent hours unable to connect will recognize the exact error messages shown and finally understand why they occurred.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Configure the PG/PC interface in TIA Portal to use the correct physical Ethernet adapter for hardware communication
- [ ] Use the "accessible devices" scan to discover a factory-default S7-1200 with no IP address and assign a static IP via TIA Portal
- [ ] Execute the complete download workflow — compile hardware, compile software, navigate the download dialog, and confirm the CPU is in RUN mode after download
- [ ] Diagnose and resolve at least three common hardware connection failures using the error messages and fixes demonstrated

**Key concepts introduced:**
- **PG/PC interface:** The TIA Portal setting that specifies which physical network adapter the software uses to communicate with PLCs. Must be set to the adapter directly connected to the PLC (or the same network); selecting the wrong adapter (e.g., Wi-Fi instead of Ethernet) results in a failed scan.
- **Factory-default IP state:** A new S7-1200 out of the box has no IP address configured. TIA Portal can still discover it by MAC address via the "accessible devices" scan, which sends a Profinet discovery broadcast regardless of IP configuration. IP assignment is performed through this scan before any project download is possible.
- **Subnet matching:** The PC's Ethernet adapter and the PLC must be on the same IP subnet for communication — e.g., PC at 192.168.0.100/24 and PLC at 192.168.0.1/24. A common error is assigning the PLC an IP on a different subnet from the PC adapter, which prevents all communication even though both devices have valid IPs.
- **Download dialog options:** The TIA Portal download dialog presents options including "Stop all" (puts CPU in STOP before download — required for hardware config changes), "Overwrite all" (replaces the entire project, including DB current values — use with caution on running systems), and individual component selection. Hardware configuration changes always require a CPU stop; software-only changes can sometimes be downloaded online.
- **CPU status LEDs:** The S7-1200 CPU has three status LEDs — RUN/STOP (green = run, yellow = stop), ERROR (red = fault condition), MAINT (yellow = maintenance needed). Understanding LED patterns eliminates guesswork about CPU state during commissioning.
- **CPU mode selector switch:** The physical rotary switch on the S7-1200 CPU — positions RUN, STOP, and MRES (memory reset). Must be in RUN or STOP (not MRES) during normal download operations; MRES held for 3 seconds performs a factory memory reset.

**Common pitfalls:**
- Using a USB-to-Ethernet adapter — TIA Portal's PG/PC interface has known compatibility issues with many USB-to-Ethernet adapters; a dedicated physical Ethernet port on the PC is strongly recommended. If a USB adapter must be used, Siemens-approved adapters are listed on SIOS.
- Windows Firewall blocking Profinet discovery — TIA Portal installs firewall rules during installation, but Windows updates can reset them. If the accessible devices scan returns nothing, check that TIA Portal's firewall exceptions are intact (searchable on SIOS by the exact error code).
- Assigning the PLC an IP address outside the PC adapter's subnet — the most common connection failure after initial IP assignment. Verify both the PC adapter IP and the PLC IP are on the same subnet before downloading.
- Downloading hardware configuration with the CPU mode switch in MRES — the CPU will not accept a download in MRES mode; switch to STOP or RUN before initiating download.
- Selecting "Overwrite all" on a running production PLC — this resets all non-retentive DB values to initial values, which can disrupt running sequences. On a first-time commission this is correct; on a live system it requires careful consideration.

**Materials:**
- Software: TIA Portal V20
- Hardware: Siemens S7-1200 CPU 1214C (DC/DC/DC or DC/DC/Relay), 24VDC power supply, standard Ethernet patch cable (Cat5e or better), PC with a dedicated physical Ethernet port
- Files: `MotorLab_S4` project from Section 5 (used for the hardware download demonstration)
- Reference: Siemens S7-1200 system manual — Section 3 (installation and wiring); Siemens SIOS article on TIA Portal PG/PC interface configuration; SIOS article on "accessible devices" and first-time IP assignment

**Connects to:** Lesson 6.3 — [Capstone] Conveyor Control System — Complete PLC Project | With both simulation and hardware connection workflows mastered, learners are ready for the capstone — building a complete, multi-requirement industrial project from a problem statement alone.
