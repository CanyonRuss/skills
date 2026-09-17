---
name: kickoff-prompt
description: >
  Write the opening prompt for the next session — the text the user
  pastes into a fresh chat to start work with the context this session
  already has. Use when the user asks for a kickoff prompt, a start
  prompt, an opening prompt, "the prompt for the next session," or asks
  what they should paste into the next chat to pick this up. Companion
  to the handoff-doc skill, not a replacement: handoff-doc writes the document,
  this writes the instruction that sends the next session to it.
---

Write the opening user turn for the next session. The reader is a model with no memory of this session. Its job is to point and prioritize, not to transfer state — name the documents rather than summarizing them. Keep it concise: a short prompt, never a document.

Emit it as a single fenced code block in chat and nothing else, so the user can copy it in one click. Use four or more backticks on the outer fence if the content includes its own.

Include what this next session actually needs, in the imperative. You have the most context about what that is — use that judgment. Treat these as a menu, not a checklist: take what applies and leave the rest, since a heading with nothing real under it is worse than its absence.

- **Mission** — what the session is for, and how much latitude it has: executing a settled plan, or interpreting an open one.
- **Deliverable** — what it should produce and where that goes, when there's a clear one. When "done" means more than committed — a deploy, a second repo, a push — say so, or the session will stop at the commit.
- **Repo state** — repos and absolute paths, current branch, whether the tree is clean, and any uncommitted or unpushed work being inherited.
- **Ground truth at entry** — the commit it should be standing on, plus a one-line baseline and the command that checks it, framed as verify-before-work. A tripwire, not a status report; what's passing and why belongs in the handoff.
- **What to read, in order** — documents, files, artifacts, and the commands that establish current state; where each lives, and any sections to pay particular attention to.
- **What not to read, and why** — superseded specs, stale phase reports, anything carrying rulings later reversed. The next session can't tell which documents went stale, and will believe them.
- **What to load first** — memory scopes and anything else the next session can't discover on its own.
- **Environment gotchas** — what breaks a session in its first few commands. State them as conditions to check, not as a list of known instances — an enumerated list reads as complete and won't be.
- **Critical constraints** — settled points or gotchas that would derail the session early, marked for what they are: binding, or a prior session's call the next one may reopen. The rest stay in the handoff.
- **Handback protocol** — what to do on hitting a gap mid-work: surface it and stop, never resolve it silently inline.
- **Interaction mode** — whether to check in as work lands or run to completion. Code sessions default to running to completion, so say when they shouldn't.

**End every prompt by telling the next session to read everything named, then state back what it understands the session to be for and raise any questions or gaps it sees — before doing any work.**

When a work-mode skill fits the session, name it as the last line so it loads with the first turn.

If material worth carrying doesn't fit in a prompt and no handoff document exists yet, say so and let the user decide whether they want one.

Redact secrets and personal data — say where they live instead.
