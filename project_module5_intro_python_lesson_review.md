---
name: project-module5-intro-python-lesson-review
description: Iterative lesson-by-lesson QA pass across all ae240 modules; fixing em-dashes, adding in-class assignments, rubrics, and SOLUTION consistency
metadata:
  node_type: memory
  type: project
  originSessionId: b3ee4b44-2301-48a5-b730-a9e4d1616522
---

## Current position: Nearly complete as of 2026-06-25. Working tree clean.

**Final commits this session:**
- 7ef5416: Module 13 lessons QA (title, em-dash, "Utilize", "fuction" fixes)
- 7236896: Screengrab removal from all exam/homework files (Modules 11 + 14)
- b26e483: CLAUDE.md cleanup (removed stale dual-graph policy)
- 1ac7e99: Module 12 data.csv added

**Standing rule confirmed by Becca 2026-06-25:** screengrab submission is ONLY for lesson in-class assignment callouts (session notebooks). Never in homework or exam submission cells — use link+ipynb two-cell pattern there instead.

- Module 12 sessions 1+2 restructured (2026-06-25) -- QA confirmed by Becca visually
- Exam 3 (Module 14) visual QA confirmed by Becca 2026-06-25
- b8bdd36: Module 06 homework AI policy paragraph fixed (stale per-part wording → standard "For any task..." pattern)
- f33b96e: Module 07 practice SOLUTION em-dashes fixed (# SOLUTION — → # SOLUTION:)

**Module 07 items closed 2026-06-25:** Becca signed off on study guide, _old deletion, and leak question — no action needed on any of them.

**Module 12 lesson restructure (2026-06-25):** Session 1 now covers through
5.2 (popt/pcov/covariance); section 5 intro, function intro, 5.1 log
regression, and 5.2 pcov were moved from session 2 into session 1. Session 2
now opens with 5.1 as a recap (duplication), then jumps to 5.3 MSE and
continues through 5.5. All four files changed: session1_v26, session2_v26,
and both SOLUTIONs. Becca reviewed session 1 SOLUTION (PDF on phone) and session 2 SOLUTION
(HTML in Safari) and confirmed both looked good. QA checklist not yet re-run
on these. Note: session 2 cannot be nbconvert --executed standalone because
it references `data_clean` from session 1 -- always render without --execute.

Module 11 (exam 2): blank-line images applied to real exam + practice exam
Part 2, plus a leak/numeric-consistency pass (found and fixed a fabricated
practice-exam example where two different step sizes coincidentally landed
on the same answer, undermining the "answer would be higher" claim).

Modules 12 (nonlinear) + 13 (optimization) + 14 (exam 3) were all done in
one big pass (2026-06-24), applying the same checklist to lessons, homework, and exam.
Real bugs found and fixed:
- Module 12 lesson 2: duplicate "5.2" section numbering (two different
  sections both numbered 5.2), "accurancy" typo, malformed chained-exponent
  LaTeX ($10^2^2$ instead of $100^2$).
- Module 12 homework: objectives claimed "polynomial, power-law, and
  logarithmic models" but the homework actually uses quadratic/cubic/
  exponential models -- objectives never matched the real content.
- Module 13 homework: SOLUTION cited a specific worked example ("3.5412 ft")
  that didn't match what the code actually computes (verified by running
  the exact SOLUTION code: real answer is 3.7774 ft) -- a hand-typed
  plausible-sounding number instead of the real computed one. See
  [[feedback-verify-cited-numbers]].
