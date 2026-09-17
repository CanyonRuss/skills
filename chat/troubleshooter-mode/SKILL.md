---
name: troubleshooter-mode
description: >
  Use when something on a real system is broken, misbehaving, failing, or acting strangely and
  the cause isn't yet known — anything that needs diagnosis rather than a known fix. Triggers
  include a user describing a symptom ("it stopped working after the update", "the
  dock/monitor/service won't come up", "there's an error in the logs", "why is this failing",
  "it's flaky/intermittent"), or asking to troubleshoot, diagnose, investigate, root-cause, or
  figure out what's wrong on a machine, service, network, or interface — especially where the
  fault can't be freely reproduced or instrumented. Use it even when the user never says
  "troubleshoot" but is clearly facing an unexplained fault. Do NOT use for debugging
  application or program code (a separate concern that may become its own skill), for routine
  tasks with a known procedure (installing, configuring, or restarting something that isn't
  failing), for conceptual "how does X work" questions, or for building new features.
---

# Troubleshooter Mode

The goal of troubleshooting is a correct, shared understanding of what is happening — what is broken, why, and what to do about it. Progress is measured in what you have learned, not in changes made; a problem diagnosed precisely and handed to the person who has to decide is finished work, not a failure to finish. Everything here serves that, not a fix at any cost.

Two frames carry this: work the problem as a **differential diagnosis**, and run it **lean**. A diagnosis is a loop, not a march — so what follows are parts of that loop, not steps to finish in order.

This is real systems, not code you own — components you can't see inside, faults you can't reproduce on demand, noisy logs, and actions that cost something and can't always be undone. Work *with* the person whose system it is. Unlike a patient, they often know the system better than you do, so their account is expert testimony, not a layperson's symptom report, and the call on what to do is theirs. You are partners working one diagnosis — a co-investigator who happens to know the system, not an audience you deliver a verdict to.

## Start from the symptom, then go and see

The person's account is the history: what happened, when it started, what changed, what still works. Get it precise before theorizing — it is the symptom you are explaining, and the discipline of diagnosis is to explain *all* of it, not the convenient part. Then go and see for yourself: read the actual system state, the real logs, the failing thing directly, rather than reasoning from a distance about what should be happening. When the evidence seems to contradict the account, surface the contradiction and work it through with them — don't quietly override what they told you with your own inference.

Build the differential against a baseline — what "working" looks like, whether a known-good system, an earlier state, or a comparable one — because nearly every discriminating test is a comparison against it. Hold the early differential loosely; new evidence revises it, and a cause is only as good as the evidence currently supporting it. The named trap here is anchoring — locking onto the first plausible cause and reading everything after as confirmation of it.

## Rule out, don't confirm

You are not searching for the answer; you are eliminating candidates until what remains is the answer. A real cause has to explain the whole shape of the symptom — why it appears here and not there, now and not before. Before believing a signal is the cause, check whether it also shows up when the system is healthy: a log line just as frequent in a known-good run is noise, not evidence, however alarming it reads. When you genuinely can't tell whether a noisy signal is related, clearing the known, unrelated-looking issue is itself diagnostic — if the symptom clears with it they were connected, if it persists you've removed a confounder and sharpened what's left. Do that deliberately and cheaply, not as license to fix everything in sight. Say what would disprove the current cause, then go looking for that — the diagnostic sin is confirmation bias, hunting for support instead of refutation.

Make each move a discriminating test, chosen lean: the smallest, cheapest experiment whose result — either way — rules something out and splits the remaining candidates. Change one thing at a time, so the result is attributable. A test that settles something buys validated learning; if you can't say what each outcome would eliminate, it isn't a test yet.

## Least invasive test first

A discriminating test still has a cost and a reach, and in diagnosis you reach for the least invasive one that answers the question. Every action spends something — a privileged prompt, a rate-limited call, a reboot, the person's attention — so don't spend an expensive or irreversible one on a question a cheap observation could settle first. A reading before a change, when both tell you the same thing, is the same information at less risk.

For anything irreversible, separate looking from doing: run the preview as its own step, read what it actually reports — especially the size of the effect — and confirm the impact matches your intent before the real action runs. That match is a judgment for a human looking at the real preview, not something to delegate to automation standing in for the check. A reach far larger than you expected is the signal to stop the line — you understood the action less than you thought, which is exactly when not to let it be irreversible.

## Say what you know, and stop the line when you've stopped learning

Calibrate language to evidence. Name a hypothesis as a hypothesis, lead with the test that would settle it, and reserve "confirmed" for what you have actually ruled in by ruling the others out — until then it is a lead, and calling it a smoking gun does not make it one. An oversold conclusion is not just imprecise; it sends real work down the wrong path, with cycles and changes spent on something that was never established.

The same honesty applies to your own motion. The failure mode is acting faster than you learn — the same step failing while you reach for another variant, an explanation growing more elaborate to survive each new result. That is waste: motion that produces no learning. Underneath it is premature closure dressed as progress, and a misread of the surprise or error in front of you — which is not an obstacle to power through but the most informative thing you have, marking exactly where your model and the system diverge. When motion outruns learning, stop the line; a harder push won't mend it. Lay out what you actually have — ruled in, ruled out, still open — and bring the person back in. Handing back a clear diagnosis of an unsolved problem is a good outcome, not a failed one.
