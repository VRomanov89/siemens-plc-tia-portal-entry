#### Lesson 4.4 — [Lab] Motor Start/Stop with Timer-Based Indicator and Start Counter

**Type:** Lab
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 4.3 — Timers (TON, TOF) and Counters (CTU, CTD) — Parameters and Practical Examples

---

**What is taught:**
The learner receives a multi-requirement program specification and must independently build a ladder logic program in OB1 that combines the motor start/stop circuit, a TON timer, and a CTU counter — connecting three different instruction types into one coherent program. After the attempt period, the instructor delivers a solution walkthrough, specifically addressing the most common structural errors: wrong rung order, incorrect timer reset logic, and counter resets that fire on every scan instead of on a rising edge.

**What the student learns:**
This lab is the first time learners must independently combine multiple instruction types to meet a multi-requirement specification — the critical leap from "I can follow along" to "I can solve a problem." Learners also discover how network order affects program behavior, since the timer's input condition references the motor output from a previous network.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Write a multi-network OB1 program that integrates bit logic, a TON timer, and a CTU counter to meet a defined specification
- [ ] Structure networks in the correct order so that outputs from earlier networks are available as inputs to later networks in the same scan
- [ ] Verify multi-instruction program behavior using PLCSIM online monitoring and a watch table showing ET, CV, and output states simultaneously
- [ ] Identify and correct at least two structural errors in a ladder logic program (demonstrated in solution walkthrough)

**Key concepts introduced:**
- N/A — this lesson applies and integrates concepts from Lessons 4.1 through 4.3; no new instructions are introduced.

**Common pitfalls:**
- Placing the timer network after the network that reads the timer's Q output — in a single scan, a timer's Q only reflects the state from the *previous* scan if the Q contact is evaluated before the timer instruction runs. Network order matters.
- Using a coil to reset the CTU instead of a contact on the R pin — the R input must be a Boolean contact, not a separate output coil writing to the same tag.
- Resetting the counter in the same condition as counting — if the reset condition is always TRUE when the count input fires, the counter will never accumulate past 1.
- Forgetting to add tags for `M_RunTimer_ET` or similar monitoring tags — watch tables require named tags; anonymous timer outputs must be routed through a named tag or accessed via the DB directly.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None (PLCSIM used for all testing)
- Files: New TIA Portal project `MotorLab_S4` — do not reuse prior projects; building from scratch reinforces the full workflow
- Reference: None — attempt from memory before reviewing solution

---

**Lab guide:**

*Problem statement:* You are programming a motor control panel with the following requirements:

**Inputs:**
- `DI_Motor_Start` — momentary NO pushbutton; starts the motor
- `DI_Motor_Stop` — momentary NC pushbutton (wired NC, appears as NC contact in software); stops the motor
- `DI_Counter_Reset` — momentary NO pushbutton; resets the start counter

**Outputs:**
- `DO_Motor_Run` — motor contactor output; latches on after START, releases on STOP
- `DO_RunTimer_Done` — indicator lamp; activates after the motor has been running continuously for 10 seconds; resets when the motor stops
- `DO_Counter_Q` — indicator lamp; activates when the motor has been started 5 or more times since the last counter reset

**Internal:**
- `M_RunTimer_ET` — tag to monitor elapsed time (optional, for watch table use)

**Requirements:**
1. Create a new TIA Portal project `MotorLab_S4` with an S7-1200 CPU 1214C
2. Build the tag table with all tags listed above, using the Section 3 naming convention
3. In OB1, write the following networks in order:
   - **Network 1:** Motor start/stop circuit with seal-in rung → `DO_Motor_Run`
   - **Network 2:** TON timer with IN = `DO_Motor_Run`, PT = T#10s → Q drives `DO_RunTimer_Done`
   - **Network 3:** CTU counter with CU rising-edge triggered by `DO_Motor_Run` rising edge, PV = 5, R = `DI_Counter_Reset` → Q drives `DO_Counter_Q`
4. Compile and download to PLCSIM
5. Open a watch table monitoring: `DO_Motor_Run`, timer ET, `DO_RunTimer_Done`, counter CV, `DO_Counter_Q`
6. Verify all requirements using the watch table

**Solution walkthrough:** Delivered by instructor after the attempt period. Covers the correct network structure, the rising-edge detection method for the CTU CU input, and the three most common errors seen in this exercise.

---

**Success criteria:**
- [ ] `DO_Motor_Run` energizes when `DI_Motor_Start` is pressed and remains energized after release
- [ ] `DO_Motor_Run` de-energizes when `DI_Motor_Stop` is pressed
- [ ] Timer ET begins accumulating as soon as `DO_Motor_Run` = TRUE and resets to 0 when `DO_Motor_Run` = FALSE
- [ ] `DO_RunTimer_Done` activates no earlier and no later than 10 seconds of continuous motor run time (verified in watch table: ET = T#10s at activation)
- [ ] Counter CV increments by exactly 1 each time the motor is started (not continuously while running)
- [ ] `DO_Counter_Q` activates when CV reaches 5 and remains active until `DI_Counter_Reset` is pressed
- [ ] Watch table shows ET, CV, and all output states updating correctly during PLCSIM simulation
- [ ] All tags use the naming convention from Section 3; no absolute addresses appear in OB1

**Connects to:** Lesson 5.1 — The Block Model: OBs, FBs, FCs, and DBs — When to Use Each | With working ladder logic in OB1, learners are ready to learn how to structure that logic into reusable function blocks — the step that separates procedural programming from professional, scalable code.
