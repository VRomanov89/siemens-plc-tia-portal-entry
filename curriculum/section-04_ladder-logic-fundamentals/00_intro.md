# Section 4 — Ladder Logic: Contacts, Coils, Timers, and Counters: Introduction

**Estimated segment duration:** 3–5 minutes
**Type:** Section orientation (structural — not counted in lesson totals)

---

## What You'll Learn in This Section

This is the programming section. Four lessons — one concept, two demos, one lab — and by the end you'll have written a working ladder logic program from scratch, tested it in PLCSIM, and proven you can do it without following the instructor step for step.

1. **OB1, the scan cycle, and the LAD editor** — how the CPU calls your program, what a network and a rung are, and how to navigate TIA Portal's LAD editor before you start writing logic.

2. **Contacts, coils, AND/OR logic, and the motor start/stop circuit** — the three building blocks of every ladder logic program, applied to the universal first exercise: a motor that starts, latches, and stops on demand.

3. **Timers and counters** — TON, TOF, CTU, and CTD with parameters explained and practical examples demonstrated. These four instructions appear in almost every real PLC program.

4. **Lab: Motor start/stop with timer-based indicator and start counter** — you build it independently from a problem statement. No follow-along.

---

## The Motor Start/Stop Circuit

The motor start/stop circuit with a seal-in rung is the universal first ladder logic exercise — every PLC platform, every training program, every automation engineer learned it at some point. There's a reason for that: it's simple enough to grasp immediately but teaches the most important concept in ladder logic — the latching output. Get this one right and the pattern generalizes to almost everything you'll build later.

---

*Start with Lesson 4.1.*
