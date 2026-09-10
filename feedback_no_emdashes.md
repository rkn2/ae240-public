---
name: feedback-no-emdashes
description: "Never use em-dashes (—) or stock LLM-sounding words (e.g. 'crucial') in course materials or chat responses"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b3ee4b44-2301-48a5-b730-a9e4d1916522
---

Do not use em-dashes (—) anywhere: not in notebook/lesson content I write, and not in chat responses.

**Why**: Becca explicitly asked me to stop (2026-06-22), after I'd used 23 of them across new cells in a single notebook restructuring pass. She wants this remembered as a standing rule, not just a one-off fix.

**How to apply**: when writing any prose (course materials, docs, chat replies), use a period, colon, comma, or parentheses instead of an em-dash, depending on what reads naturally. Before finishing a writing task, it's worth scanning what was just written for the em-dash character and rewriting any hits. Note: when grepping `.ipynb` (JSON) files for em-dashes, the raw character often won't match, because Python's `json.dump` escapes non-ASCII characters by codepoint (U+2014) by default. Grep for the escaped form too (or pass `ensure_ascii=False` when writing JSON, so the real character round-trips and stays greppable).

## Stock LLM-sounding words

Same standing rule extends to individual words that read as AI-generated,
not just em-dashes. Becca flagged "crucial" specifically (2026-06-24, Module
08 homework: "remove the word crucial since that is an llm word") and asked
for it to be replaced with "important". Treat this as one instance of a
broader pattern, not a one-off: words like "crucial", "delve", "leverage",
"robust", "pivotal", "seamless" read as AI-written and should be swapped for
plainer phrasing when writing course materials. When in doubt about whether a
word reads as LLM-flavored, prefer the more ordinary synonym.
