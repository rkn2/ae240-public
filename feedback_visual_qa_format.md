---
name: feedback-visual-qa-format
description: Default to opening rendered HTML in Safari for notebook visual QA when Becca is on her computer; only build a merged PDF when she says she's on her phone
metadata:
  node_type: memory
  type: feedback
  originSessionId: 77c9f38e-9d01-4209-b377-baed98cc9127
---

When Becca is at her computer (not SSHed in, not on her phone), default to
the plain `nbconvert --to html` + `open` workflow from [[tooling-nbconvert]]
for visual QA of notebooks — render each notebook to HTML and open it in
Safari. Don't reach for the [[reference-screenshots-to-pdf-skill]] merged-PDF
pipeline unless she explicitly says she's on her phone right now; she'll tell
you when that's the case.

**Why**: stated directly 2026-06-24 ("now that I'm back on my computer you
can just open the pages in html in safari like we were doing before... I only
need the pdfs when I am on my phone and I'll let you know"). The PDF pipeline
is heavier (headless Chrome render + merge) and was built for the phone/SSH
case specifically, not as the general default.

**How to apply**: ask or infer which device she's on before picking a format
if it's not obvious from context; default to HTML+Safari absent a signal she's
on her phone.
