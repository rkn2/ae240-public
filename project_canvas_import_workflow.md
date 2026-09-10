---
name: canvas-import-workflow
description: "Canvas Fall 2026 imscc update — script location, approach, module status, next steps"
metadata: 
  node_type: memory
  type: project
  originSessionId: 4c40e175-13f2-475f-a862-df4a6c4a4b64
---

Canvas Fall 2026 import is in progress. All modules 05-14 are handled by one script.

**Why:** Replacing stale Drive-ID Colab links with stable GitHub/Drive links for Fall 2026.

**How to apply:**
- Script: `cavasIMporting/update_modules06_14.py` (committed to repo)
- Output: `cavasIMporting/ae240_fall2026_all_modules_updated.imscc` (gitignored, regenerate with `python3 cavasIMporting/update_modules06_14.py`)
- imscc workflow: import via Canvas Settings → Import Course Content → Canvas Course Export Package → "Select specific content"
- Test M05 first, then import remaining modules once verified

## Link strategy (decided this session)
- **Lesson notes + homework** → GitHub public repo (`rkn2/ae240-public`) for student files, private (`rkn2/ae240`) for solutions
- **Exam notebooks (actual exams)** → Google Drive links. Students can't browse to them; Canvas quiz is unpublished until exam day. Drive links are stable as long as files are never deleted+re-uploaded (update in place instead).
- **Practice exams + study guides** → GitHub public (students should access freely)
- **Mitigation for broken links**: run Canvas Link Validator (Settings → Link Validator) at start of each semester

## Module status

### Module 05 — FULLY REBUILT in script
New structure:
- Pre Lesson Activities (gptPreSurvey, ethicsPreSurvey)
- Lesson 1 materials: session1 (public) → session1_SOLUTION (private) → introPy_inclass1 (new quiz)
- Lesson 2 materials: session2 (public) → session2_SOLUTION (private, new item) → introPy_inclass2 (existing quiz renamed)
- Homework: assignment (HTML updated) → homework_SOLUTION (private)

### Module 06 — FULLY REBUILT in script
New structure:
- Lesson 1 materials: linReg_notes (public) → Sept9 zoom (unpublished) → linReg_notes_SOLUTION (private) → linReg_inclass quiz
- Lesson 2 materials: barChart_notes (public) → Sept11 zoom (unpublished) → barChart_notes_SOLUTION (private) → barCharts_inclass quiz
- Homework: Linear Regression Homework quiz (description updated with GitHub link to student hw notebook) → linReg_homework_SOLUTION (private)
- Note: homework student notebook link (`3_linReg_dataVis_homework_v26.ipynb`) is in the quiz description using `blob/v26` branch URL on private repo

### Modules 07, 11, 14 (exam modules) — URL substitution only so far, NEED DRIVE LINKS
- Current: practice exam + study guide → GitHub public ✓
- Still needed: upload actual exam notebooks to Google Drive, get IDs, update REAL SUBMISSION quiz descriptions
- Exam files (per module):
  - M07: exam_1_part1_v26.ipynb, exam_1_part2_v26.ipynb (+ solutions)
  - M11: exam2_part1_v26.ipynb, exam2_part2_v26.ipynb (+ solutions)  
  - M14: exam3_part1_v26.ipynb, exam3_part2_v26.ipynb (+ solutions)
- PRACTICE quiz descriptions in M07 should get link to exam_1_practice_v26.ipynb (GitHub public) — not yet done

### Modules 08, 09, 10, 12, 13 — URL substitution only, NEED STRUCTURAL REVIEW
- All Colab links updated to GitHub public/private URLs ✓
- Headers, ordering, zoom link visibility, quiz descriptions not yet reviewed
- Same pattern as M06: probably need lesson 1/2 headers, zoom links unpublished, quiz descriptions updated

## Key technical notes
- **Both url locations must be updated**: Canvas reads `<url>` from module_meta.xml AND from webLink XML files — script updates both
- **Sub-headers stripped from manifest**: Canvas creates standalone empty modules for manifest items without identifierref. Sub-headers belong only in module_meta.xml.
- **Manifest regex rule**: use `\n        </item>` (newline + 8 spaces) as terminator, never bare 8 spaces (substring of 10-space child tags)
- **imscc workflow notes**: see project memory `canvas-import-workflow` (this file) and script docstring
- **Public mirror**: `rkn2/ae240-public` syncs automatically via GitHub Action on every push to main (`sync-public.yml`)
- `*.imscc` excluded from git via `cavasIMporting/.gitignore`
