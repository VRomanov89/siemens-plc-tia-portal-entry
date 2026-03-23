#### Lesson 1.1 — What is a PLC, How It Works, and Why Siemens

**Type:** Concept
**Estimated duration:** 12 minutes
**Prerequisites:** None

---

**What is taught:**
The instructor explains what a PLC is — a ruggedized industrial computer purpose-built for real-time, deterministic control of machines and processes — and how it differs from a general-purpose PC. The lesson walks through the scan cycle (read inputs → execute program logic → write outputs → repeat) using a simple diagram, explains what "deterministic execution" means and why it matters in industrial environments, and closes with a brief overview of why Siemens TIA Portal is the platform this course is built on: its market presence in global manufacturing and the professional value of Siemens-specific skills.

**What the student learns:**
Learners gain the foundational mental model that underpins every lesson that follows. They understand what the PLC is doing at every moment of operation and why the scan cycle creates the timing behaviors they'll encounter later in programming — including why a very short signal pulse can be missed. They also leave with a clear sense of why learning Siemens specifically is a high-value investment, not just "one more PLC brand."

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Identify the defining characteristics that distinguish a PLC from a general-purpose computer
- [ ] Describe the three phases of the PLC scan cycle in the correct order
- [ ] Explain why deterministic execution matters for industrial control applications
- [ ] Recognize the role of TIA Portal as the engineering software for Siemens S7-series PLCs

**Key concepts introduced:**
- **PLC (Programmable Logic Controller):** A ruggedized industrial computer designed for real-time, deterministic control of machine inputs and outputs in manufacturing and process environments.
- **Scan cycle:** The continuous loop a PLC executes — read all physical inputs, run the user program top to bottom, write all outputs — repeated hundreds of times per second.
- **Deterministic execution:** The guarantee that a PLC will complete its scan in a bounded, predictable time window, unlike a general-purpose OS where background processes can preempt foreground tasks.
- **TIA Portal (Totally Integrated Automation Portal):** Siemens' unified engineering software for configuring, programming, and commissioning S7-series PLCs and other automation devices — runs on a PC, communicates with the PLC over Ethernet.

**Common pitfalls:**
- Assuming the PLC reacts instantly to input changes — inputs are only sampled at the start of each scan, so a pulse shorter than one scan cycle can be missed entirely.
- Confusing TIA Portal (the software on your PC) with the PLC firmware (what runs on the CPU itself) — they are separate products with separate version numbers that must be compatible with each other.

**Materials:**
- Software: None
- Hardware: None
- Files: None
- Reference: None

**Connects to:** Lesson 1.2 — S7-1200, S7-1200 G2, and S7-1500 — Hardware Families Compared | With a working mental model of what a PLC is, learners are ready to evaluate which Siemens hardware platform is right for their application and what they need to follow the course.
