# Workflow 01 — Deep Curriculum Research

## Objective

Produce a comprehensive research document for a proposed course. The document maps what already exists across every source type, extracts actual curricula where possible, surfaces what learners are asking for and what the market is missing, and proposes a high-level curriculum structure grounded in evidence. This document becomes the foundation for all subsequent curriculum development.

---

## Required Inputs (Parameters)

Before beginning, collect the following from the user. If any are missing, ask for them explicitly. Do not proceed until all required parameters are confirmed.

| # | Parameter | Required | Description |
|---|-----------|----------|-------------|
| 1 | `course_topic` | Yes | The subject matter of the course (e.g., "Getting Started with X Technology") |
| 2 | `target_audience` | Yes | Who the course is for — role, industry, and any relevant background knowledge they bring |
| 3 | `skill_entry_level` | Yes | What learners already know before taking this course |
| 4 | `course_goal` | Yes | What a learner should be able to do after completing the course (one clear outcome statement) |
| 5 | `course_format` | Yes | How the course will be delivered (e.g., video-based, self-paced, instructor-led, hybrid) |
| 6 | `depth_and_scope` | Yes | How broad and deep should coverage go (e.g., "fundamentals only", "zero to job-ready", "full professional proficiency") |
| 7 | `focus_areas` | No | Specific topics the user wants to emphasize or ensure are covered |
| 8 | `exclusions` | No | Topics explicitly out of scope for this course |

Once all required parameters are confirmed, echo them back to the user for a final check before starting research.

---

## Steps

### Step 1 — Collect Parameters

Ask the user for any missing required parameters. Present the full list, note which are already known from project context, and ask only for what's missing.

Echo confirmed parameters back before proceeding to Step 2.

---

### Step 2 — Broad Source Discovery

Conduct web searches across all of the following source categories for the `course_topic`. Do not limit research to any single platform type — breadth matters here.

**Source categories to cover:**

1. **Official / manufacturer sources** — Does the technology vendor offer training, certification, documentation portals, or learning paths? What do they cover and at what cost?
2. **Online course platforms** — Search Udemy, Coursera, LinkedIn Learning, Skillshare, edX, Teachable, and similar. Look for courses sorted by enrollment, rating, and recency.
3. **University and college programs** — Search for courses, degree programs, and continuing education offerings at universities and community colleges. Look for publicly available syllabi.
4. **YouTube** — Search for channels and playlists covering the topic. Identify the most-viewed and highest-rated content. Note which creators have substantial audiences.
5. **Web tutorials and blogs** — Search Google broadly for tutorials, guides, and written resources. Include niche sites, industry blogs, and documentation.
6. **Community forums** — Search Reddit, Stack Overflow, industry-specific forums, and Facebook Groups for discussions about the topic. These are primary signals for what learners are struggling with and asking for.

For each source category, perform at minimum 2 targeted searches. Log what search queries were used in the Research Notes section of the output.

---

### Step 3 — Competitive Resource Inventory

For every course, learning resource, or structured program found in Step 2, document the following. Aim for a minimum of 15 entries spanning at least 4 different source categories.

| Field | Description |
|-------|-------------|
| Title | Name of the course or resource |
| Provider | Who created or hosts it |
| URL | Direct link |
| Source type | Manufacturer / Online platform / University / YouTube / Tutorial / Other |
| Format | Video, text, interactive, blended, etc. |
| Skill level targeted | Beginner, intermediate, advanced, or mixed |
| Estimated length | Hours, modules, weeks, etc. |
| Cost | Free, one-time price, subscription — include actual price where visible |
| Curriculum available? | Yes / Partial / No — can we see a syllabus or module list? |
| Curriculum summary | If visible, list the major topics or modules covered |
| Notable strengths | What this resource does well based on content, reviews, or description |
| Notable weaknesses | What it lacks, what reviewers complain about, or what's conspicuously absent |

Where curriculum details are not publicly visible (paywalled), use whatever is accessible: course outline pages, preview videos, sample syllabi, promotional descriptions, or learner reviews describing content.

---

### Step 4 — Curriculum Cross-Analysis

Analyze the curricula and module structures collected in Step 3. Identify patterns across courses using these lenses:

**Consensus topics** — What topics appear in nearly every course? These are the non-negotiables. List them.

**Sequencing norms** — What order do courses typically follow? Is there a standard progression? Note any courses that deviate and whether that deviation seems to help or hurt based on learner feedback.

**Coverage gaps** — What topics are rarely or never covered, yet logically belong in the subject area? What do learners ask about in forums that courses don't address?

**Depth imbalances** — What topics are over-taught relative to their real-world importance? What topics are under-taught? Support this with evidence from reviews or forum posts where possible.

**Lab and exercise quality** — How do existing courses handle practical application? Are labs realistic? Are they hands-on or purely theoretical? What do learners say about them?

Summarize findings as patterns with supporting evidence — not just lists of topics.

---

### Step 5 — Market Signal Research (Gaps and Learner Voice)

This step is specifically about what learners and practitioners are saying, asking, and complaining about. It is separate from competitive analysis and must draw on primary community sources.

Search the following for signals:

- Reddit threads (e.g., r/PLC, r/learnprogramming, r/[relevant subreddit]) — What questions do beginners ask repeatedly? What do experienced practitioners say is missing from beginner training?
- YouTube comments on top-performing videos in this topic area — What are viewers asking for in the comments? What follow-up content are they requesting?
- Course reviews on Udemy, Coursera, or similar — What do 1-star and 2-star reviewers specifically say is missing or wrong? What do 5-star reviewers say made the course valuable?
- Forum threads on Stack Overflow, industry-specific communities, or manufacturer support forums — What recurring problems do learners hit?

