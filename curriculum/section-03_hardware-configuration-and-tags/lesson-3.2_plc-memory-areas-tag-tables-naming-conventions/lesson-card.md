#### Lesson 3.2 — PLC Memory Areas (I/Q/M/DB), Tag Tables, and Naming Conventions

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 3.1 — Creating a Project and Adding Your S7-1200 CPU

---

**What is taught:**
The instructor explains the four Siemens PLC memory areas — I (input image), Q (output image), M (bit memory/flags), and DB (data block) — in plain language, with diagrams showing where each lives in the CPU and when the PLC reads and writes to each. The lesson then moves into TIA Portal's tag table editor, where the instructor builds a complete tag table for a motor control application, demonstrating: naming conventions (prefix-based naming using area and function), data type selection (Bool, Int, Real, Word), the difference between absolute and symbolic addressing, and how to set a comment for every tag. The instructor also shows why symbolic addressing is the professional standard and what happens in the program editor when you try to use absolute addresses directly.

*Addresses Coverage Gap §2.3 #5 (memory areas explained clearly) and Consensus Topics §2.1 #4 (tag tables and symbolic addressing). Addresses Common Knowledge Gap §3.3 #2 (tag addressing and memory areas not well understood after beginner courses). Addresses Depth Imbalance §2.4 (naming conventions under-taught).*

**What the student learns:**
Learners gain a clear mental model of where every variable in a PLC program lives — which memory area it belongs to and how TIA Portal addresses it. They leave with a naming convention they can apply immediately and a habit of building a complete tag table before writing any program logic. This directly corrects the gap where learners can copy instructor code but don't understand what memory they're actually referencing.

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Describe the purpose of each Siemens PLC memory area — I, Q, M, and DB — and identify what type of data belongs in each
- [ ] Create a tag table in TIA Portal with correctly named, typed, and commented tags for a described application
- [ ] Apply a prefix-based naming convention consistently across all tags in a project
- [ ] Distinguish between absolute addressing (I0.0, Q0.1) and symbolic addressing, and explain why symbolic is the professional standard

**Key concepts introduced:**
- **Input image (I):** A snapshot of all physical input states taken at the start of each scan cycle — the PLC reads from this area, not directly from hardware, during program execution. Addressed as I[byte].[bit] (e.g., I0.0, I1.3).
- **Output image (Q):** A buffer of output states that the PLC writes to during program execution — physical outputs are only updated at the end of each scan. Addressed as Q[byte].[bit] (e.g., Q0.0, Q0.4).
- **Bit memory (M):** Internal flag storage with no physical I/O connection — used for intermediate logic, latches, flags, and variables that exist only in software. Addressed as M[byte].[bit] (e.g., M0.0, M5.2).
- **Data block (DB):** Structured memory storage for larger or typed data sets — integers, reals, arrays, and structs. Used by function blocks (instance DBs) and as global variable storage (global DBs). Addressed symbolically through the DB name and variable name.
- **Symbolic addressing:** Referencing a tag by its name (e.g., `Motor1_Start`) rather than its absolute address (I0.0) — the professional standard in TIA Portal; makes programs readable, maintainable, and portable across hardware revisions.
- **Naming convention (prefix-based):** A consistent tag naming pattern that encodes the tag's type and function — e.g., `DI_` for digital input, `DO_` for digital output, `M_` for memory flag, followed by a descriptive functional name: `DI_Motor1_Start`, `DO_Motor1_Run`, `M_Motor1_Fault`.

**Common pitfalls:**
- Using raw absolute addresses (I0.0, Q0.1) in program blocks instead of symbolic tag names — makes programs impossible to read or maintain and breaks portability when hardware is revised.
- Creating tags without comments — a tag table without comments is a liability; six months later, `M5.3` means nothing without a comment explaining its function.
- Using generic names like `Input1`, `Output2`, `Flag3` — defeats the purpose of symbolic addressing entirely; names must encode function, not position.
- Selecting the wrong data type — using Int for a bit that should be Bool, or Real for a count that should be Int — causes type mismatch errors in program blocks and wastes memory.

**Materials:**
- Software: TIA Portal V20
- Hardware: None
- Files: TIA Portal project created in Lesson 3.1 (used as the base for building the tag table)
- Reference: Siemens S7-1200 system manual — Section 6 (PLC concepts: memory areas and addressing)

**Connects to:** Lesson 3.3 — [Lab] Build a Hardware Configuration and Structured Tag Table | Learners apply everything from Lessons 3.1 and 3.2 independently — creating hardware config and a complete tag table from a problem statement without instructor guidance.
