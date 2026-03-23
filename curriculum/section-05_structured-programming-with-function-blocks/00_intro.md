# Section 5 — Structured Programming with Function Blocks: Introduction

**Estimated segment duration:** 3–5 minutes
**Type:** Section orientation (structural — not counted in lesson totals)

---

## What You'll Learn in This Section

Your motor control program works. The problem is that it lives entirely in OB1, and if you need to control a second motor — or a third — you copy and paste logic and start manually managing which tags belong to which motor. That approach breaks down fast.

This section is about the Siemens block model and why it exists. Three lessons:

1. **The block model: OBs, FBs, FCs, and DBs** — what each block type is, what it's for, and when to use which. This is the most commonly misunderstood concept in Siemens PLC programming. Learners can usually copy a block structure from an instructor but cannot make independent decisions about which block type to use. This lesson fixes that.

2. **Building a Function Block and instance Data Block** — you'll build a `Motor_Control` FB from scratch, with properly typed inputs, outputs, and static variables. The lesson also covers optimized vs. non-optimized Data Blocks — a Siemens-specific concept that doesn't exist in Allen-Bradley or Mitsubishi and causes persistent confusion for anyone switching platforms.

3. **Lab: Refactor motor control into a reusable FB** — the motor control logic from Section 4 becomes a proper Function Block, instantiated twice for two independent motors. If both instances run independently, the lab is done.

---

## Why This Order Matters

Understanding the block model conceptually before building in software is not optional — if you don't know what an instance DB is for before creating one, you won't understand what you built. Lesson 5.1 loads the mental model; Lesson 5.2 puts it into practice; Lesson 5.3 tests it.

---

*Start with Lesson 5.1.*
