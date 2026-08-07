---
name: reference-screenshots-to-pdf-skill
description: Global Claude Code skill at ~/.claude/skills/screenshots-to-pdf that renders notebooks/HTML/URLs/images into one merged PDF
metadata: 
  node_type: memory
  type: reference
  originSessionId: ead0d7d6-535c-4b61-ac89-4d678a3268f1
---

Built 2026-06-23 as a generalization of the manual nbconvert+headless-Chrome
pipeline used in [[tooling-nbconvert]]. Lives at
`~/.claude/skills/screenshots-to-pdf/` (global, not project-scoped — usable
from any Claude Code project, not just ae240).

- `SKILL.md` — trigger description + usage steps
- `bootstrap.sh` — idempotent venv setup (pypdf, nbconvert, ipykernel, bs4)
- `make_pdf.py` — takes N sources (`.ipynb`, `.html`, image, URL, `.pdf`) in
  order, renders each via headless Chrome `--print-to-pdf`, merges into one
  output PDF with `pypdf`

Bakes in the delivery lesson from [[feedback-remote-file-delivery]]: the
SKILL.md instructs always printing an `scp user@host:path ~/Desktop/`
fallback alongside `SendUserFile`, since SendUserFile can silently fail to
reach her laptop when she's SSHed into giraffes-Mac-mini.

Tested working end-to-end on 2026-06-23 (rendered Module 06 homework
student+SOLUTION notebooks into one merged PDF).
