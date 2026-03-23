# Section 3 — Hardware Configuration and Tags: Introduction

**Estimated segment duration:** 3–5 minutes
**Type:** Section orientation (structural — not counted in lesson totals)

---

## What You'll Learn in This Section

This is where you start building something real. By the end of this section you'll have a fully configured TIA Portal project — hardware, I/O addresses, and a professional tag table — ready to receive your first ladder logic program.

Three lessons:

1. **Creating a project and adding your S7-1200 CPU** — the project creation workflow, choosing the right CPU model, navigating Device View, adding signal modules, and compiling hardware configuration without errors.

2. **PLC memory areas and tag tables** — what I, Q, M, and DB memory actually are and why Siemens structures them this way, plus how to build a tag table that a professional would be comfortable reading.

3. **Lab: Build a hardware configuration and structured tag table** — you do it independently. No follow-along. A problem statement, a target application, and success criteria. This is the first test of whether the previous two lessons landed.

---

## Why This Order

Hardware before tags, tags before code. Every program block you write from here forward will reference tags that live in a tag table, and those tags reference I/O addresses that live in the hardware configuration. Building these in the right order — and doing it right the first time — saves significant rework later.

The naming conventions introduced in Lesson 3.2 apply for the rest of the course. Getting them established now means every lesson from 4.1 onward uses professional, readable code.

---

*Start with Lesson 3.1.*
