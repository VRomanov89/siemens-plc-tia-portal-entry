# Section 4 — Ladder Logic: Contacts, Coils, Timers, and Counters: Conclusion

**Estimated segment duration:** 3–5 minutes
**Type:** Section recap (structural — not counted in lesson totals)

---

## What You Covered in This Section

Four lessons. The core of ladder logic programming — and if you got through the lab without copying the instructor, you are ahead of most people who have taken similar courses.

**From Lesson 4.1:**
- OB1 is the main cyclic program block — the CPU calls it once per scan, executes every network top to bottom, then updates I/O and repeats
- Networks are logical units within a program block — they execute sequentially; what one network writes is available to the next in the same scan
- The LAD editor is navigable before you know how to program — instruction placement, network creation, and tag assignment are mechanical skills separate from logic design

**From Lesson 4.2:**
- NO contact = passes when tag is TRUE; NC contact = passes when tag is FALSE; output coil = writes TRUE when rung evaluates TRUE
- AND logic = contacts in series; OR logic = parallel branches
- The seal-in rung is the foundational latching pattern — the output's own contact in parallel with the start condition keeps the rung latched after a momentary input goes away
- A STOP button wired NC in hardware must be treated as NC in software — this is a safety design standard, not a convention

**From Lesson 4.3:**
- TON: starts counting when IN goes TRUE, Q energizes after PT elapses, resets when IN goes FALSE
- TOF: Q energizes immediately when IN goes TRUE, stays on for PT after IN goes FALSE
- CTU: counts rising edges on CU, Q energizes when CV ≥ PV, R input resets CV to 0
- IEC timers require instance DBs — TIA Portal creates them automatically, but the timer state lives in that DB

**From Lesson 4.4 (Lab):**
- Network order matters — a timer Q contact read in an earlier network reflects the previous scan's state, not the current scan's newly computed state
- Rising-edge detection on CTU's CU input is required to count motor starts correctly — a level input causes the counter to run up continuously while the motor runs
- Multi-instruction programs are tested most efficiently with a watch table showing all relevant variables simultaneously

---

## Before You Continue

Make sure you have:
- [ ] A working motor start/stop circuit with seal-in rung in OB1
- [ ] A TON timer and CTU counter correctly configured and tested in PLCSIM
- [ ] A watch table that verifies ET, CV, and output states during simulation
- [ ] No absolute addresses anywhere in your program blocks

---

## What's Next

Section 5 is about structure. Your program works — but it's all in OB1, which doesn't scale. You'll learn the Siemens block model, build your first Function Block with an instance Data Block, and refactor your motor control logic into a reusable FB that can be instantiated as many times as needed.

*See you in Section 5.*
