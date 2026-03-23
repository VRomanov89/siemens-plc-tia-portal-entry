#### Lesson 5.2 — Building a Function Block, Instance Data Block, and Optimized vs. Non-Optimized DBs

**Type:** Demo
**Estimated duration:** 18 minutes
**Prerequisites:** Lesson 5.1 — The Block Model: OBs, FBs, FCs, and DBs — When to Use Each

---

**What is taught:**
The instructor builds a `Motor_Control` Function Block from scratch in TIA Portal. The FB interface is defined step by step — Input variables (`Start`: Bool, `Stop`: Bool), Output variables (`Run`: Bool), and Static variables (`Running`: Bool for the latch state, `RunTimer`: TON for the on-delay timer instance). The ladder logic from Lesson 4.2's motor start/stop circuit is rewritten inside the FB using the local interface variables instead of global tags. The FB is then called from OB1 with a newly created instance DB, and the inputs are wired to the physical I/O tags from the tag table. The lesson then pivots to optimized vs. non-optimized Data Blocks — explaining what "optimized" means in TIA Portal (Siemens manages memory layout; no fixed byte offsets; symbolic-only access), why non-optimized DBs exist (third-party communication, legacy Modbus/OPC-DA addressing requirements), and the critical production trap: downloading a DB to a running PLC resets all non-retentive values in that DB to their initial values, which can zero out a step counter or sequence variable mid-production.

*Addresses Coverage Gap §2.3 #4 (optimized vs. non-optimized DB — not covered in any beginner course found). Addresses Learner Frustration §3.1 #5 (DB download resetting runtime values) and §3.1 #6 (optimized vs. non-optimized confusion for learners from other PLC platforms). Addresses Learner Request §3.2 #5 (block model clearly explained).*

**What the student learns:**
Learners build the Motor_Control FB with enough understanding to modify and extend it independently — they know where each variable type lives, why Static variables go in the FB interface rather than the global tag table, and why the timer instruction inside the FB uses a local static variable rather than an external instance DB. The optimized DB explanation closes a persistent gap for anyone who has encountered "can't access DB by absolute address" errors in integration work without understanding why.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Create a Function Block in TIA Portal with correctly typed Input, Output, and Static interface variables
- [ ] Write ladder logic inside an FB using local interface variables rather than global tag table references
- [ ] Call an FB from OB1, assign an instance DB, and wire physical I/O tags to the FB's input and output pins
- [ ] Explain the difference between optimized and non-optimized Data Blocks and identify at least one scenario where non-optimized access is required
- [ ] Describe the consequence of downloading a DB to a running PLC and how to avoid unintended value resets in production

**Key concepts introduced:**
- **FB interface sections:** The variable declaration table at the top of every FB — Input (values passed in from the caller), Output (values passed back to the caller), InOut (read-write pass-through), Static (values that persist between calls, stored in the instance DB), Temp (values that exist only during the current scan cycle, discarded afterward).
- **Local variable reference in FB logic:** Inside an FB, all logic references the FB's own interface variable names (e.g., `#Start`, `#Run`, `#Running`) using the `#` prefix — not global tag table entries. This is what makes the FB reusable: the logic is the same for every instance; only the data (the instance DB) differs.
- **Optimized Data Block:** The default DB type in TIA Portal for S7-1200/1500 — Siemens manages the memory layout automatically; variables are accessed by symbolic name only (no fixed byte/bit offsets); TIA Portal can optimize memory usage and alignment. Cannot be addressed by absolute offset from external tools.
- **Non-optimized Data Block:** A DB with fixed byte offsets for every variable — each variable has a defined address (e.g., DB1.DBX0.0, DB1.DBW2) that is stable across program changes. Required when a third-party device or OPC server must address specific byte offsets. Enabled by unchecking "Optimized block access" in the DB properties.
- **DB download and value reset:** When a DB is downloaded to a running PLC (e.g., after adding a variable or changing an initial value), all non-retentive variables in that DB are reset to their initial values — the PLC does not preserve runtime values during a DB download. This is a documented Siemens behavior that can disrupt running sequences or reset critical process variables mid-production.

**Common pitfalls:**
- Referencing global tag table entries inside an FB instead of the FB's own `#` interface variables — this works but creates a hidden dependency between the FB and specific global tags, destroying reusability; every instance will read and write the same global tags simultaneously.
- Creating a Static variable for every intermediate result — Temp variables are the correct choice for values used only within a single scan; Static variables should only be used for values that must be remembered between scans.
- Assuming a DB download is safe during production because "only one variable changed" — any non-retentive variable in the DB is reset on download, regardless of which variable was modified. Always verify retentivity settings and test impact before downloading to a live system.
- Placing timer instructions in the FB by referencing an external instance DB rather than a Static variable — timers inside FBs must use a Static variable of type TON (or TOF, TP) so each FB instance has its own private timer state.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None
- Files: Continuing the TIA Portal project from Lesson 4.4 (`MotorLab_S4`); the Motor_Control FB is added as a new block alongside the existing OB1
- Reference: Siemens S7-1200 system manual — Section 7.4 (Data Blocks and optimized block access); Siemens TIA Portal programming guidelines — DB retentivity section (SIOS)

**Connects to:** Lesson 5.3 — [Lab] Refactor Motor Control into a Reusable FB | Learners immediately apply the FB build process independently — refactoring the existing motor control logic out of OB1 and into a proper FB, then instantiating it twice.