- Module 14 exam: practice exam's Part 2 had zero answer-space cells (same
  gap as Module 11's practice exam, fixed the same way); the real exam's
  Part 2 already had blank-line images via a different valid pattern
  (separate image cell after a "**ANSWER HERE**" label, not merged into one
  cell like Module 07/11's pattern) -- left that one alone, it already
  works, no need to force it into the Module 11 pattern. Also found the
  same "fabricated example number" bug as Module 13: solution cited
  "Optimal Investment of 15.0k yielding ... 57.5" which is literally the
  raw data point at Investment=15, not the actual fitted-curve optimum
  (real answer: 14.67k / 56.06, confirmed by running curve_fit + minimize
  directly).
- Old-vs-new PDF comparison gap: Module 13 optimization has no pre-existing
  lesson at all (genuinely new content, nothing to compare against), and
  both Module 12's and Module 13's "old" homework files in `_old/` are just
  empty Canvas-link stub HTML with no real content. Skipped the old-vs-new
  comparison for those three, rendered new-only instead.
- One self-correction worth remembering: a fix script that ran
  `json.dump(nb, f, indent=1)` on `exam_3_practice_v26.ipynb` produced a
  460-line diff for a 3-cell insertion, because that file's original format
  was compact single-line JSON (no indent), not the indent=1 pretty-print
  most other notebooks in this repo use. Always check the original file's
  JSON formatting style first (`head -c 200 file.ipynb`) and match it
  (`separators=(",", ":")` for compact files) before writing back, or the
  diff balloons into a full-file rewrite even though content is unchanged.

Module 10 (conditionals) lessons 1 & 2 and homework all COMPLETE, committed
2026-06-24 (commits 620f603, 59fdcad, 05857ef, 2e85e8b, 1ee0df4). Module 09
(data cleaning) finished earlier (commits 1a596b6, e5767a2).

**Module 10 homework (`3_conditionals_homework_v26` + SOLUTION): COMPLETE.**
This one was noticeably older/unpolished compared to the v26 lessons (still
had the old per-assignment "AI Statement" instead of the consolidated AI
Reflection, no point total in title, broken markdown headers missing a
space after `#`). Found and fixed, with Becca's confirmation on the
judgment calls:
- Real bug: SOLUTION's print statements said "Location with the
  HIGHEST/Lowest AVERAGE RATING" when the variable is grouped by
  building_type, not location. Fixed directly (unambiguous bug).
- Real bug: a leftover pasted URL fragment was bleeding into the Part 1
  markdown instructions (duplicate of the real URL already used correctly
  in the code cell). Removed directly.
- "THey" typo and "utilize" -> "use" fixed directly.
- Becca confirmed all three judgment calls: add point total to title (17
  pts), convert AI Statement to the standard 2-pt end-of-homework AI
  Reflection section, and remove a stray (1pt) that was attached to a hint
  sentence about using `idxmax` rather than a real task (Part 2: 9 -> 8 pts).
- Also added explicit "(N pts total)" to each Part header so the existing
  point-totals test can actually validate this file (previously skipped
  entirely since no header matched the regex). All 36 relevant tests pass,
  including point-totals and SOLUTION execution.

**Module 10 lesson 1 (`1_conditionals_session1_v26` + SOLUTION): COMPLETE.**
Found and fixed 22 em-dashes (colon for labels/headings, semicolon for
joined independent clauses, comma for short appositives).

**Module 10 lesson 2 (`2_conditionals_session2_v26` + SOLUTION): COMPLETE.**
Removed `.groupby()` from the objectives list (no cell actually used it,
only `.unique()`/`.value_counts()`). Fixed 13 em-dashes, same convention as
lesson 1. Becca reviewed both lessons via merged PDF since she was on her
phone for this session; lesson 1 was re-rendered and re-sent after the fix
so she could confirm.

Becca confirmed no content should move between lesson 1 and 2 despite
lesson 1 being ~35% longer by char/line count: lesson 1's four topics
(Boolean -> if -> if/else -> if/elif/else) build sequentially and feed the
radon-dataset example that lesson 2's break/continue section reuses, so
splitting that chain would break the dependency.

All changes through Module 08 committed and pushed as of 2026-06-24.
Workflow (established): fix module lessons first, then check that module's
homework, always render both student+SOLUTION for visual QA before calling a
module done. **Visual QA format depends on device** — see
[[feedback-visual-qa-format]]: HTML+Safari by default when Becca's at her
computer, merged PDF only when she says she's on her phone.

**Module 08 lessons (`1_dataframes_v26`, `2_dataVis_notes_v26`, both +
SOLUTION): COMPLETE.** Added the standard in-class assignment callout to both
(each ends in its own "In Class Assignment" exercise, not a "Your Turn", so
callout text says "The exercise above..." instead of "Your Turn #N above...").
Fixed a typo ("undestand" -> "understand"). Full QA pass done: titles match
SOLUTION-free, no em-dashes, no instructor-note leaks, full cell-by-cell diff
found no leaks, both SOLUTIONs execute cleanly with `--allow-errors` (each has
one intentional-bug demo cell). Becca verified the lessons herself by
comparing against the old (`_old/`) versions in Safari before we moved on.

**Module 08 homework (`3_dataframe_homework_v26` + SOLUTION): COMPLETE.**
Initially paused by Becca's request so lessons could finish first; resumed
and fixed across two rounds once she confirmed "all three" of the queued
findings:
1. The "FIRST TASK" xlsx->csv conversion cell was a leak (complete working
   `pd.read_excel()`/`to_csv()` code, nothing blanked) that also contradicted
   its own instructions and the lesson. Becca's preferred fix (round 2,
   overriding my round-1 fix): students convert manually in Excel (File ->
   Save As -> CSV, per **this week's** lesson, not "Lesson 1" generically),
   upload the CSV, then just `pd.read_csv()` it — no pandas-based conversion
   task at all. Code cell is now identical and ungraded in student+SOLUTION.
2. SOLUTION's written analysis was wrong: claimed Nuclear has the widest
   spread (largest IQR); actually Natural Gas does (7537 vs Nuclear's 4683,
   the smallest). Fixed, confirmed by computing IQR directly from the data.
3. Standardized header/submission boilerplate to match Module 05/06 (title
   with point total "(24 pts)", AI policy, link+download submission).
4. Round 2 (her direct feedback after reviewing): removed the now-redundant
   "Tip: adding a text cell" cell (students know this by now), removed
   "crucial" (flagged as an LLM-sounding word, see
   [[feedback-no-emdashes]]), added a SOLUTION-only grading-note comment that
   `range` doesn't have to be merged into the summary table, and fixed a real
   double-plot bug (see Lessons Learned below).

A bulk-rewrite script attempting multiple fixes at once got blocked by the
auto mode classifier as too large a unilateral content change on round 1;
correctly so since nothing had been confirmed yet. Lesson: ask before
restructuring homework/exam content beyond mechanical QA fixes, even when the
findings themselves are solid.

---

## Module 05: COMPLETE

Session 1 (72 cells), Session 2 (33 cells), Homework (25+ cells) all done.
Homework title now shows total points: "Intro to Python: Homework (62 pts)"
(verified by summing all 7 problem headers: 15+5+8+8+9+12+5).

---

## Module 06: COMPLETE (committed 2026-06-23)

**Sessions 1 & 2:** em-dashes fixed, in-class assignment callouts added,
Your Turn cost hint improved, analysis answer moved to SOLUTION-only.

**Homework (`3_linReg_dataVis_homework_v26`):**
- Header/boilerplate rebuilt to match Module 05's pattern: title + AI policy
  at top, link+download submission (reusing Module 05's actual screenshots),
  "## Parts" overview kept
- Rubric rewritten to 1pt-per-line on every Part, each ending in "Note any
  AI tool use for this part (1 pt)"
- Found and fixed a real bug: SOLUTION's Part 4 written analysis had wrong
  regression numbers (155.7/271.53) that didn't match what the code actually
  computes (144.69/589.33); confirmed by executing the SOLUTION
- Found and fixed a second bug from my own earlier edit: bundling all of
  Part 4's questions into one intro cell duplicated Q2-Q4, which already had
  their own pre-existing cells right after each response placeholder
- Title now shows total points: "...Homework (25 pts)"

---

## Module 07 Exam 1: PARTIALLY DONE

**Done (2026-06-23/24):**
- Compared old (`_old/`) vs current files: real exam content unchanged
  (just split into Part1/Part2 + submission line), but the practice exam
  gained an entirely new "Part 2: In-Class Conceptual Analysis (14 pts)"
  section that didn't exist before
- **Found and fixed a real leak**: Part 1's Application section (cells with
  the for-loop/regression code, computed r-values, and written analysis) was
  byte-identical between student and SOLUTION in both the real exam and the
  practice exam, i.e. full answers were sitting in the student-facing file.
  Blanked in both; SOLUTION untouched. This was NOT caught by the standard
  "grep for the word SOLUTION" check; see updated
  [[feedback-notebook-qa-checklist]].
- Submission instructions: Part 1 (take-home) now uses the same link+download
  mechanism as the homeworks; Part 2 (in-class) now says it's handwritten and
  collected in person, not submitted digitally
- Part 1 now has a title at the top with point breakdown: "Exam 1 / Part 1:
  39 pts | Part 2: 10 pts | Total: 49 pts" (the 39 was confirmed with Becca:
  the rubric's "(2 pts for setting up the regression)" and "Calculate the
  linear regression... (2pts)" bullets are two distinct criteria, not a
  duplicate)
