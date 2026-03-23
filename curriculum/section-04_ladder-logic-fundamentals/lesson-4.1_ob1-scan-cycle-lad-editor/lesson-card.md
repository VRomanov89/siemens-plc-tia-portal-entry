#### Lesson 4.1 — OB1, the Scan Cycle, and the LAD Editor

**Type:** Concept
**Estimated duration:** 12 minutes
**Prerequisites:** Lesson 3.3 — [Lab] Build a Hardware Configuration and Structured Tag Table

---

**What is taught:**
The instructor revisits the scan cycle from Lesson 1.1, now framing it specifically in terms of how TIA Portal's program structure maps to it — OB1 as the main program organization block that the CPU calls once per scan, what happens between scan cycles (watchdog timing, I/O update), and why writing all basic logic in OB1 is the correct starting point before introducing function blocks. The lesson then moves into the LAD editor interface: what a network is, what a rung is, how to insert new networks, how to add instructions from the toolbar or instruction panel, and how to navigate between networks. The objective is for learners to understand the spatial layout of a ladder program before they start placing instructions.

*Addresses Consensus Topics §2.1 #5 (LAD editor) and §2.1 #8 (block model — OBs). Addresses Learner Request §3.2 #6 (TIA Portal scan cycle specifically, not generically).*

**What the student learns:**
Learners gain a clear picture of how their code runs — specifically, that OB1 is called by the operating system once per scan and executes top-to-bottom, network by network. They leave with enough spatial familiarity with the LAD editor to place instructions confidently in Lesson 4.2 without spending cognitive effort on navigation.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Explain the role of OB1 in the Siemens S7-1200 program execution model
- [ ] Describe what happens during a single PLC scan cycle in TIA Portal terms — when inputs are read, when OB1 executes, when outputs are written
- [ ] Navigate the TIA Portal LAD editor — insert a network, add a rung, open the instruction panel, and place a placeholder contact and coil
- [ ] Distinguish between a network and a rung in the LAD editor

**Key concepts introduced:**
- **OB1 (Organization Block 1):** The main cyclic program block in Siemens PLCs — the operating system calls OB1 once per scan, executes all networks top to bottom, then returns control to the OS for I/O update and housekeeping before calling OB1 again.
- **Network:** A discrete logical grouping within a program block — each network contains one complete rung or logical unit. Networks can be titled and commented; they execute sequentially from top to bottom.
- **Rung:** A single horizontal line of logic in a ladder diagram — contains contacts (conditions) and a terminating coil or instruction (action). Evaluated left to right: if the logic path to the coil is true, the coil energizes.
- **Watchdog timer:** A hardware timer that monitors scan cycle time — if OB1 takes longer than the configured watchdog limit (default 150ms), the CPU stops and faults. Runaway loops and missing instructions can trigger this.

**Common pitfalls:**
- Treating OB1 as equivalent to a main() function in general-purpose programming — OB1 has no return value, no loop construct, and no concept of blocking; it runs to completion on every scan regardless.
- Placing unrelated logic in the same network — networks should each contain one logical unit; combining unrelated logic in one network makes troubleshooting in online monitoring significantly harder.

**Materials:**
- Software: TIA Portal V20 with the project from Lesson 3.3 (or the completed Lesson 3.1 demo project)
- Hardware: None
- Files: TIA Portal project from Section 3
- Reference: Siemens S7-1200 system manual — Section 5 (program execution model and OBs)

**Connects to:** Lesson 4.2 — Contacts, Coils, AND/OR Logic, and the Motor Start/Stop Circuit | With OB1 open and the LAD editor navigation understood, learners are ready to place their first instructions and build working ladder logic.