Document specific quotes or paraphrased sentiments where possible — not just summaries.

Organize findings into:
- **Top recurring learner frustrations** (what existing courses fail to deliver)
- **Top recurring learner requests** (what people explicitly ask for)
- **Common knowledge gaps** (what learners consistently don't know coming out of existing courses)
- **What learners say they wish existed**

---

### Step 6 — Cost and Access Comparison

Summarize the cost landscape for existing resources:
- What is the price range for paid courses on this topic?
- What is available for free, and how does free content compare in quality to paid?
- Are there manufacturer certifications tied to paid training? What do they cost and what do they require?
- What is the typical time investment to complete comparable training?

Present this as a brief comparison table and a 1–2 paragraph summary of what the cost landscape means for a new course entering this space.

---

### Step 7 — Proposed Curriculum Structure

Using the research from Steps 3–6, draft a proposed high-level curriculum structure for the course. This is a hypothesis to validate — not a final curriculum.

Format as:
- **Modules** (major topic groups, typically 3–8)
  - **Lessons** within each module (specific units — one lesson = one video or activity)
  - **Estimated lesson count** per module
  - **Learning objective** per module ("By the end of this module, learners will be able to…")
  - **Suggested lab or exercise** per module

Apply these design criteria:
- Each module must build on the previous — no orphaned topics
- The first module must deliver a quick win — reduce early dropout
- Lab scenarios should be relevant to the `target_audience`'s real work context
- The overall scope must match `depth_and_scope` — do not pad or under-deliver
- Sequence and topic selection must be grounded in the research — explain any deviations from the norm found in Step 4

---

### Step 8 — Compile and Save Research Document

Assemble all outputs from Steps 3–7 into a single markdown document using the output format below. Save it to:

```
curriculum/01_research_[course_topic_slug].md
```

Where `course_topic_slug` is a lowercase, hyphenated shorthand for the course topic.

---

## Output Format

The final document must follow this structure exactly:

```markdown
# Curriculum Research: [Course Topic]

**Generated:** [date]
**Target audience:** [target_audience]
**Entry skill level:** [skill_entry_level]
**Course goal:** [course_goal]
**Course format:** [course_format]
**Depth and scope:** [depth_and_scope]

---

## 1. Competitive Resource Inventory

[Full table — minimum 15 entries across at least 4 source types]

---

## 2. Curriculum Cross-Analysis

### 2.1 Consensus Topics
[Topics that appear across nearly all courses]

### 2.2 Sequencing Norms
[Common progression patterns and notable deviations]

### 2.3 Coverage Gaps
[Topics rarely covered that logically belong — supported by evidence]

### 2.4 Depth Imbalances
[Over-taught and under-taught topics relative to real-world importance]

### 2.5 Lab and Exercise Quality
[How existing courses handle practical application]

---

## 3. Market Signals — Learner Voice

### 3.1 Top Recurring Frustrations
[What learners say existing courses fail to deliver]

### 3.2 Top Recurring Requests
[What learners explicitly ask for]

### 3.3 Common Knowledge Gaps
[What learners consistently don't know after completing existing courses]

### 3.4 What Learners Say They Wish Existed
[Direct quotes or paraphrased sentiments from forums, comments, reviews]

---

## 4. Cost and Access Comparison

[Table and summary of pricing landscape]

---

## 5. Proposed Curriculum Structure

[Module-by-module breakdown with lessons, objectives, labs, and rationale]

---

## 6. Research Notes

[Search queries used, source limitations, paywalled content that couldn't be fully reviewed, any follow-up questions for the user]
```

---

## Quality Checks

Before delivering the document to the user, verify:

- [ ] All required parameters confirmed before research began
- [ ] Minimum 15 resources documented with URLs across at least 4 source types
- [ ] Actual curriculum/syllabus content captured where available — not just course titles
- [ ] Market signals section includes specific learner quotes or paraphrased sentiments, not just general summaries
- [ ] Coverage gaps are supported by evidence (forum posts, reviews, absence in research) — not invented
- [ ] Cost comparison covers the full range from free to paid/certified
- [ ] Proposed curriculum structure references the research — design decisions are traceable
- [ ] At least one lab or exercise proposed per module
- [ ] All URLs spot-checked (minimum 5 verified as reachable)
- [ ] Document saved to the correct path in `curriculum/`

---

## Edge Cases

**Topic yields few existing courses:** Broaden searches to adjacent or parent topics and note this in Research Notes. Fewer existing courses is itself a market signal — document it as such.

**Paywalled content:** Include it in the inventory. Use every publicly available signal — course outline pages, preview content, syllabi, learner reviews — to characterize it. Note what could not be verified.

**Conflicting curriculum structures across sources:** Document both approaches in Section 2.2 and make an explicit recommendation in Section 5 with reasoning. Do not average them together or hedge.

**User changes parameters mid-research:** Stop. Confirm the updated parameters. Identify which already-gathered research remains valid and which must be re-run. Continue from the earliest affected step.

**Learner voice sources yield little signal:** If forums and reviews are sparse, expand to adjacent communities (e.g., if the tool-specific community is small, search the broader industry community). Note the limitation in Research Notes.
