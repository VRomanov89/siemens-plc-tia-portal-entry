#### Lesson 4.3 — Timers (TON, TOF) and Counters (CTU, CTD) — Parameters and Practical Examples

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 4.2 — Contacts, Coils, AND/OR Logic, and the Motor Start/Stop Circuit

---

**What is taught:**
The instructor introduces the four timer and counter instructions used throughout this course. For each instruction, the instructor explains every parameter, demonstrates its behavior in PLCSIM with online monitoring active (so learners can watch ET accumulate, Q energize, and CV increment in real time), and builds a minimal but realistic practical example. TON is demonstrated first with a delayed output — a warning lamp that activates 5 seconds after a motor starts. TOF is demonstrated with a coast-down delay — an exhaust fan that stays on for 10 seconds after a machine stops. CTU is demonstrated counting conveyor passes; CTD is shown briefly as the complement. The lesson closes with a brief note on IEC timers vs. legacy SIMATIC timers and why this course uses IEC exclusively.

*Addresses Consensus Topic §2.1 #6 (timers and counters — universal in every structured course).*

**What the student learns:**
Learners leave able to drop any of these four instructions into a program and configure them correctly from memory. More importantly, they understand the behavioral model — specifically the difference between the timer's IN pin (the enable condition), the Q output (the timed contact), and the ET output (elapsed time, useful for monitoring and logic), which is where most beginners get confused. The practical examples make the instructions immediately relatable to real machine scenarios.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Configure and test a TON (on-delay timer) instruction, correctly wiring the IN, PT, Q, and ET parameters
- [ ] Configure and test a TOF (off-delay timer) instruction and explain when TOF is preferable to TON
- [ ] Configure and test a CTU (count-up counter) and CTD (count-down counter), correctly wiring CU, R, PV, CV, and Q
- [ ] Combine a TON timer and a CTU counter in a single program and verify their interaction using PLCSIM watch tables

**Key concepts introduced:**
- **TON (on-delay timer):** Starts counting when IN = TRUE; Q energizes after the preset time (PT) is reached; resets immediately when IN = FALSE. ET (elapsed time) accumulates from 0 to PT. Used wherever an output should activate after a condition has been true for a specified duration.
- **TOF (off-delay timer):** Q energizes immediately when IN = TRUE; starts counting when IN goes FALSE; resets Q after PT elapses. Used for coast-down delays, exhaust fans, and any output that must stay on briefly after its trigger is removed.
- **CTU (count-up counter):** Increments CV (current value) on each rising edge of CU (count up input); Q energizes when CV ≥ PV (preset value); R (reset) input clears CV to 0. Used for counting events — parts produced, cycles completed, starts accumulated.
- **CTD (count-down counter):** Loads PV into CV on rising edge of LD (load); decrements CV on each rising edge of CD; Q energizes when CV ≤ 0. Used when counting down to zero is more natural than counting up to a target.
- **IEC timers vs. SIMATIC timers:** TIA Portal supports both IEC-compliant timers (TON, TOF, TP — used in this course) and legacy SIMATIC timers (T0–T255 from the S7-300/400 era). IEC timers are the standard for all new S7-1200/1500 projects; SIMATIC timers exist only for backward compatibility and should not be used in new programs.

**Common pitfalls:**
- Connecting the timer Q output directly to a coil without storing the timer instance in a DB — IEC timers are function blocks and require an instance Data Block; TIA Portal creates this automatically when the instruction is placed, but learners must understand that the timer state lives in that DB, not in a global memory area.
- Confusing PT (preset time — input, how long to count) with ET (elapsed time — output, how long it has counted) — a common source of errors when learners try to use ET as a preset, which has no effect.
- Resetting a CTU with a coil on R instead of a contact — the R pin is a Boolean input, not a coil; connecting a tag to it that is permanently TRUE prevents the counter from ever counting.
- Expecting the counter to reset automatically when Q energizes — CTU does not self-reset; an explicit reset input or Reset coil must be used.

**Materials:**
- Software: TIA Portal V20 with PLCSIM V20
- Hardware: None
- Files: Continuing TIA Portal project from Lesson 4.2; instructor adds timer and counter examples in new networks within OB1
- Reference: Siemens TIA Portal LAD/FBD/STL programming guide — Chapter 5 (timer instructions) and Chapter 6 (counter instructions)

**Connects to:** Lesson 4.4 — [Lab] Motor Start/Stop with Timer-Based Indicator and Flash Counter | Learners apply contacts, coils, timers, and counters together in an independent lab — the first time all four instruction types are combined in a single program.
