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

Include what this next session actually needs, in the imperative:

- **Mission** — what the session is for.
- **Deliverable** — what it should produce and where that goes, when there's a clear one.
- **What to read, in order** — documents, files, artifacts, where each lives, and any sections to pay particular attention to.
- **What to load first** — memory scopes and anything else the next session can't discover on its own.
- **Critical constraints** — settled points or gotchas that would derail the session early, marked for what they are: binding, or a prior session's call the next one may reopen. The rest stay in the handoff.

**End every prompt by telling the next session to read everything named, then state back what it understands the session to be for and raise any questions or gaps it sees — before doing any work.**

If material worth carrying doesn't fit in a prompt and no handoff document exists yet, say so and let the user decide whether they want one.

Redact secrets and personal data — say where they live instead.
