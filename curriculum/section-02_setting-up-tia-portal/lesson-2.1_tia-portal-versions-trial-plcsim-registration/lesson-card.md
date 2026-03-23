#### Lesson 2.1 — TIA Portal Versions, the 21-Day Trial, PC Requirements, and the PLCSIM Registration Wall

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 1.2 — S7-1200, S7-1200 G2, and S7-1500 — Hardware Families Compared

---

**What is taught:**
The instructor demonstrates navigating the Siemens Industry Online Support (SIOS) download portal, explains the TIA Portal version history (V11 through V21) and why version-to-firmware matching matters in practice, and shows exactly where to find and download the correct trial version. The PLCSIM export control registration is covered step by step — what form to fill out, why it exists, how long the approval typically takes, and what learners should do in the meantime. The lesson closes with a specific PC requirements checklist and a clear recommendation on which TIA Portal version to install to follow this course.

*Addresses Coverage Gaps §2.3 #3 (licensing/trial realities) and §2.3 #6 (version compatibility). Directly addresses Learner Frustrations §3.1 #2 (PLCSIM export control), §3.1 #4 (version confusion), and §3.1 #7 (PC requirements underestimated). Answers Learner Request §3.2 #3 ("What version should I install?").*

**What the student learns:**
Learners gain the ability to navigate Siemens' download system confidently and identify the correct TIA Portal version for their hardware — eliminating the version confusion that derails learners mid-course. They leave knowing exactly what the PLCSIM export control process involves so it doesn't block them unexpectedly, and they have a concrete checklist to verify their PC is capable before committing to installation.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Navigate the Siemens SIOS download portal and locate the correct TIA Portal trial version for a given PLC firmware version
- [ ] Distinguish between STEP 7 Basic and STEP 7 Professional licenses and identify which is needed for this course
- [ ] Describe the PLCSIM export control registration process, including expected approval timeline and what to do while waiting
- [ ] Verify that a PC meets TIA Portal's minimum and recommended hardware requirements before beginning installation

**Key concepts introduced:**
- **TIA Portal version compatibility:** Each TIA Portal version supports specific PLC firmware ranges — using a mismatched combination results in configuration errors or blocked downloads at compile time. The rule: always match TIA Portal version to the firmware version stamped on your CPU.
- **STEP 7 Basic vs. Professional:** Basic supports S7-1200 programming only; Professional adds S7-300/400/1500 support and the SCL editor. The 21-day trial includes Professional; for this course, Basic capability is all that is required.
- **PLCSIM export control registration:** A legal compliance requirement under dual-use export regulations — Siemens must verify the requester's identity and location before releasing simulation software. The form is submitted through SIOS; approval takes 1–5 business days and is not waivable. This is not a technical problem — it is an administrative one that must be initiated early.
- **TIA Portal minimum PC requirements:** Minimum 8GB RAM (16GB strongly recommended); SSD required for acceptable compilation speed; Windows 10 or Windows 11 64-bit; dedicated physical Ethernet adapter for hardware communication (USB-to-Ethernet adapters have known compatibility issues with TIA Portal's PG/PC interface).

**Common pitfalls:**
- Starting the 21-day trial clock before the PLCSIM export control approval arrives — the clock runs regardless of whether PLCSIM is accessible. Submit the registration form immediately and use the wait time for Section 1 review.
- Installing the newest TIA Portal version by default without checking CPU firmware compatibility — a PLC shipped with older firmware may require an older TIA Portal version to configure correctly.
- Attempting to run TIA Portal on an HDD-based machine or with less than 8GB RAM — expect compilation to take minutes instead of seconds, simulation to crash, and general instability that is blamed on the software but is a hardware constraint.

**Materials:**
- Software: None required for this lesson (demonstrating download portal and registration process on screen only)
- Hardware: None
- Files: None
- Reference: Siemens SIOS download portal (support.industry.siemens.com); TIA Portal compatibility matrix (searchable on SIOS); PLCSIM export control registration form (accessible from the SIOS PLCSIM download page)

**Connects to:** Lesson 2.2 — Installing TIA Portal and a First Look at the Interface | With the correct version downloaded and the PLCSIM registration submitted, learners proceed through the installation process and get their first look at the TIA Portal workspace.
