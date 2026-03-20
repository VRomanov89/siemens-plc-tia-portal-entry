# Workflow 02 — Refined Outline Generation

## Objective

Transform a research document produced by Workflow 01 into a complete, highly detailed course curriculum outline. Every module, lesson, lab, and capstone is fully specified: what is taught, what the student learns, measurable learning objectives, key concepts introduced, common pitfalls, materials needed, lab guides with step-by-step instructions, and success criteria. The output is production-ready — specific enough that the instructor can pick up any lesson card and know exactly what to film.

---

## Required Skill

**Read `skills/curriculum_writing.md` before starting any output.** This skill defines the exact format for lesson cards, module cards, and the course header, as well as all quality standards for learning objectives, lesson types, and lab specifications. Do not produce any curriculum content without having read and internalized those standards.

---

## Required Inputs (Parameters)

Before beginning, collect the following from the user. Mark any already known from project context and ask only for what's missing.

| # | Parameter | Required | Description |
|---|-----------|----------|-------------|
| 1 | `research_document_path` | Yes | Path to the Workflow 01 research document (e.g., `curriculum/01_research_[slug].md`) |
| 2 | `target_lesson_duration` | Yes | Target video length range per lesson (e.g., "10–15 minutes", "5–20 minutes"). This constrains how much content fits in one lesson. |
| 3 | `lesson_count_target` | No | Approximate total number of lessons desired. If provided, use it to calibrate how much to split or consolidate. If not provided, let content dictate. |
| 4 | `module_adjustments` | No | Any modules from the proposed structure the user wants to add, remove, merge, or reorder before the outline begins |
| 5 | `pacing_notes` | No | Any pacing preferences (e.g., "keep early modules short to reduce friction," "labs every 2–3 lessons") |
| 6 | `lesson_type_preference` | No | Any preference for ratio of lesson types (e.g., "heavy on demos," "a lab after every major concept block") |

Once all required parameters are confirmed, echo them back to the user for a final check before starting.

---

## Steps

### Step 1 — Collect Parameters and Read Research Document

1. Ask for any missing required parameters. Echo confirmed parameters back before proceeding.

2. Read the research document at `research_document_path` in full. Do not skim. Extract and hold the following in working context:
   - The proposed curriculum structure (modules, lessons, and objectives from Section 5 of the research doc)
   - The full list of consensus topics (Section 2.1)
   - The full list of coverage gaps (Section 2.3)
   - The depth imbalance findings (Section 2.4)
   - The learner voice findings: top frustrations, recurring requests, common knowledge gaps, and wishes (Section 3)
   - The exclusions stated in the course parameters
   - Any follow-up research notes that affect curriculum design

3. Read `skills/curriculum_writing.md` in full. This governs all output produced in subsequent steps.

---

### Step 2 — Validate and Confirm the Module Structure

Before writing any lesson detail, present the module structure for user confirmation:

- List every module from the research document's proposed curriculum
- For each module, list the lessons proposed
- Flag any modules or lessons that appear to conflict with stated exclusions
- Flag any consensus topics from Section 2.1 that are not yet covered by any module
- Flag any coverage gaps from Section 2.3 that are not yet addressed
- Apply any `module_adjustments` from the confirmed parameters

Present this consolidated module map to the user. Ask for explicit confirmation or corrections before proceeding to Step 3.

**Do not proceed until the user confirms the module structure.**

---

### Step 3 — Plan Lesson Type Distribution

Before writing lesson cards, plan the type distribution for each module using the following rules:

**Type assignment rules:**
- Assign **Concept** to lessons that introduce new terminology, frameworks, or non-procedural knowledge
- Assign **Demo** to lessons where the instructor shows a workflow step-by-step in software or on hardware
- Assign **Lab** to lessons where the learner must solve a problem independently — one lab per major skill block, minimum
- Assign **Capstone** to the final integrative project lesson only

**Pacing rules:**
- No more than two consecutive Concept lessons without a Demo or Lab between them
- Every module should contain at least one Demo or Lab (no purely conceptual modules)
- Labs should appear with increasing frequency as the course progresses — early modules may have one lab; later modules may have one after every major skill block

