---
name: feedback-verify-cited-numbers
description: When a homework/exam SOLUTION cites a specific worked-example number in prose, actually run the code to verify it before trusting it
metadata:
  node_type: memory
  type: feedback
  originSessionId: e3eb0bcf-d905-49e8-9993-0c1b61939593
---

When a SOLUTION's written answer cites a specific numeric example (e.g. "the
optimal height is approximately X ft", "(e.g., Optimal Investment of 15.0k
yielding ... 57.5)"), don't take the number on faith just because it sounds
plausible or is hedged with "e.g.". Actually run the underlying code (or a
faithful reproduction of it) and check the real output against the cited
number.

**Why**: found twice in one pass through Modules 13-14 (2026-06-24). Module
13's lamp-illumination homework cited "3.5412 ft" as the derivative-based
optimum; the real computed value (running the exact SOLUTION code) is
3.7774 ft — a 6.8% miss, not "extremely close" as the prose claimed. Module
14's exam 3 cited "Optimal Investment of 15.0k yielding ... 57.5"; 57.5 is
literally the raw data point at Investment=15 in the given dataset, not the
fitted-curve optimum from `curve_fit` + `minimize` (real answer: 14.67k /
56.06). Both read as a human typing a plausible-sounding number instead of
running the cell — same root cause as the Module 06 regression-number bug
and the Module 11 iteration-overshoot bug, just a third instance of the
pattern.

**How to apply**: this is a habit, not a one-off fix. Any time QA touches a
notebook with curve_fit/minimize/regression output cited in prose (not just
shown as code output), reproduce the computation standalone (a quick script
is enough) before accepting the cited number. If the actual data has no
randomness/seed dependency, the check is cheap and the result is
deterministic, so there's no excuse to skip it. See
[[project-module5-intro-python-lesson-review]] for the specific instances.