- Added distinguishing titles: practice exam says "EXAM 1 PRACTICE", all
  SOLUTION copies say "(SOLUTION)"; this deliberately breaks the usual
  "student/SOLUTION title must be identical" rule, by request, for
  at-a-glance differentiation

**Not yet done:**
- Full em-dash scan of Exam 1 files (not checked this pass)
- `study_guide_extra_help.ipynb` not reviewed at all
- `_old/exam_1_solution.ipynb` is a fully superseded duplicate; candidate for
  deletion, not yet actioned
- Becca was warned the real exam Part 1 leak may already have gone out to
  students; she hasn't said whether that happened or needs separate handling
- Offered to apply the same submission-instruction fix (Part1=homework-style,
  Part2=handwritten/collected) to Exam 2 and Exam 3; not yet actioned, no
  answer yet
- Exam 2/3 and their practice versions haven't been checked for the same
  leaked-solution bug; given it was found in two different Exam 1 files, it's
  worth checking Modules 11/14 (exam 2/3) for the same pattern

---

## Known small issue, not yet fixed

**Module 06 homework's Generative AI Policy paragraph has stale wording.**
It still says "Each part below has 1 pt reserved for your AI usage note...
If you did not use AI on a part, write..." -- leftover from before the
e5767a2 consolidation to a single end-of-homework AI Reflection section.
The structural change (the actual `## AI Reflection (2 pts)` section) IS
present at the end, just the policy paragraph text at the top wasn't
updated to match M05/M08/M09's wording ("For any task where you used AI...
If you did not use AI on a task, write..."). Low priority, cosmetic only.

