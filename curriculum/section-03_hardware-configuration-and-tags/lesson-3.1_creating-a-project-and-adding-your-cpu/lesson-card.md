#### Lesson 3.1 — Creating a Project and Adding Your S7-1200 CPU

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 2.2 — Installing TIA Portal and a First Look at the Interface

---

**What is taught:**
The instructor creates a new TIA Portal project from scratch, selects an S7-1200 CPU from the hardware catalog, and walks through the Device View interface in detail — what each panel shows, how to read I/O address assignments, and how to add digital input and output signal modules to expand the CPU's I/O count. The lesson concludes with compiling the hardware configuration, interpreting the compile output window, and fixing a deliberately introduced error so learners see what a hardware compile error looks like and how to resolve it.

*Addresses Consensus Topics §2.1 #2 (creating a new project) and §2.1 #3 (hardware configuration).*

**What the student learns:**
Learners leave able to independently create a TIA Portal project, select the correct CPU model for a given application, and configure basic hardware — including the critical step of matching the CPU model and firmware version in software to what is physically on their bench. They also understand what "compile hardware" produces and why it must succeed before any program can be downloaded.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Create a new TIA Portal project and assign a project name and storage path
- [ ] Add an S7-1200 CPU to a project by selecting the correct model and firmware version from the hardware catalog
- [ ] Add digital input and digital output signal modules in Device View and identify their auto-assigned I/O addresses
- [ ] Compile the hardware configuration and interpret the output to confirm a successful compile or locate an error

**Key concepts introduced:**
- **Hardware catalog:** The component library in TIA Portal's Device View used to add CPUs, signal modules, communication modules, and other hardware. Components are selected by exact order number to match physical hardware.
- **Firmware version matching:** Each CPU in the hardware catalog is tied to a specific firmware revision — the firmware version configured in software must match the firmware version installed on the physical CPU, or the download will fail.
- **I/O address assignment:** When signal modules are added in Device View, TIA Portal automatically assigns input addresses (I0.0–I0.7, I1.0–I1.7, etc.) and output addresses (Q0.0–Q0.7, etc.) — these are the absolute addresses that tags will reference.
- **Hardware compile:** The process of validating the hardware configuration — checking for address conflicts, unsupported module combinations, and configuration errors — before allowing a download to the PLC.

**Common pitfalls:**
- Selecting a CPU model that doesn't match the physical hardware order number — the S7-1200 family has many variants (1211C, 1212C, 1214C, 1215C, 1217C); selecting the wrong one results in a firmware/hardware mismatch error at download.
- Selecting the wrong firmware version in the hardware catalog — if the physical CPU has firmware V4.5 and the project is configured for V4.4, the download will be rejected. Always check the CPU nameplate for the installed firmware version.
- Skipping the hardware compile and going straight to program download — TIA Portal will catch the omission but the error message is not always intuitive; building the habit of compiling hardware first prevents confusion.

**Materials:**
- Software: TIA Portal V20
- Hardware: None required for this lesson (configuring in software only; hardware connection is covered in Section 6)
- Files: None
- Reference: Siemens S7-1200 system manual — Section 2 (CPU specifications and order numbers)

**Connects to:** Lesson 3.2 — PLC Memory Areas (I/Q/M/DB), Tag Tables, and Naming Conventions | With hardware configured and I/O addresses assigned, learners move to the tag layer — defining symbolic names for every I/O point and internal variable they'll use in programming.
