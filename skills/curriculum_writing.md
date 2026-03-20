# Skill: Curriculum Writing Standards

This skill defines the quality standards, formats, and rules for writing course curriculum content within this system. Any workflow that generates lesson outlines, module structures, learning objectives, or lab guides must read and apply these standards before producing output.

---

## 1. Learning Objectives

### What a learning objective is

A learning objective is a single, measurable statement describing what the learner will be able to **do** after completing a lesson or module — not what they will be exposed to. It answers the question: "If a learner has truly absorbed this lesson, what can they now do that they couldn't do before?"

### Rules for writing objectives

- **Start with an action verb** — never start with "understand," "know," "learn," or "appreciate." These are not measurable.
- **One behavior per objective** — if it requires "and," it's two objectives.
- **Observable and testable** — could you design a test or task that proves this objective was met? If not, rewrite it.
- **Written from the learner's perspective** — "Learners will be able to..." not "This lesson covers..."
- **3–5 objectives per lesson** is the target range. Fewer suggests the lesson is too thin. More suggests the lesson is too broad.

### Bloom's Taxonomy — choose verbs by the right cognitive level

| Level | When to use | Example verbs |
|-------|-------------|---------------|
| **Remember** | For foundational facts, terminology, or sequences | identify, name, list, recall, recognize, define, label |
| **Understand** | For concepts the learner must explain or interpret | explain, describe, summarize, classify, distinguish, interpret |
| **Apply** | For procedures the learner must execute in new situations | use, demonstrate, execute, implement, solve, configure, write |
| **Analyze** | For breaking down systems to understand their parts | differentiate, compare, examine, test, troubleshoot, diagnose |
| **Evaluate** | For making judgements or selecting among options | select, justify, decide, argue, assess, recommend |
| **Create** | For building something new from components | design, construct, build, develop, produce, program |

**Beginner courses** should be weighted toward Remember, Understand, and Apply. Analyze and Evaluate appear at mid-course as complexity increases. Create is reserved for the capstone.

---

## 2. Lesson Types

Every lesson must be assigned one of four types. The type determines what format, depth, and materials the lesson requires.

### Concept
A lesson that introduces and explains ideas, terminology, or frameworks. No hands-on work in TIA Portal or on hardware. Used for orientation, theory, and context-setting.

- **Format:** Talking head, slides, or diagram walkthrough
- **Objectives:** Weighted toward Remember and Understand
- **Materials:** None (or reference links only)
- **Lab guide:** Not required

### Demo
A lesson where the instructor demonstrates a workflow or procedure in TIA Portal or on hardware. The learner watches and follows along. Not graded — the learner replicates what they see.

- **Format:** Screen recording (TIA Portal) or top-down bench video (hardware)
- **Objectives:** Weighted toward Apply — the learner should be able to replicate the steps
- **Materials:** TIA Portal project file (if applicable), hardware (if applicable)
- **Lab guide:** Optional — a brief "try it yourself" prompt may follow

### Lab
A lesson where the learner is given a problem statement or task and must complete it independently before (or after) seeing the solution. This is the primary vehicle for skill consolidation.

- **Format:** Problem statement first, then solution walkthrough
- **Objectives:** Weighted toward Apply and Analyze
- **Materials:** Must be fully specified — software version, hardware model, project files, any physical components
- **Lab guide:** Required. Must include: step-by-step outline, success criteria, and common failure modes
- **Success criteria:** Defined as specific, observable outcomes — not "the program works" but "the motor output activates within 500ms of pressing the Start button and latches until Stop is pressed"

### Capstone
A summative project lesson that integrates multiple skills from prior modules. No new instruction — the learner applies everything learned. The capstone includes a full problem statement, deliverables, and evaluation criteria.

- **Format:** Problem statement video + optional solution walkthrough video (post-submission)
- **Objectives:** Weighted toward Apply, Analyze, and Create
- **Materials:** Fully specified — treat as the most demanding lab
- **Deliverables:** Must be clearly defined — what does the learner submit or demonstrate?
- **Evaluation criteria:** Defined and specific — what does a passing deliverable look like?

---

## 3. Lesson Card Format

Every lesson in the outline must use this exact format. Do not omit fields — if a field is not applicable, write "N/A" rather than leaving it blank.

```markdown
#### Lesson X.Y — [Title]

**Type:** Concept | Demo | Lab | Capstone
**Estimated duration:** X–Y minutes
**Prerequisites:** [Lesson numbers and titles, or "None" if this is the first lesson]

**What is taught:**
[2–4 sentences from the instructor's perspective. What content does this lesson cover? What does the instructor explain, demonstrate, or assign?]

**What the student learns:**
[2–4 sentences from the learner's perspective. What knowledge, skill, or capability does the learner gain? How does it connect to their real-world role or the course goal?]

**Learning objectives:**
By the end of this lesson, learners will be able to:
- [ ] [Action verb] + [observable behavior] + [context or condition if needed]
- [ ] [Action verb] + [observable behavior]
- [ ] [Action verb] + [observable behavior]

**Key concepts introduced:**
- [Term or concept]: [One-sentence definition or description]
- [Term or concept]: [One-sentence definition or description]

**Common pitfalls:**
- [Specific mistake or misconception learners typically have at this point]
- [Specific mistake or misconception]

**Materials:**
- Software: [e.g., TIA Portal V20, PLCSIM V20 — or "None"]
- Hardware: [e.g., Siemens S7-1200 CPU 1214C, 24VDC power supply — or "None"]
- Files: [e.g., Starter project file, completed reference file — or "None"]
- Reference: [e.g., Siemens S7-1200 System Manual Section 4.2 — or "None"]

**Lab guide:** *(Required for Lab and Capstone types; omit for Concept and Demo)*
1. [Step 1 — what the learner is instructed to do]
2. [Step 2]
3. [Step 3]
...

**Success criteria:** *(Required for Lab and Capstone types; omit for Concept and Demo)*
- [ ] [Specific, observable outcome that confirms the learner completed the task correctly]
- [ ] [Specific, observable outcome]

**Connects to:** Lesson X.Z — [Title] | [One sentence explaining how this lesson leads into the next]
```

