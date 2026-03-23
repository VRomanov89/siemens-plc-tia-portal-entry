#### Lesson 5.3 — [Lab] Refactor Motor Control into a Reusable FB

**Type:** Lab
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 5.2 — Building a Function Block, Instance Data Block, and Optimized vs. Non-Optimized DBs

---

**What is taught:**
The learner refactors the motor start/stop circuit from OB1 into a properly structured `Motor_Control` FB, then instantiates it twice from OB1 with independent I/O tag assignments — proving that one FB definition can drive two completely independent motors. After the attempt period, the instructor delivers a solution walkthrough focused on the most common structural errors: global tag references inside the FB, timer instances not declared as Static, and both instances sharing the same instance DB.

**What the student learns:**
This lab delivers the tangible payoff of the block model — learners see firsthand that writing logic once and instantiating it multiple times is not a theoretical benefit; it's a concrete reduction in the amount of code that needs to be written, tested, and maintained. The two-instance requirement forces learners to confront and resolve the most common FB mistakes in a controlled environment before the capstone.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Create a reusable `Motor_Control` FB with correctly structured Input, Output, and Static interface variables
- [ ] Write self-contained ladder logic inside the FB using only `#` local interface variables — no global tag references
- [ ] Call the FB from OB1 twice, assigning a unique instance DB to each call and wiring different physical I/O tags to each instance
- [ ] Verify that both FB instances operate independently by running both motors simultaneously in PLCSIM without interference between instances

**Key concepts introduced:**
- N/A — this lesson applies concepts from Lessons 5.1 and 5.2; no new block types or instructions are introduced.

**Common pitfalls:**
- Assigning the same instance DB to both FB calls — both instances then share state; starting Motor 1 will also latch Motor 2. Each call must receive a unique, dedicated instance DB.
- Referencing global I/O tags (e.g., `DI_Motor1_Start`) directly inside the FB logic instead of the FB's `#Start` input pin — the FB will always control Motor 1 regardless of what is wired to the input pin at the OB1 call.
- Forgetting to declare the TON timer as a Static variable in the FB interface — if the timer is added as a stand-alone instruction referencing an external DB, it breaks encapsulation and the timer state is shared across instances.
- Leaving the original OB1 motor control logic (from Lesson 4.4) in place alongside the new FB call — this causes both the raw rung and the FB output to write to the same `DO_Motor_Run` tag, producing unpredictable behavior.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None
- Files: `MotorLab_S4` project from Lesson 5.2; add the following tags to the existing tag table before starting: `DI_Motor2_Start` (Bool, I1.0), `DI_Motor2_Stop` (Bool, I1.1), `DO_Motor2_Run` (Bool, Q0.2)
- Reference: None — attempt from knowledge gained in Lessons 5.1 and 5.2 before reviewing solution

---

**Lab guide:**

*Problem statement:* Refactor the motor start/stop circuit from the `MotorLab_S4` project into a reusable Function Block, then use it to control two independent motors from OB1.

**Requirements:**

1. In the `MotorLab_S4` project, add a new Function Block named `Motor_Control` (FB1)

2. Define the FB interface:
   - **Input:** `Start` (Bool), `Stop` (Bool)
   - **Output:** `Run` (Bool)
   - **Static:** `Running` (Bool), `RunTimer` (TON)

3. Write the motor start/stop circuit with seal-in rung inside the FB using only `#` local variables:
   - Network 1: `#Start` OR `#Running` in series with `#Stop` NC → `#Running` coil (seal-in latch)
   - Network 2: `#Running` contact → `#Run` output coil
   - Network 3: TON with IN = `#Running`, PT = T#10s, instance = `#RunTimer`

4. In OB1, remove the existing motor start/stop rungs from Lesson 4.4 (or place them in a commented-out network)

5. Call `Motor_Control` (FB1) twice in OB1:
   - **Instance 1:** DB name `Motor1_DB` — wire `DI_Motor1_Start` → Start, `DI_Motor1_Stop` → Stop, Run → `DO_Motor1_Run`
   - **Instance 2:** DB name `Motor2_DB` — wire `DI_Motor2_Start` → Start, `DI_Motor2_Stop` → Stop, Run → `DO_Motor2_Run`

6. Compile the full project (hardware + software) and download to PLCSIM

7. Test independence: start Motor 1 and confirm Motor 2 is not affected; start Motor 2 and confirm Motor 1 is not affected; stop each independently

**Solution walkthrough:** Delivered by instructor after the attempt period. Highlights the three most common errors: shared instance DB, global tag references inside the FB, and the original OB1 rungs left active in parallel with the FB calls.

---

**Success criteria:**
- [ ] `Motor_Control` FB exists with the correct Input, Output, and Static interface — no global tag references anywhere in the FB logic
- [ ] `Motor1_DB` and `Motor2_DB` exist as separate, dedicated instance DBs for each FB call
- [ ] Pressing `DI_Motor1_Start` energizes `DO_Motor1_Run` and latches — `DO_Motor2_Run` is not affected
- [ ] Pressing `DI_Motor2_Start` energizes `DO_Motor2_Run` and latches — `DO_Motor1_Run` is not affected
- [ ] Each motor stops independently when its own Stop input is triggered
- [ ] Project compiles without errors or warnings
- [ ] No original OB1 motor control rungs remain active in parallel with the FB calls

**Connects to:** Lesson 6.1 — PLCSIM Simulation, Online Monitoring, Watch Tables, and the Diagnostics Buffer | With structured, FB-based code in place, learners move into the testing and deployment section — using TIA Portal's diagnostic tools and, for those with physical hardware, downloading to a real S7-1200.
