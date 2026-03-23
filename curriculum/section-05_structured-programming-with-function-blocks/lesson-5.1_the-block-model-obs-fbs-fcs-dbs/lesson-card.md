#### Lesson 5.1 — The Block Model: OBs, FBs, FCs, and DBs — When to Use Each

**Type:** Concept
**Estimated duration:** 12 minutes
**Prerequisites:** Lesson 4.4 — [Lab] Motor Start/Stop with Timer-Based Indicator and Start Counter

---

**What is taught:**
The instructor explains the Siemens block model with a focus on the decision-making framework: not just what each block type is, but when and why to choose one over another. OBs are covered as operating system entry points — OB1 (cyclic), fault OBs (OB80, OB82, OB86), and why this matters for program reliability. FBs are introduced as stateful blocks — their static variable interface section is the defining characteristic, and the instance DB is the mechanism that makes multiple independent instances possible. FCs are presented as stateless functions — no memory, pure input-to-output transformation, appropriate for calculations and conversions but not for anything that needs to remember state between scans. Global DBs are introduced as shared data stores — recipe parameters, setpoints, process variables — that any block can read from or write to. The lesson closes with a simple decision flowchart: "Does this block need to remember something between scans? → FB. Does it just calculate? → FC. Does it store shared data? → Global DB."

*Addresses Consensus Topic §2.1 #8 (block model). Addresses Learner Request §3.2 #5 ("explain the block model clearly"). Addresses Common Knowledge Gap §3.3 #1 (learners can copy block structure but cannot make independent decisions).*

**What the student learns:**
Learners gain the decision framework that separates engineers who can read PLC code from engineers who can design it. The distinction between FB and FC — specifically that FB has static memory and FC does not — is the single most important concept in this section, and the one most beginner courses treat as incidental. Learners leave with a clear, memorable rule for choosing the right block type.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Describe the role of OB1 and at least two fault OBs in the S7-1200 program execution model
- [ ] Distinguish between a Function Block (FB) and a Function (FC) based on whether the block requires persistent state between scan cycles
- [ ] Explain the role of an instance Data Block in relation to a Function Block
- [ ] Select the appropriate block type (OB, FB, FC, or global DB) for three described programming scenarios using the decision framework

**Key concepts introduced:**
- **Organization Block (OB):** The operating system's entry point into user code — OBs are called by the CPU OS in response to specific events. OB1 = main cyclic execution; OB30–OB38 = cyclic interrupt OBs (time-triggered); OB80 = time error; OB82 = diagnostic interrupt; OB86 = rack/station failure. Writing fault OBs prevents the CPU from stopping on non-critical errors.
- **Function Block (FB):** A program block with a variable interface (Input, Output, InOut, Static, Temp) where Static variables retain their values between calls via an instance Data Block. Use FBs for anything with state: motor control, valve control, sequences, PID.
- **Function (FC):** A program block with inputs, outputs, and temporary variables only — no static variables, no instance DB. State is not retained between calls. Use FCs for pure calculations: unit conversions, scaling, logic that produces an output purely from its inputs.
- **Global Data Block (DB):** A shared data store accessible by any block in the project — stores persistent data not tied to a specific FB instance: recipe parameters, setpoints, production counts, alarm records.
- **Instance Data Block:** Automatically created when an FB is called — stores all Static variables for that specific call instance. Two calls to the same FB produce two independent instance DBs, giving each instance its own private state.

**Common pitfalls:**
- Using FBs for stateless calculations — adding unnecessary instance DBs creates memory overhead and organizational complexity; FCs are the correct choice for pure input-to-output transformations.
- Calling the same FB with the same instance DB from two different network locations — this causes state collision; each FB call must have its own unique instance DB.
- Confusing a global DB with an instance DB — a global DB is explicitly created by the programmer and contains shared data; an instance DB is created automatically when an FB is called and is private to that call instance.

**Materials:**
- Software: TIA Portal V20 (interface reference only — no project building in this lesson)
- Hardware: None
- Files: None
- Reference: Siemens S7-1200 system manual — Section 7 (program blocks and block types); Siemens TIA Portal programming guidelines (available on SIOS)

**Connects to:** Lesson 5.2 — Building a Function Block, Instance Data Block, and Optimized vs. Non-Optimized DBs | With the decision framework clear, learners move directly into building the Motor_Control FB from scratch — applying the block model in TIA Portal.