**Duration constraints:**
- Respect the `target_lesson_duration` parameter
- If a planned lesson would exceed the upper bound of the target duration range, split it into two lessons
- If a planned lesson would fall significantly short of the lower bound, consider merging it with an adjacent lesson of the same type

Present the planned type distribution as a table (Module | Lesson | Title | Type | Est. Duration) and ask for user confirmation or adjustments before writing lesson cards.

**Do not proceed until the user confirms the lesson type plan.**

---

### Step 4 — Write Lesson Cards (Module by Module)

Write full lesson cards for every lesson in the confirmed structure, one module at a time. Use the lesson card format defined in `skills/curriculum_writing.md` exactly — do not omit any fields.

For each lesson, derive content from the following sources in priority order:

1. **The research document** — what specific topics, tools, and concepts were identified as important? What gaps need to be filled in this lesson? What learner frustrations does this lesson address?
2. **The skill file standards** — apply the correct cognitive level for the lesson's position in the course; use Bloom's action verbs; write objectives the learner can demonstrate
3. **Subject matter expertise** — fill in the technical specifics (key concepts, pitfalls, step-by-step lab instructions) that the research document implies but doesn't spell out in detail

**For every lesson, explicitly:**

- Write "What is taught" from the instructor's perspective (what does the instructor cover?)
- Write "What the student learns" from the learner's perspective (what capability does the learner gain?)
- Write 3–5 measurable learning objectives using Bloom's action verbs at the correct cognitive level
- List 2–4 key concepts introduced with one-sentence definitions
- List 2–3 common pitfalls specific to this lesson (not generic; based on research doc learner voice findings where applicable)
- Fully specify materials — if hardware is needed, name the exact model; if a TIA Portal project file is a prerequisite, note it; if a reference document is relevant, cite it
- For Lab and Capstone lessons: write the full step-by-step lab guide and define observable success criteria — not "the program works" but specifically what the learner must demonstrate

**Grounding requirements:**
- If a lesson addresses a coverage gap from Section 2.3 of the research doc, note it explicitly in "What is taught"
- If a lesson addresses a learner frustration or wish from Section 3 of the research doc, note it in "What the student learns"
- Do not introduce topics that are in the exclusions list — if you find a lesson drifting toward excluded content, constrain it back

After completing each module's lesson cards, write the module card header (format in `skills/curriculum_writing.md`) consolidating the module's objective, lesson count, duration estimate, type breakdown, prerequisites, rationale, and consolidated materials list.

Pause after each module and ask the user: "Module [X] complete. Review and confirm before I continue to Module [X+1]."

**Do not proceed to the next module until the user confirms.**

---

### Step 5 — Write the Course Header

After all modules are confirmed, write the course header using the format in `skills/curriculum_writing.md`:

