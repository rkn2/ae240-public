---
name: feedback-notebook-qa-checklist
description: QA steps for every lesson/homework notebook pair before committing; includes homework-specific checklist
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 9430f52d-1b80-4fc4-95db-c882115cdc96
---

## For every lesson pair (session notebooks)

Before committing any student+SOLUTION pair:

1. **Title**: student title must NOT include "(SOLUTION)"
2. **SOLUTION leak**: grep student code cells for "SOLUTION" — only `# ADD CODE HERE` allowed.
   **This grep is not sufficient on its own** (established 2026-06-24, Exam 1
   incident): a leak doesn't need the word "SOLUTION" in it — it can just be
   complete, working code and fully-written analysis with no blanking at all.
   The reliable check is a full cell-by-cell diff of student vs SOLUTION: any
   cell that's supposed to require student work (not given data, not
   instructions) that comes out byte-identical to SOLUTION is a leak. Do this
   on exams especially, not just homework — Exam 1's real take-home exam had
   this exact bug in its Application section.
3. **Em-dashes**: scan all cells for `—`; replace with comma, colon, or semicolon by context
4. **Instructor notes**: scan for "list comprehension", "next class", "for the curious", "ignore", "TODO" — not for students
5. **In-class assignment**: every lesson needs callout after the last Your Turn (see boilerplate below)
6. **Execute SOLUTION**: `jupyter nbconvert --to notebook --execute` (add `--allow-errors` if broken-code problems exist)
7. **HTML preview**: render old+new for both student and solution; open in Safari in this order: old solution, new solution, old student, new student. Priority view is solution vs old solution side by side.
8. **SOLUTION completeness**: SOLUTION must have all student question text PLUS solutions — not solutions only

## For homework notebooks

Additional checks:
- **Math/output consistency**: verify solution output matches what question says (e.g., if question says "13.0", solution must produce "13.0" — not "13.000" from `:.3f` or "13.0" via unexpected `round()`)
- **Don't add `round()`** unless the question explicitly asks for it
- **Verify cell match**: every student markdown cell id should appear in SOLUTION with identical content (run verify script)
- **Broken-code sections**: SOLUTION should show buggy cell immediately before fixed cell; use `--allow-errors` to execute

## In-class assignment boilerplate

```
---
## 📋 Today's In-Class Assignment

**Your Turn #N above is your in-class assignment for today. Submit it to Canvas before you leave.**

To submit:
1. Make sure your code in the cell above runs without errors (press Shift+Enter to run it)
2. Take a screenshot of your code and its output
3. Go to the module on Canvas that this lesson was part of and find today's in-class assignment, due at midnight
4. Upload your screenshot

*If you have multiple screenshots, combine them into a single PDF before uploading.*

**You only need to show that you tried; this is graded on effort, not perfection.**

---
```

## For plotting lessons (add automatically, no need to ask)

Before the "Up Next" cell:
- Matplotlib gallery image (from `_old/1_introPy_SOLUTION.ipynb` cell 117)
- Link to `https://matplotlib.org/stable/gallery/index.html`

## Homework rubric pattern

- 1 pt per individual task line, listed inline with each instruction
- AI disclosure = single 2-pt "AI Reflection" section at the very end of the homework (NOT per-task bullets)
- SOLUTION must have BOTH the buggy version and the fixed version for broken-code problems
- AI policy goes in the title/header cell, not as a separate problem

## LaTeX in notebooks

Use single braces `{a^2 + b^2}` not double `{{a^2 + b^2}}`. Double braces are Python `.format()` escapes — they leak into JSON and render wrong in notebooks.

## Execution

- Regular notebooks: `jupyter nbconvert --to notebook --execute`
- Notebooks with intentionally broken code: add `--allow-errors`
