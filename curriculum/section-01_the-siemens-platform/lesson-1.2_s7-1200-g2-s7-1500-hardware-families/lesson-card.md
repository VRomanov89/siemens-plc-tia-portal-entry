#### Lesson 1.2 — S7-1200, S7-1200 G2, and S7-1500 — Hardware Families Compared + What You Need for This Course

**Type:** Demo
**Estimated duration:** 15 minutes
**Prerequisites:** Lesson 1.1 — What is a PLC, How It Works, and Why Siemens

---

**What is taught:**
The instructor demonstrates a side-by-side comparison of the three Siemens hardware families learners will encounter. Using the Siemens product catalog on screen alongside physical hardware (or high-resolution product photos), the instructor identifies each CPU family, explains the key practical differences, and spends significant time on the S7-1200 G2 — the 2024 hardware revision that introduced a new physical form factor, incompatible signal modules, a relocated Profinet port, and an integrated fail-safe option. The lesson closes with a concrete "which one to buy" decision framework and a full hardware and software checklist for the rest of the course.

*Addresses Coverage Gap §2.3 #1: No existing course covers the S7-1200 G2 as of early 2026.*

**What the student learns:**
Learners gain the ability to identify which Siemens hardware generation they're working with — critical because G1 and G2 S7-1200 accessories are not interchangeable, and most tutorials available in 2026 still show G1 hardware without noting the distinction. They leave with a practical answer to "which one should I buy?" and a complete checklist of what they need to set up before Section 2. This lesson directly addresses the top hardware question in Siemens community forums (§3.2 #2, #7).

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] Identify the S7-1200 (G1), S7-1200 G2, and S7-1500 CPUs by physical appearance and nameplate markings
- [ ] List three hardware changes introduced in the S7-1200 G2 that affect signal module and accessory compatibility
- [ ] Select the appropriate Siemens hardware platform for a described application using the decision framework shown
- [ ] Compile the complete hardware and software requirements needed to follow this course

**Key concepts introduced:**
- **S7-1200 (G1):** Siemens' compact PLC family introduced ~2009; the standard starting point for new Siemens learners; wide ecosystem of signal modules and accessories.
- **S7-1200 G2:** Second-generation S7-1200 released in 2024; identified by "G2" on the CPU nameplate; physically different dimensions, new signal module lineup (not backward-compatible with G1 SMs), relocated Profinet port, integrated fail-safe option on select CPUs.
- **S7-1500:** Siemens' mid-to-high performance PLC family; larger I/O capacity, faster processing, native motion/safety capabilities; appropriate when the application exceeds what S7-1200 can handle — not the right starting point for first-time learners.
- **CPU nameplate:** The label on the physical CPU housing that identifies the exact model number, hardware generation (G2 marking), and firmware version — always check this before ordering accessories or following a tutorial.

**Common pitfalls:**
- Ordering G1 signal modules (e.g., SM 1221, SM 1222) for a G2 CPU — the physical housing and connector are different; they will not mount. Always confirm "G2" on the nameplate before purchasing accessories.
- Assuming the S7-1500 is "better for learning" because it's more powerful — it adds configuration complexity and cost without benefit at the beginner stage; the S7-1200 is the correct starting point.
- Following a YouTube tutorial or online course filmed on G1 hardware and not realizing that hardware config screenshots and physical wiring will differ on a G2 unit.

**Materials:**
- Software: None (Siemens product pages shown on screen — no TIA Portal required yet)
- Hardware: S7-1200 CPU 1214C (G1) and S7-1200 G2 CPU unit for side-by-side comparison if available; product photos acceptable as substitute; S7-1500 CPU for reference comparison
- Files: None
- Reference: Siemens S7-1200 system manual (for nameplate identification); Siemens S7-1200 G2 product announcement documentation; Siemens product selector at mall.industry.siemens.com

**Connects to:** Lesson 2.1 — TIA Portal Versions, the 21-Day Trial, PC Requirements, and the PLCSIM Registration Wall | With hardware selection settled, learners move to the software side of the setup — which TIA Portal version to use and how to get through installation without hitting the obstacles that cause most beginners to stall.
