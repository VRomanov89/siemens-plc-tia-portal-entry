#### Lesson 2.2 — Installing TIA Portal and a First Look at the Interface

**Type:** Demo
**Estimated duration:** 12 minutes
**Prerequisites:** Lesson 2.1 — TIA Portal Versions, the 21-Day Trial, PC Requirements, and the PLCSIM Registration Wall

---

**What is taught:**
The instructor runs through the TIA Portal installation process on screen — launching the installer, selecting the correct components for this course (STEP 7 and PLCSIM only, skipping WinCC Runtime, drive packages, and other extras that consume disk space unnecessarily), and handling the reboot. After installation, the instructor opens TIA Portal, creates a blank project as a navigation sandbox, and delivers a structured tour of every major interface area: the Project Tree, Device View, Network View, Program Editor, Tag Table editor, and Watch Table. Each area is introduced with a single-sentence description of its purpose — enough for orientation, not deep enough to overwhelm.

*Addresses Consensus Topic §2.1 #1 (TIA Portal installation and navigation) and Learner Frustration §3.1 #3 (interface overwhelm on first launch).*

**What the student learns:**
Learners complete this lesson with a working TIA Portal installation and, critically, a spatial map of the interface — they know where everything lives before they need to use it. This removes the cognitive load of navigating an unfamiliar environment while also trying to learn programming concepts in later sections. The interface tour is designed specifically around the areas used in this course; nothing extraneous is shown.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Execute the TIA Portal installation, selecting only the components required for this course
- [ ] Navigate to each major interface area — Project Tree, Device View, Network View, Program Editor, Tag Table, Watch Table — without assistance
- [ ] Describe the purpose of each major interface area in one sentence
- [ ] Create a new blank TIA Portal project and confirm the software is functioning correctly

**Key concepts introduced:**
- **Project Tree:** The left-side navigator in TIA Portal that organizes all elements of a project — devices, program blocks, tag tables, and online access tools. Everything in a TIA Portal project is accessible from here.
- **Device View:** The hardware configuration workspace where you add CPUs and signal modules, configure device properties, and view I/O address assignments.
- **Network View:** The workspace for configuring connections between multiple devices — PLCs, HMIs, drives — within the same project. Not used in this course but important to recognize.
- **Program Editor:** The workspace where PLC programs are written — opens in LAD, FBD, or SCL depending on the selected programming language. Most of this course is spent here.
- **Tag Table:** The project-wide database of symbolic tag names and their associated memory addresses. Tags defined here are available throughout all program blocks.
- **Watch Table:** An online diagnostic tool for monitoring and forcing individual variable values while the PLC is running — used in Sections 3 through 6 for testing.

**Common pitfalls:**
- Installing all components by default — the full TIA Portal suite including WinCC Runtime Professional and drive packages can exceed 30GB of disk space. For this course, only STEP 7 and PLCSIM are needed; deselect everything else during installation.
- Expecting the interface to be static — TIA Portal's workspace is context-sensitive; the properties panel, inspector panel, and available toolbars all change depending on what is selected. This feels unpredictable at first but follows a consistent pattern once understood.

**Materials:**
- Software: TIA Portal V20 installer (downloaded in Lesson 2.1); Windows 10 or Windows 11 64-bit
- Hardware: None
- Files: None
- Reference: TIA Portal installation guide (included with installer download from SIOS)

**Connects to:** Lesson 3.1 — Creating a Project and Adding Your S7-1200 CPU | With TIA Portal installed and the interface familiar, learners are ready to create their first real project and configure hardware.
