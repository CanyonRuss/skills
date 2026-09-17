---
name: handoff-doc
description: >
  Capture the state and intent of the current work into a handoff
  document so a fresh chat — or the user returning later — can resume
  without re-deriving context. Use whenever the user asks to create,
  write, or prepare a handoff (e.g. "create a handoff doc", "let's get
  this ready to hand off", "write this up for the next session"), or when
  work is winding down and they want to capture state for later — even if
  they don't use the word "handoff". Prefer this over an ad-hoc summary;
  the goal is transferable state, not a recap of the discussion.
---

Write a handoff document that transfers the *state and intent* of the current work, not a transcript of the conversation. The reader is a fresh chat (or the user returning later) with no memory of this session. Include enough that the next session can pick up the thread from this handoff and the docs it references — and nothing it could reconstruct on its own.

Produce it as a Markdown artifact, titled `<topic>-handoff-<YYYYMMDD>`. Anchor it with the date and, if the user gave one, the stated focus of the next session.

You have the most context about what this particular handoff needs — use that judgment. Decide what to include based on what the next session will actually need, not on filling out sections.

Treat these as a menu, not a checklist — capture what's relevant and would otherwise be lost:

- **Objective** — what this work is ultimately for.
- **Current state** — where things stand; what's settled and what's still open. Where it matters, flag what's confirmed versus assumed.
- **Decisions & rationale** — choices made and why, including paths considered and ruled out. Often the most valuable content, and the easiest to over-include — carry the reasoning the next session needs, not a full archaeology of how you got there.
- **Next actions** — what the next session should pick up, ideally with a clear starting point.
- **Open questions, risks, gotchas** — unresolved issues, things that surprised us, edge cases worth knowing about.
- **References** — point to existing artifacts (docs, plans, prior chats, files, URLs) rather than restating them.
- **Suggested skills** — skills the next session should invoke, with a one-line reason each.

Add sections these don't cover, and order them however serves this handoff.

Redact secrets, credentials, tokens, and personal data — reference where they live instead of reproducing them.

If the user described what the next session will focus on, weight the document toward it and trim what doesn't serve it.