---

## 4. Module Card Format

Every module in the outline must use this format.

```markdown
### Module X — [Title]

**Module objective:** By the end of this module, learners will be able to [single measurable outcome that represents the module's contribution to the course goal].

**Lesson count:** X lessons
**Estimated module duration:** X–X minutes
**Module type breakdown:** X Concept | X Demo | X Lab | X Capstone

**Module prerequisites:** [What the learner must have completed or know before starting this module. Reference prior modules or lessons by number.]

**Why this module:** [1–2 sentences explaining why this module exists in the curriculum — what gap it fills, what learner need it addresses, how it builds on prior modules and enables the next.]

**Consolidated materials for this module:**
- Software: [list]
- Hardware: [list]
- Files: [list]
- Reference: [list]

---
[Lesson cards follow]
```

---

## 5. Course Header Format

The outline document must open with this header before any module content.

```markdown
# Course Outline: [Course Title]

**Generated:** [date]
**Source research document:** [filename of the workflow 01 research doc]
**Target audience:** [from research doc]
**Entry skill level:** [from research doc]
**Course goal:** [from research doc]
**Course format:** [from research doc]

---

## Course Overview

[3–5 sentence description of the course. What is it, who is it for, what does it enable, and what makes it different from what already exists in the market? Base the differentiation on the gaps identified in the research document.]

---

## Prerequisites

[What the learner must know or have before starting Lesson 1.1. Be specific — list skills, not credentials. If there are no prerequisites, say "None — this course is designed for learners with no prior experience in [topic]."]

---

## Consolidated Course Materials

[Single consolidated list of everything the learner needs for the entire course. Organized by category: Software, Hardware, Files, Reference. This is the "what to prepare before you start" section.]

---

## Course Structure at a Glance

| Module | Title | Lessons | Est. Duration | Types |
|--------|-------|---------|---------------|-------|
| 1 | [Title] | X | X–X min | C/D/L/Cap |
| ... | | | | |
| **Total** | | **X** | **X–X hrs** | |

*C = Concept, D = Demo, L = Lab, Cap = Capstone*

---
[Module cards follow]
```

---

## 6. Quality Standards — What Good Looks Like

Apply these standards as a checklist before finalizing any curriculum outline:

### Objectives
- [ ] Every lesson has 3–5 objectives
- [ ] Every objective starts with a Bloom's action verb
- [ ] No objective uses "understand," "know," "learn," or "appreciate"
- [ ] Objectives are at the correct cognitive level for the lesson's position in the course (early = Remember/Understand; mid = Apply/Analyze; capstone = Create)
- [ ] Module objectives are achievable by completing the module's lessons

### Pacing and scope
- [ ] Concept lessons: 8–15 minutes estimated duration
- [ ] Demo lessons: 10–20 minutes estimated duration
- [ ] Lab lessons: 15–30 minutes estimated duration (problem attempt + solution walkthrough)
- [ ] Capstone: 30–60 minutes estimated duration
- [ ] No lesson tries to introduce more than 2–3 new concepts
- [ ] Each module ends before starting a topic that belongs in the next module

### Lesson flow
- [ ] Every lesson has a clearly defined prerequisite chain
- [ ] No lesson requires knowledge introduced in a later lesson
- [ ] The first lesson of the course has zero prerequisites
- [ ] Each lesson's "Connects to" points to the next logical lesson
- [ ] No orphaned lessons (every lesson connects to what came before and what comes after)

### Labs
- [ ] Every lab has a complete materials list
- [ ] Every lab has a problem statement (not just "follow along")
- [ ] Every lab has success criteria — specific and observable
- [ ] Every lab has at least 2 common pitfalls documented
- [ ] Labs are sequenced so each one builds on the previous

### Coverage
- [ ] All consensus topics from the research document appear in the outline
- [ ] All coverage gaps identified in the research document are addressed in at least one lesson
- [ ] All learner voice requests from the research document are reflected somewhere in the outline
- [ ] No out-of-scope content (check against research document exclusions)
- [ ] The capstone project appears as the final lesson and integrates skills from across the course

---

## 7. What to Avoid

- **Vague lesson titles** — "Introduction," "Getting Started," "Overview" tell the learner nothing. Titles should describe the specific skill or concept covered: "Assigning an IP Address to a New S7-1200" is better than "Connecting Your PLC."
- **Objectives that describe instructor activity** — "This lesson demonstrates how to..." is an objective for the instructor, not the learner.
- **Labs without success criteria** — "Try it yourself" is not a lab. A lab is defined by a problem statement and a clear definition of done.
- **Bloated concept lessons** — if a concept lesson needs more than 15 minutes, it is covering more than one concept. Split it.
- **Back-to-back concept lessons** — alternate concept/demo/lab to maintain engagement. No more than two concept lessons in a row.
- **Invented content** — every lesson must trace back to a topic in the research document or a logical prerequisite for a topic in the research document. Do not add lessons that don't connect to the course goal.
