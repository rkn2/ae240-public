---
name: tooling-nbconvert
description: nbconvert is installed in .venv-test to render any .ipynb to standalone HTML for local review
metadata: 
  node_type: memory
  type: reference
  originSessionId: b3ee4b44-2301-48a5-b730-a9e4d1916522
---

`.venv-test/bin/jupyter nbconvert --to html --output <out.html> <notebook.ipynb>` renders a notebook (markdown, code, embedded base64 images) to a self-contained HTML file Becca can open directly in her browser — no GitHub or Jupyter server needed.

Installed packages: nbconvert + deps (mistune, jinja2, bleach, beautifulsoup4, etc.) in `.venv-test`. No pandoc needed for HTML export.

Note: the built-in Read tool can't render these course notebooks once they contain embedded base64 images — the base64 blows past the 25000-token read limit (and the file-size cap for very large old notebooks). nbconvert + `open <file>.html` is the reliable fallback for visualizing them.

**For showing code/output cells inline in chat** (works even when Becca is SSHed in and `open`/SendUserFile can't reach her laptop — see [[feedback-remote-file-delivery]]): nbconvert alone isn't enough since Read can't load the full HTML. The working pipeline:
1. `jupyter nbconvert --to html --execute` the notebook (kernel `python3` is registered in `.venv-test`) to get real outputs baked in.
2. Use BeautifulSoup (installed as an nbconvert dep) to extract just the `<head>` (styles/MathJax) plus the specific `jp-Cell` divs wanted, into a small standalone HTML file.
3. Screenshot that minimal HTML with headless Chrome: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu --no-sandbox --hide-scrollbars --force-device-scale-factor=2 --window-size=900,1000 --screenshot=out.png file:///tmp/snippet.html`. Headless Chrome works fine over SSH (no TCC/Screen-Recording permission needed) — confirmed working 2026-06-22.
4. Read the resulting PNG — it renders inline in the chat response itself, which does reach Becca's laptop even over plain SSH (unlike SendUserFile/`open`).

This gives a faithful preview of syntax highlighting, cell input/output styling, and rendered LaTeX/markdown — closer to "how it'll actually look" than a plain fenced code block.

See [[project-module5-intro-python-lesson-review]] for the task this came up in.
