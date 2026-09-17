---
name: working-doc
description: >
  Spin up a working doc — a live scratchpad that captures the state of
  in-progress work (findings, open questions, decisions) and grows as the
  work proceeds. Use whenever the user asks to start, create, or draft a
  working doc, or to capture work "as we go", "keep this somewhere," or
  "track what we find." Also covers running a full Cleanup — a
  consistency and formatting pass — on an existing working doc; trigger
  on "clean up the doc," "run a cleanup," "doc cleanup," or similar. Not
  the end-of-session handoff — that's the handoff-doc skill.
---

A working doc is a scratchpad — stand it up to hold the live state of the work (what's been found, what's still open, what's been decided) outside the chat. If there's already material in the conversation, capture that current state first, then grow the doc as the work proceeds; the goal isn't to create a finished document. It's session scratch, not memory: when something durable settles — a preference, or a decision worth keeping past this work — that graduates to the memory skill.

Produce it as a Markdown artifact titled `<topic>-working-doc` — no date in the filename. Put a short header block at the top (status, last-updated) so its currency is visible at a glance; for a doc that runs across sessions, a dated changelog at the bottom tracks how it moved.

You have the most context about what this particular doc needs — use that judgment. The sections below are a menu, not a checklist: take what fits the work, skip what doesn't, and add new ones as they become relevant. Order them however serves the work.

- **Current state** — where things stand right now; the orienting snapshot for a fast re-read.
- **Open questions** — what's unresolved. Track resolution in place — mark them Resolved / Unresolved / Deferred rather than deleting — so the doc shows what's closed and what's still live.
- **Decisions & rationale** — what was decided and *why*. The decision survives in the output; the reasoning is what evaporates and gets re-litigated, so capture it.
- **Findings** — what's been turned up: research, test results, observations.
- **References** — pointers to other docs, files, or artifacts this work produced or leans on.
- **Next steps** — what to pick up next.

Keep it current as the work moves — fold in new findings, log decisions as they're made, update open questions as they resolve.

Redact secrets, credentials, tokens, and personal data — reference where they live instead of reproducing them.

## Cleanup

A full consistency and cleanup pass over an existing working doc — for when repeated spot updates (each touching one section) have let sections drift out of sync with each other, or left formatting artifacts behind. Trigger on "clean up the doc," "run a cleanup," "doc cleanup," or similar.

1. Read the doc in full, top to bottom.
2. Cross-check consistency — compare each section against the others and against the current state established in this conversation. Flag or fix: claims that contradict a later decision, open questions that have since resolved but aren't marked, stale "current state" language, references to since-abandoned approaches.
3. Formatting pass — fix broken Markdown, duplicate or orphaned headers, inconsistent list/bullet styles, and stray fragments left by partial or interrupted writes.
4. Update the header block (status, last-updated).
5. Flag anything genuinely ambiguous rather than resolving it silently — if two sections disagree and it's not clear which is current, surface it and ask rather than guess.
6. Update the changelog if appropriate — for docs that run across sessions, add an entry summarizing what the cleanup changed.
7. Report back short: what changed, what's flagged. Not a full diff dump.
