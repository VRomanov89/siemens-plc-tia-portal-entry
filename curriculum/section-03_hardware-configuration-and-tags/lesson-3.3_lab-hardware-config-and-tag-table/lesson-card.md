#### Lesson 3.3 — [Lab] Build a Hardware Configuration and Structured Tag Table

**Type:** Lab
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 3.2 — PLC Memory Areas (I/Q/M/DB), Tag Tables, and Naming Conventions

---

**What is taught:**
The learner receives a problem statement describing a pump control station and is asked to independently build the complete TIA Portal hardware configuration and tag table for it — without following along with an instructor. After the attempt period, the instructor delivers a solution walkthrough showing a correct implementation, calling out common errors made during independent attempts and explaining the reasoning behind each decision.

**What the student learns:**
Learners discover whether they can translate a real-world I/O description into a TIA Portal project without instructor scaffolding. The gap between watching a demo and doing it independently becomes immediately apparent here — and the solution walkthrough closes that gap with targeted correction rather than generic repetition. This is the skill consolidation checkpoint for Section 3.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Build a complete TIA Portal hardware configuration for a described application independently, selecting the correct CPU and signal modules
- [ ] Construct a tag table with correctly named, typed, addressed, and commented tags using a consistent naming convention
- [ ] Verify the hardware configuration compiles without errors before submitting
- [ ] Identify and correct at least two common errors in a tag table (wrong data type, inconsistent naming, missing comments)

**Key concepts introduced:**
- N/A — this lesson applies concepts introduced in Lessons 3.1 and 3.2; no new concepts are introduced.

**Common pitfalls:**
- Jumping straight to the tag table before completing and compiling the hardware configuration — tags reference I/O addresses that only exist after hardware config is complete.
- Using data type `Int` for physical I/O points — physical digital I/O signals are Bool (a single bit), not Int. Using Int wastes memory and causes type errors in logic blocks.
- Inconsistent naming — mixing conventions within the same tag table (e.g., `DI_Pump1_Start` alongside `Stop_Button` and `INPUT_3`) makes the program unreadable and signals a misunderstanding of the convention's purpose.

**Materials:**
- Software: TIA Portal V20
- Hardware: None
- Files: New blank TIA Portal project (do not reuse the Lesson 3.1/3.2 project — start fresh to practice the full workflow)
- Reference: None — attempt the lab using knowledge from Lessons 3.1 and 3.2 before reviewing the solution

---

**Lab guide:**

*Problem statement:* You are configuring a TIA Portal project for a pump control station. The station has the following I/O:

**Physical I/O (on the S7-1200 CPU 1214C, firmware V4.5):**
- 3 digital inputs: Start pushbutton, Stop pushbutton, High-level float switch
- 2 digital outputs: Pump motor contactor, Fault indicator lamp
- 1 additional digital input module (SM 1221, 8 DI) is installed for future expansion — add it to the hardware configuration even though no tags reference it yet

**Requirements:**
1. Create a new TIA Portal project named `PumpStation_Lab`
2. Add an S7-1200 CPU 1214C (firmware V4.5) to the project
3. Add an SM 1221 8DI signal module in the next available slot
4. Compile the hardware configuration — resolve any errors before proceeding
5. Create a tag table named `PumpStation_Tags` with all 5 I/O tags
6. Apply the prefix naming convention from Lesson 3.2 to all tags (`DI_`, `DO_` prefixes)
7. Assign the correct data type to each tag (all are Bool)
8. Assign absolute addresses based on the hardware configuration's auto-assigned I/O addresses
9. Add a descriptive comment to every tag

**Solution walkthrough:** Presented by instructor after the attempt period. The walkthrough shows a correct `PumpStation_Tags` table and highlights the three most common errors observed in this exercise.

---

**Success criteria:**
- [ ] Project `PumpStation_Lab` exists and opens without errors
- [ ] Hardware configuration contains an S7-1200 CPU 1214C (V4.5) and an SM 1221 8DI module in the correct slot
- [ ] Hardware configuration compiles without errors or warnings
- [ ] Tag table `PumpStation_Tags` contains exactly 5 tags — 3 inputs, 2 outputs
- [ ] All tag names use the `DI_` / `DO_` prefix convention and include a functional descriptor (e.g., `DI_Pump1_Start`, not `Input1`)
- [ ] All tags are data type Bool
- [ ] All tags have non-empty comments describing their function
- [ ] No absolute addresses (I0.0, Q0.0) appear in program blocks — tags are referenced symbolically

**Connects to:** Lesson 4.1 — OB1, the Scan Cycle, and the LAD Editor | With a complete hardware configuration and tag table in place, learners are ready to write their first ladder logic program in OB1.