- Course overview (3–5 sentences: what is it, who is it for, what does it enable, what differentiates it — pull the differentiation directly from the research doc's gaps and market signal findings)
- Prerequisites section
- Consolidated course materials list (every piece of software, hardware, and reference material across all modules, deduplicated)
- Course structure at a glance table (all modules, lesson counts, durations, type breakdowns)

---

### Step 6 — Quality Check

Before finalizing the document, run through the complete quality checklist from `skills/curriculum_writing.md` (Section 6). For each item that fails, fix it before proceeding.

Additionally verify:

- [ ] Every consensus topic from the research doc Section 2.1 appears in at least one lesson
- [ ] Every coverage gap from the research doc Section 2.3 is addressed in at least one lesson — note which lesson covers it
- [ ] Every top learner request from the research doc Section 3.2 is addressed in at least one lesson — note which lesson covers it
- [ ] Every top learner frustration from the research doc Section 3.1 is addressed somewhere in the outline — either as a dedicated lesson or as a "common pitfall" entry
- [ ] No lesson covers content from the exclusions list
- [ ] The capstone project is fully specified: problem statement, deliverables, evaluation criteria
- [ ] The course structure table reflects accurate lesson counts and duration totals

If any of the above fail, fix the outline before saving.

---

### Step 7 — Compile and Save

Assemble the full document in this order:
1. Course header (Step 5 output)
2. Module 1 card + all Module 1 lesson cards
3. Module 2 card + all Module 2 lesson cards
4. ... (all remaining modules)
5. Coverage traceability table (Step 6 — which lessons cover which gaps and requests)

Save to:

```
curriculum/02_outline_[course_topic_slug].md
```

Where `course_topic_slug` matches the slug used in the Workflow 01 research document filename.

Report to the user: file path, total lesson count, total estimated course duration, and a brief summary of any adjustments made during quality check.

---

## Output Format

The final document structure, in order:

```
# Course Outline: [Course Title]
[Course header — metadata, overview, prerequisites, consolidated materials, structure at a glance]

---

### Module 1 — [Title]
[Module 1 card]

#### Lesson 1.1 — [Title]
[Lesson card]

#### Lesson 1.2 — [Title]
[Lesson card]

... (all Module 1 lessons)

---

### Module 2 — [Title]
...

---

## Coverage Traceability

### Research Gaps Addressed
| Gap (from research doc §2.3) | Addressed in |
|------------------------------|-------------|
| [Gap description] | Lesson X.Y |
| ... | |

### Learner Requests Addressed
| Request (from research doc §3.2) | Addressed in |
|----------------------------------|-------------|
| [Request description] | Lesson X.Y |
| ... | |

### Learner Frustrations Addressed
| Frustration (from research doc §3.1) | Addressed in |
|--------------------------------------|-------------|
| [Frustration description] | Lesson X.Y or Common Pitfall in Lesson X.Y |
| ... | |
```

---

## Quality Checks (Final Gate)

Before saving, verify every item:

- [ ] `skills/curriculum_writing.md` was read before producing any output
- [ ] Module structure was confirmed by user before writing lesson cards
- [ ] Lesson type distribution was confirmed by user before writing lesson cards
- [ ] Each module was confirmed by user before moving to the next
- [ ] Every lesson uses the exact lesson card format from the skill file
- [ ] Every lesson has 3–5 objectives starting with Bloom's action verbs
- [ ] No objective uses "understand," "know," "learn," or "appreciate"
- [ ] Every lab and capstone has a complete lab guide and observable success criteria
- [ ] Every lab and capstone has a fully specified materials list
- [ ] No back-to-back concept lessons (max 2 in a row before a demo or lab)
- [ ] All consensus topics from research doc §2.1 are covered
- [ ] All coverage gaps from research doc §2.3 are addressed
- [ ] All top learner requests from research doc §3.2 are reflected
- [ ] All top learner frustrations from research doc §3.1 are addressed (as lessons or pitfalls)
- [ ] No excluded content appears anywhere in the outline
- [ ] Coverage traceability table is complete and accurate
- [ ] Document saved to the correct path in `curriculum/`

---

## Edge Cases

**Research document has a weak or missing proposed curriculum structure:** Build the module and lesson structure from scratch using Section 2 (curriculum patterns) and Section 3 (learner voice) of the research document as primary inputs. Do not guess — derive every lesson from an explicit finding in the research document.

**A coverage gap requires a lesson that conflicts with the exclusions list:** Do not add the lesson. Note the conflict in the coverage traceability table and flag it to the user for a decision.

**Target lesson duration is too short for a concept or lab:** Flag this to the user before writing. Either the duration target needs to be relaxed for certain lesson types, or the lesson needs to be restructured. Do not silently produce a lesson that violates the duration constraint.

**User requests changes mid-module:** Stop, apply the change, and re-present the affected lesson(s) for re-confirmation. Do not continue to the next lesson until the current one is confirmed.

**Subject matter requires a level of technical detail that is outside your knowledge:** Note the gap explicitly in the lesson card under "What is taught" — flag it with [NEEDS EXPERT REVIEW]. Do not invent technical detail you are not confident about. The instructor will fill in or correct these flagged items.
