---
name: project-drive-link-migration
description: "Migration from GitHub Colab links back to Google Drive Colab links — in progress, drive_links.json not yet created"
metadata: 
  node_type: memory
  type: project
  originSessionId: 4c40e175-13f2-475f-a862-df4a6c4a4b64
---

Canvas scripts now read `drive_links.json` instead of building GitHub URLs, but the file doesn't exist yet.

**Why:** GitHub repos are all-or-nothing; Drive gives per-file/folder permissions needed for solutions (TAs only) and time-gated exams.

**Drive folders already created** (2026-06-26): ae240 root `1jGPkTy2YOTbBQUDKfELcOazcFucIKeSY`, module subfolders for 05-14 hardcoded in `upload_to_drive.py`.

**Remaining steps:** (1) set up `credentials.json` from Google Cloud Console + `pip install google-auth-oauthlib google-api-python-client`, (2) run `python upload_to_drive.py` to upload 63 notebooks, (3) run `python build_drive_map.py 1jGPkTy2YOTbBQUDKfELcOazcFucIKeSY` to generate `drive_links.json`, (4) run `python update_readme_links.py`, (5) set Drive permissions manually (solutions/exams restricted, blanks public).

Files: `build_drive_map.py`, `upload_to_drive.py`, `update_readme_links.py`, `cavasIMporting/update_module05.py`, `cavasIMporting/update_modules06_14.py`.
