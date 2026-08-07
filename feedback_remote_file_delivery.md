---
name: feedback-remote-file-delivery
description: "Don't rely on SendUserFile when Becca is SSHed into giraffes-Mac-mini — it doesn't reach her laptop"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b3ee4b44-2301-48a5-b730-a9e4d1916522
---

When Becca is working by SSHing from her laptop into `giraffes-Mac-mini` (hostname `giraffes-Mac-mini`, user `becca`) and driving Claude Code there, `SendUserFile` attachments and `open <file>` only land on the Mac mini — they do not cross the SSH session back to whatever client she's actually viewing the conversation in on her laptop. Confirmed: she could see opened/sent files "on giraffe" but not on her laptop.

**Why**: her Claude Code client in this setup is a bare SSH terminal session into the Mac mini, not a web/desktop app with its own out-of-band channel back to her laptop — so file-delivery tools that assume such a channel exists silently no-op for her.

**How to apply**: when she needs to view a generated file (HTML render, image, etc.) while in this SSH setup, skip `SendUserFile`/`open` as the primary path. Instead give her a copy-pasteable `scp` (or equivalent) command to run from a separate terminal *on her laptop* (outside the current SSH session), pulling from the Mac mini using whatever host/user she already used to SSH in. Mention the exact remote path. See [[tooling-nbconvert]] for the kind of file this came up with (rendered notebook HTML).

**Update (conclusively resolved 2026-06-22)**: inline images from the Read tool also don't render in her terminal setup — Ghostty (supports Kitty graphics protocol) stacked with tmux (and sometimes zellij). Ran a full isolation test:
- Added `set -g allow-passthrough on` to `~/.tmux.conf` — alone, did not fix it.
- Added `set -as terminal-features ',xterm-ghostty:sixel'` (closed a real gap: tmux's live `client_termfeatures` already auto-detected sixel support, but the static `terminal-features` config didn't declare it) — reloaded live, still did not fix Claude Code's own image rendering.
- Wrote a dependency-free Python script (`/tmp/kitty_emit.py`, stdlib only — `chafa` install failed, needs `sudo chown` on shared `/opt/homebrew`, avoided) that emits raw Kitty graphics protocol escapes directly, and injected it into her live tmux pane via `tmux send-keys` (after confirming the right pane: match `$TMUX`'s session id against `tmux list-sessions -F "#{session_name} id=#{session_id}"`, then cross-check with `tmux list-clients` for which one is actually attached/focused). **This rendered correctly** — she saw it via a phone photo of her real terminal screen.
- Conclusion: the transport (SSH+tmux+Ghostty) fully supports Kitty graphics now. The remaining gap is specifically that the Claude Code CLI's own image-output code doesn't render in her tmux session even though the pipe works — i.e. it's a CLI-internal limitation, not a config problem. **Stop troubleshooting this from the tmux/Ghostty config side — it's a dead end, conclusively tested.** Default to her phone for any inline image/screenshot when she's in this SSH+tmux setup; don't suggest more terminal-graphics config tweaks unless Claude Code itself changes.
- Side finding: `tmux send-keys` into a live pane is risky if she's also typing at the same time (caused one harmless mix-up, no data loss) — always tell her to stop typing/watch-only before sending, and warn her first.
