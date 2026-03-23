# Course Outline: Getting Started with Siemens PLC Programming

**Generated:** 2026-03-22
**Source research document:** `curriculum/01_research_siemens-plc-tia-portal-entry.md`
**Target audience:** Engineers, technicians, and managers working in industrial automation
**Entry skill level:** No prior Siemens PLC experience; may have general automation or electrical background
**Course goal:** Build a complete, simple TIA Portal project from start to finish
**Course format:** Video course — TIA Portal screen recordings + top-down bench videos with physical hardware

---

## Course Overview

This is a free, structured video course that takes learners from zero Siemens knowledge to a complete, working TIA Portal project — covering platform selection, software setup, hardware configuration, ladder logic programming, structured programming with Function Blocks, and hardware commissioning. The course is built for engineers, technicians, and managers in industrial automation who need to get productive with Siemens PLCs quickly and without paying thousands of dollars for official SITRAIN training. Unlike every other free or low-cost alternative available in 2026, this course includes real hardware demonstrations — physical S7-1200 wiring, Ethernet connection, IP address assignment, and a live download — alongside PLCSIM-based simulation for learners who do not yet have hardware. The course also covers the S7-1200 G2 (2024 hardware revision), TIA Portal's PLCSIM export control registration process, optimized vs. non-optimized Data Blocks, and a PLC-only capstone project — all of which are absent from every competing resource at the free price point. The result is a course that prepares learners for real-world Siemens work, not just a simulation environment.

---

## Prerequisites

No prior Siemens PLC experience is required. The course is designed for complete beginners to Siemens and TIA Portal. Learners with a general automation or electrical background will find the early sections move quickly; learners with no automation background at all may want to supplement with a brief general PLC introduction before starting (any "what is a PLC" article or video — 15 minutes of background reading is sufficient).

**Helpful but not required:**
- Basic understanding of digital logic (TRUE/FALSE, AND, OR)
- Familiarity with any industrial control environment (electrical panels, control cabinets, sensors, actuators)

---

## Consolidated Course Materials

### Software
- TIA Portal V20 (trial version — 21-day, downloadable from Siemens SIOS; requires Siemens ID)
- PLCSIM V20 (included with TIA Portal trial; requires separate export control registration — submit early, approval takes 1–5 business days)
- Windows 10 or Windows 11 64-bit

### Hardware *(optional — PLCSIM covers all simulation-based exercises; hardware required only for Lesson 6.2 and the hardware delivery option for the capstone)*
- Siemens S7-1200 CPU 1214C — DC/DC/DC or DC/DC/Relay variant (either G1 or G2; course covers both)
- 24VDC DIN-rail power supply (appropriately rated for CPU + signal modules)
- Standard Ethernet patch cable (Cat5e or better)
- PC with a dedicated physical Ethernet port (USB-to-Ethernet adapters have known TIA Portal compatibility issues)
- Momentary NO pushbuttons ×4 (for capstone lab: Start, Reset, E-Stop, Proximity Sensor simulator)
- Indicator lamp or LED ×1 (for capstone: Cycle Complete output)

### PC Requirements
- RAM: 16GB recommended; 8GB minimum
- Storage: SSD required; 30GB minimum free space for TIA Portal installation
- Network: Dedicated physical Ethernet adapter for PLC communication
- OS: Windows 10 64-bit or Windows 11 64-bit

### Reference Documents *(all free, available on Siemens SIOS — support.industry.siemens.com)*
- Siemens S7-1200 System Manual (PDF)
- TIA Portal LAD/FBD/STL Programming Guide (PDF)
- TIA Portal Installation Guide (bundled with installer download)
- Siemens TIA Portal Programming Guidelines (PDF — professional coding standards)

---

## Course Structure at a Glance

| Section | Title | Lessons | Est. Duration | Types |
|---------|-------|---------|---------------|-------|
| 1 | The Siemens Platform | 2 | ~27 min | 1C / 1D |
| 2 | Setting Up TIA Portal | 2 | ~27 min | 2D |
| 3 | Hardware Configuration and Tags | 3 | ~45 min | 2D / 1L |
| 4 | Ladder Logic Fundamentals | 4 | ~54 min | 1C / 2D / 1L |
| 5 | Structured Programming with Function Blocks | 3 | ~45 min | 1C / 1D / 1L |
| 6 | Testing, Hardware Connection, and Capstone | 3 | ~70 min | 2D / 1Cap |
| **Total** | | **17** | **~4.5 hrs** | **3C / 8D / 3L / 1Cap** |

*C = Concept, D = Demo, L = Lab, Cap = Capstone*
*Section intro and conclusion segments (3–5 min each) add approximately 36–60 min of structural content not reflected in the lesson totals above.*

---

## Folder Structure

```
curriculum/
  02_course-overview.md               ← This file
  02_coverage-traceability.md         ← Research gap and learner request traceability
  section-01_the-siemens-platform/
    00_intro.md
    lesson-1.1_what-is-a-plc/
    lesson-1.2_s7-1200-g2-s7-1500-hardware-families/
    99_conclusion.md
  section-02_setting-up-tia-portal/
    00_intro.md
    lesson-2.1_tia-portal-versions-trial-plcsim-registration/
    lesson-2.2_installing-tia-portal-interface-tour/
    99_conclusion.md
  section-03_hardware-configuration-and-tags/
    00_intro.md
    lesson-3.1_creating-a-project-and-adding-your-cpu/
    lesson-3.2_plc-memory-areas-tag-tables-naming-conventions/
    lesson-3.3_lab-hardware-config-and-tag-table/
    99_conclusion.md
  section-04_ladder-logic-fundamentals/
    00_intro.md
    lesson-4.1_ob1-scan-cycle-lad-editor/
    lesson-4.2_contacts-coils-and-or-logic-motor-start-stop/
    lesson-4.3_timers-ton-tof-counters-ctu-ctd/
    lesson-4.4_lab-motor-start-stop-timer-indicator-start-counter/
    99_conclusion.md
  section-05_structured-programming-with-function-blocks/
    00_intro.md
    lesson-5.1_the-block-model-obs-fbs-fcs-dbs/
    lesson-5.2_building-fb-instance-db-optimized-vs-non-optimized/
    lesson-5.3_lab-refactor-motor-control-into-reusable-fb/
    99_conclusion.md
  section-06_testing-hardware-and-capstone/
    00_intro.md
    lesson-6.1_plcsim-online-monitoring-watch-tables-diagnostics/
    lesson-6.2_connecting-to-physical-s7-1200-ip-pgpc-download-troubleshooting/
    lesson-6.3_capstone-conveyor-control-system/
    99_conclusion.md
```
