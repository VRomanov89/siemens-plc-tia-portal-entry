# Coverage Traceability

**Course:** Getting Started with Siemens PLC Programming
**Source research document:** `curriculum/01_research_siemens-plc-tia-portal-entry.md`
**Generated:** 2026-03-22
**Quality check status:** PASSED — all gaps, frustrations, and requests covered; all exclusions compliant

---

## Research Gaps Addressed (§2.3)

| Gap (from research doc §2.3) | Addressed in |
|------------------------------|-------------|
| S7-1200 G2 explicitly covered — no existing course addresses 2024 hardware revision | Lesson 1.2 |
| Physical hardware connection workflow in full detail — IP assignment, PG/PC interface, accessible devices scan, download dialog | Lesson 6.2 |
| TIA Portal licensing and trial realities — export control for PLCSIM, STEP 7 Basic vs. Professional, trial clock behavior | Lesson 2.1 |
| Optimized vs. non-optimized Data Block access — not explained in any beginner course; critical for integration work | Lesson 5.2 |
| Memory areas explained clearly (I, Q, M, DB) — persistent knowledge gap vs. other PLC platforms | Lesson 3.2 |
| TIA Portal version compatibility with PLC firmware — version mismatch causes failed downloads; courses teach a version without explaining the rules | Lessons 2.1, 3.1 |
| PLC-only capstone project — most capstones introduce HMI/WinCC; no pure PLC capstone exists in free market | Lesson 6.3 |

---

## Learner Frustrations Addressed (§3.1)

| Frustration (from research doc §3.1) | Addressed in |
|--------------------------------------|-------------|
| Cannot connect TIA Portal to the physical PLC — #1 forum complaint; PG/PC interface, no IP on new PLC, firewall, wrong NIC | Lesson 6.2; Common Pitfall in Lessons 6.2 |
| TIA Portal installation and PLCSIM download obstacles — export control registration not mentioned in any course | Lesson 2.1; Common Pitfall in Lesson 2.1 |
| Software overwhelm — TIA Portal interface is dense and context-sensitive | Lesson 2.2; Common Pitfall in Lesson 2.2 |
| Version confusion — courses filmed on V15/V16 don't match V20 menus; learners get lost | Lessons 1.2, 2.1; Common Pitfall in Lesson 2.1 |
| Data block download resets runtime values — production trap; not covered in any beginner course | Lesson 5.2; Common Pitfall in Lesson 5.2 |
| Optimized vs. non-optimized data blocks — disorienting for learners from Allen-Bradley or Mitsubishi | Lesson 5.2; Common Pitfall in Lesson 5.2 |
| PC hardware requirements underestimated — TIA Portal crashes on underpowered machines; not mentioned in courses | Lesson 2.1; Common Pitfall in Lesson 2.2 |

---

## Learner Requests Addressed (§3.2)

| Request (from research doc §3.2) | Addressed in |
|----------------------------------|-------------|
| "Show me connecting to a real PLC, not just simulation" | Lesson 6.2 |
| "Explain when to use S7-1200 vs S7-1500" | Lesson 1.2 |
| "What version of TIA Portal should I install?" | Lesson 2.1 |
| "Give me a complete project, not just exercises" | Lesson 6.3 (Capstone) |
| "Explain the block model clearly" | Lessons 5.1, 5.2 |
| "Help with Siemens-specific concepts — scan cycle in TIA Portal terms, PLCSIM vs. real hardware" | Lessons 1.1, 4.1, 6.1, 6.2 |

---

## Exclusions Compliance

The following topics were excluded per the course parameters. None appear in any lesson:

| Excluded Topic | Status |
|---|---|
| HMI / WinCC | Excluded — capstone is explicitly PLC-only (Coverage Gap §2.3 #7) |
| Motion control | Excluded — S7-1500 motion capability noted as a hardware feature only (Lesson 1.2) |
| Safety PLCs | Excluded — S7-1200 G2 fail-safe option identified for hardware recognition only (Lesson 1.2) |
| SCADA | Excluded — not mentioned anywhere |
| Profibus / Profinet (beyond basics) | Excluded — Profinet mentioned only in hardware identification (Lesson 1.2) and accessible devices scan mechanism (Lesson 6.2); no Profinet configuration taught |
| SCL (Structured Control Language) | Excluded — STEP 7 Professional includes SCL editor (noted in Lesson 2.1) but SCL is not used or taught; all programming is in LAD |
| FBD (Function Block Diagram) | Excluded — not mentioned; all programming is in LAD |
| Legacy platforms (S7-300 / S7-400) | Excluded — S7-300/400 mentioned only to identify IEC timers as replacement for legacy SIMATIC timers (Lesson 4.3); no S7-300/400 programming taught |

---

## Consensus Topics Coverage (§2.1)

All 10 consensus topics from the research document appear in the curriculum:

| Consensus Topic (§2.1) | Covered in |
|---|---|
| TIA Portal software installation and navigation | Lessons 2.1, 2.2 |
| Creating a new TIA Portal project | Lesson 3.1 |
| Hardware configuration | Lessons 3.1, 3.3 (Lab) |
| Tag tables and symbolic addressing | Lessons 3.2, 3.3 (Lab) |
| Ladder Logic (LAD) basics — NO/NC contacts, coils, AND/OR | Lessons 4.2, 4.4 (Lab) |
| Timers and Counters — TON, TOF, CTU, CTD | Lessons 4.3, 4.4 (Lab) |
| Simulation with PLCSIM | Lessons 4.1–4.4, 6.1 |
| Block model — OBs, FBs, FCs, DBs | Lessons 5.1, 5.2, 5.3 (Lab) |
| Downloading a project to the PLC | Lessons 6.1, 6.2 |
| Diagnostics and online monitoring | Lessons 6.1, 6.2 |