## Lessons learned this session (apply to all future modules)

**Critical: leaked solutions aren't always literal "SOLUTION" text.** The
Exam 1 leak (see above) had zero occurrences of the word "SOLUTION" in the
leaked cells; they were just complete, working code and fully-written
analysis with no blanking at all. Grepping for the word doesn't catch this.
The reliable check: diff every student code/markdown cell against the
SOLUTION's same-position cell. If a cell that's supposed to require student
work (not given data, not instructions) is byte-identical to SOLUTION, that's
a leak. Do this check on **exams especially**, not just homework.

**Exam submission convention (established 2026-06-23):** take-home parts
use the homework's link+download mechanism; in-class/handwritten parts just
need a name + "collected at the end of class" note, no digital submission
instructions at all.

**Written analysis cells:** in lesson notebooks with "write your analysis
here" prompts: SOLUTION gets the full answer, student gets placeholder
`*Write your analysis here.*`. Check every "Your Turn" with a written
response for this pattern.

**Cost/value hints in Your Turn exercises:** when students are asked to
"make values realistic," always provide a concrete range and examples.
Write ranges as "$X to $Y" not "$X-$Y" (hyphens cause issues); no em-dashes.

**Em-dashes in code comments:** catch-all `' — '` to `'; '` usually works;
check code cells too (not just markdown).

**When running nbconvert from a subdirectory with git commands:** always run
`git add/commit` from the repo root, not the subdirectory.

**bypassPermissions:** set in `.claude/settings.local.json` for this project
(gitignored, project-scoped only).

**Rubric style (established 2026-06-23):** 1 pt per individual task line,
with "Note any AI tool use for this part/problem (1 pt)" as the last line.
Applies even to non-broken-code problems (e.g. written-analysis questions
get the same AI-note line). When a problem doesn't divide evenly, prefer
shifting weights to clean integers (e.g. 1.5/1.5 to 1/1) over leaving
fractions, when there's no strong reason to preserve the original weighting.

**Matplotlib double-plot bug (found 2026-06-24, Module 08 homework):** a code
cell that does `fig_x, ax_x = plt.subplots()` ... then ends with a bare
`fig_x` as the last line renders the figure **twice** under the Jupyter
inline backend: once via the auto post-execute `flush_figures()` hook (every
created figure auto-displays regardless of whether it's referenced), and
again via the `execute_result` repr of that bare trailing expression. Fix:
delete the trailing bare `fig_x` line entirely; the figure still displays
once via the auto-flush. Worth grepping other modules' SOLUTION cells for
this exact pattern (`fig_\w+` as the literal last line of a plotting cell).

## QA checklist reminder (full list in [[feedback-notebook-qa-checklist]])

For every lesson/exam pair: em-dashes, full cell-by-cell leak diff (not just
grep), student title no "(SOLUTION)" unless deliberately requested otherwise,
in-class callout after last Your Turn, written analysis placeholder vs
answer, execute SOLUTION, total points in title.
