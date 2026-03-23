# Section 5 — Structured Programming with Function Blocks: Conclusion

**Estimated segment duration:** 3–5 minutes
**Type:** Section recap (structural — not counted in lesson totals)

---

## What You Covered in This Section

Three lessons. The shift from "a program that works" to "a program that scales." If the lab ran correctly — two independent motors from one FB definition — you now understand one of the most important structural concepts in professional PLC programming.

**From Lesson 5.1:**
- OBs are OS entry points, not regular blocks — OB1 is called every scan; fault OBs are called when specific error conditions occur
- FBs have Static variables that persist between scans via an instance DB — use FBs for anything that needs to remember state
- FCs have no static memory — use FCs for pure input-to-output calculations where nothing needs to be remembered
- Global DBs store shared data — recipe values, setpoints, production totals — accessible by any block in the project
- The decision rule: "Does this block need to remember something between scans?" → FB. "Does it just calculate?" → FC. "Does it store shared data?" → Global DB

**From Lesson 5.2:**
- FB interface sections: Input (in), Output (out), Static (persists, stored in instance DB), Temp (discarded after scan)
- Logic inside an FB uses `#` local variable references — no global tags inside the FB means the FB works for any application it's dropped into
- Optimized DB: symbolic access only, Siemens manages memory layout — the default and correct choice for new projects
- Non-optimized DB: fixed byte offsets — required only when external systems must address specific memory locations
- Downloading a DB to a running PLC resets all non-retentive values — this is a documented behavior, not a bug, and it can disrupt running sequences in production

**From Lesson 5.3 (Lab):**
- Two FB instances, two instance DBs, two sets of I/O tags — same logic, fully independent state
- Shared instance DBs cause instance state collision — the most common FB mistake and one that is immediately obvious when tested
- Global tag references inside an FB destroy reusability — the FB becomes hardwired to specific hardware the moment a global tag appears inside it

---

## Before You Continue

Make sure you have:
- [ ] A `Motor_Control` FB with correct interface — no global tags in the FB logic
- [ ] Two independent FB instances in OB1, each with its own instance DB
- [ ] Both motors tested for independence in PLCSIM
- [ ] Project compiling cleanly with no errors or warnings

---

## What's Next

Section 6 is the final section — and the one that sets this course apart from every simulation-only alternative. You'll cover TIA Portal's testing tools in depth, then walk through connecting to and downloading to a physical S7-1200. The section closes with the capstone project: a complete conveyor control system built from a problem statement using everything learned across all five sections.

*See you in Section 6.*
