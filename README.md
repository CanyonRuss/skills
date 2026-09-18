# Canyon R's Skills

## What are skills?

Skills are short Markdown instruction files that change how an AI assistant works with you. They're written and tested with Claude, and they follow the open [Agent Skills](https://agentskills.io/) standard, so any of the tools that read `SKILL.md` (Codex, Cursor, Gemini CLI, Copilot, and dozens more) can use them.

## Are these for you?

These are for people who use AI chat or agents to *think, decide, and plan*, not only to generate code, and who run work that spans more than one conversation. If you mostly want an assistant to produce an answer and stop, you probably don't need them.

- **Working modes** change *how the assistant behaves for the rest of a session*: how it interacts around a problem and what its frame is.
- **Working docs** externalize the information so that it doesn't get lost to context drift or between sessions.

## The skills

Each name below links to the skill file, so you can read exactly what it tells the assistant before you install it. The links go to the coding-agent version; the chat version sits under the same name in `chat/`.

### Working modes

You turn a mode on by naming it. It won't switch on by itself, and it stays on until you switch to another. (One exception: `troubleshooter-mode` can be called if you describe needing to investigate a problem or symptom.) Each mode is built on two named frames: established concepts the model already knows, so naming them does the work of a long prompt. That's why these files are short and hit hard.

- **[`explorer-mode`](skills/explorer-mode/SKILL.md)**: Opens a problem up instead of solving it. Generates angles, framings, and questions; follows tangents; deliberately holds off on converging to an answer. For when you don't yet know what the question is.
  - *Frames: [divergent thinking](https://en.wikipedia.org/wiki/Divergent_thinking) · [negative capability](https://en.wikipedia.org/wiki/Negative_capability)*
- **[`interrogator-mode`](skills/interrogator-mode/SKILL.md)**: Takes a vague idea, plan, or "we're going to do X" and questions it until it's explicit: surfaces assumptions, pins down undefined terms, finds the edges of scope, drags out the decisions nobody noticed they were making. Stops before choosing.
  - *Frames: [design-tree](https://en.wikipedia.org/wiki/Design_space_exploration) [frontier](https://en.wikipedia.org/wiki/State_space_search) · [Ladder of Inference](https://en.wikipedia.org/wiki/Ladder_of_inference)*
- **[`evaluator-mode`](skills/evaluator-mode/SKILL.md)**: Pressure-tests a direction you already have. Traces what it entails and costs, steelmans the alternatives, finds what it's quietly resting on, until it's solid enough to plan on. Refines a direction; doesn't invent one.
  - *Frames: [second-order thinking](https://fs.blog/second-order-thinking/) · [steelmanning](https://en.wikipedia.org/wiki/Straw_man#Steelmanning)*
- **[`planner-mode`](skills/planner-mode/SKILL.md)**: Turns a direction into a real plan that ends in concrete next actions. Plans around the constraint that actually gates the outcome, and doesn't oversubscribe *your* time. Plans the work; doesn't do it.
  - *Frames: [GTD Natural Planning Model](https://en.wikipedia.org/wiki/Getting_Things_Done) · [Theory of Constraints](https://en.wikipedia.org/wiki/Theory_of_constraints)*
- **[`implementer-mode`](skills/implementer-mode/SKILL.md)**: Executes an existing plan. Verifies each step actually worked (the tool result, not the narration), and when reality diverges from the plan, stops and tells you rather than improvising around it.
  - *Frames: [execution monitoring](http://www.cs.toronto.edu/~fritz/publications/depth_oral.pdf) · [belief revision](https://en.wikipedia.org/wiki/Belief_revision)*
- **[`validator-mode`](skills/validator-mode/SKILL.md)**: Establishes what's actually true about a system and leaves a record someone else can check. Treats a green test suite as an instrument you trust only once you know what it measured; records every claim with its basis; hands back findings, not quiet fixes. For "prove this works before the next phase rests on it."
  - *Frames: [audit](https://en.wikipedia.org/wiki/Auditor_independence) · [experimental design](https://en.wikipedia.org/wiki/Design_of_experiments)*
- **[`troubleshooter-mode`](skills/troubleshooter-mode/SKILL.md)**: Diagnoses a real system that's broken and nobody knows why. Works it as a differential diagnosis: rules causes out rather than confirming the first plausible one, least-invasive test first, calls a hypothesis a hypothesis, and stops when it's stopped learning.
  - *Frames: [differential diagnosis](https://en.wikipedia.org/wiki/Differential_diagnosis) · [lean](https://en.wikipedia.org/wiki/Lean_software_development)*

### Working docs

For work that outlives one conversation.

- **[`working-doc`](skills/working-doc/SKILL.md)**: A live scratchpad the assistant keeps current as you go: where things stand, what's decided *and why*, what's still open, what you've found. Includes a cleanup pass for when it drifts.
- **[`handoff-doc`](skills/handoff-doc/SKILL.md)**: At the end of a session, a document that transfers *state and intent* (decisions, rationale, next actions, gotchas) so a fresh session (or you, next week) resumes without re-deriving it all.
- **[`kickoff-prompt`](skills/kickoff-prompt/SKILL.md)**: The short prompt you paste into the next session. Points at the docs, sets the mission and constraints, and tells the assistant to read everything and state back what it understands before doing any work. Companion to `handoff-doc`.

## Why these skills

### Change how assistants work with ideas

I found when working with Claude, or other LLMs, they have a real pull to converge on an answer and hand you back a solution. Unfortunately this is rarely the way I want to work. I want an interactive, iterative process for thinking about and through a project, problem, or situation without just being handed back the easiest or most obvious answer. I want to guide the process, and use it to better understand both the problem space and what I want out of a solution or outcome. 

These skills first developed as Claude.ai styles, used to frame the way that a given session interacted and engaged with the topic or problem that I presented it with. Explorer Mode was the first attempt to get the session to hold open the space, and talk about the larger themes and issues rather than jumping to "the answer" on every turn. I found it to be not just helpful, but engaging on how it allowed me to drive the conversation and really dig into different areas of the topic. 

From this initial success I expanded to create what I saw as a basic workflow for thinking, planning, and executing on an idea. 

**explore → interrogate → evaluate → plan → implement → validate**

You can start anywhere in the process you need based on what you are trying to work on. I generally use them each in its own session with each handing off to the next. These became skills when Claude discontinued styles and this is why they are written to invoke a style-like change in the assistant.

### Setting a frame for the assistant

One of the most powerful concepts I landed on when building and testing these skills is the idea of a cognitive frame or [semantic anchor](https://llm-coding.github.io/Semantic-Anchors/).

This allows you to reference a larger concept that already exists within the training data without needing to spend context explaining the details. It's one of the main reasons that the skills are so compact but carry such an outsized impact on the assistant behavior. 

I have specifically chosen the frames for each skill based on their correlation and ability to support each other or guard against potential pitfalls of a specific anchor. They are used to both frame the behavior and set the assistant's understanding of success so that it doesn't continue to drive to a single answer.

**troubleshooter-mode** was the first where I used these anchors to overcome the assistant's tendency to take any anomaly it finds in a system and declare it the **Root Cause**, until it finds the next one and the cycle continues. I wanted to empower the session while focusing it on real causes not just the first thing it finds. This makes it useful for troubleshooting both systems and processes.

**interrogator-mode** is based on Matt Pocock's popular [grill-me skill](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me) but adapted into my format with the addition of the **Ladder of Inference** anchor and made less prescriptive on the format of the questions.

### Working and Handing off

The Working docs set of skills solved two specific issues I, and others, have encountered. One was the context drift within a long session where earlier research, conclusions, decisions, or references would get lost or muddled. So I created the **working-doc** skill to give the session a scratch pad to keep notes in while we worked. I also found that after many ongoing edits the documents could, themselves, get muddled so I added the **Cleanup** function for the assistant to fix any doc issues.

The second issue was continuing work from one session to the next. I was inspired by Matt Pocock's [Handoff skill](https://github.com/mattpocock/skills/tree/main/skills/productivity/handoff) but felt it was very light on direction so I made my own version that was more prescriptive on what the **handoff-doc** should include.

This then led to the **kickoff-prompt** skill which facilitates one session to create the prompt to start the next one. This way the handoff-doc can carry the majority of the context forward while the kickoff-prompt gives the new session its direction and pointers to all the relevant information and docs. While not strictly a "doc" skill I think it fits into the overall flow of the other skills so I'm including it with them in **Working docs**.

### Why two copies of each skill

These skills are useful for any LLM interface but the chat or Cowork surface offers different functions and tools than a coding-capable harness. Therefore each skill has a version tuned for those capabilities. The seven working modes are nearly identical across the two; the three docs skills differ more, because the coding-agent versions add sections about repository state, test status, and environment that don't apply in chat. `troubleshooter-mode` is the same file in both.

## Install

Install as a plugin if you want updates automatically; copy the files if you want to edit them. Each skill has two versions: one for coding agents (`skills/`) and one for chat (`chat/`). Same name either way; pick by where you're running it.

### Claude Code

Add the marketplace once, then install either or both families:

```
/plugin marketplace add CanyonRuss/skills
/plugin install working-modes@canyonr-skills
/plugin install working-docs@canyonr-skills
```

Plugin skills are namespaced, so you invoke them as `working-modes:explorer-mode`, `working-docs:handoff-doc`, and so on.

To run from a local clone without the marketplace:

```bash
git clone https://github.com/CanyonRuss/skills.git
claude --plugin-dir ./skills
```

### claude.ai (chat)

claude.ai has no plugin marketplace, so skills are uploaded by hand. Cowork uses the same skills as your claude.ai account, so one upload covers both.

1. Download the skill's `SKILL.md` from **`chat/<skill-name>/`** in this repo.
2. In claude.ai, open **Settings → Customize → Skills**, click **Add**, choose **Upload skill**, and select the file.
3. Enable it. Repeat for each skill you want.

Every skill here is a single `SKILL.md`, so you upload the file directly. A zip is only needed for skills that bundle extra files. There's no auto-update in chat; to update a skill, upload the file again. Anthropic's [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude) has the current UI.

### Other coding agents

Every skill is a folder containing a `SKILL.md`, and `skills/` is laid out the way most agents read directly. Pick your tool:

- **Codex:** add the repo as a marketplace, then install **canyonr-skills** from the Plugins directory. Codex sees all ten skills as one plugin.
  ```bash
  codex plugin marketplace add CanyonRuss/skills
  ```
- **Gemini CLI:** installs one skill at a time into `~/.gemini/skills/`.
  ```bash
  gemini skills install https://github.com/CanyonRuss/skills.git --path skills/explorer-mode --consent
  ```
- **Hermes Agent:** install single skills straight from the repo, or add it as a tap to browse them.
  ```bash
  hermes skills install CanyonRuss/skills/skills/explorer-mode
  hermes skills tap add CanyonRuss/skills
  ```
- **Cursor:** copy the folder into `.cursor/skills/<skill-name>/`.
- **Claude Code, without the plugin:** copy into `~/.claude/skills/<skill-name>/` for yourself, or `<project>/.claude/skills/<skill-name>/` for one project.
- **Anything else:** copy the folder to wherever that tool loads skills from.

Or let the [skills CLI](https://github.com/vercel-labs/skills) do the copying. It installs into whichever agents it finds on your machine:

```bash
npx skills add CanyonRuss/skills --list                 # see what's here
npx skills add CanyonRuss/skills                        # install everything
npx skills add CanyonRuss/skills --skill explorer-mode  # or just one
```

### Updating

- **Claude Code plugin:** `/plugin update working-modes@canyonr-skills` (and the same for `working-docs`).
- **skills CLI:** `npx skills update`
- **Hermes:** `hermes skills update`
- **Codex:** update from the Plugins directory.
- **claude.ai:** upload the skill's `SKILL.md` again; there's no auto-update in chat.
- **Gemini CLI, or copied by hand:** install or copy the folder again.

## Contributing

Issues and pull requests are welcome. Skills here follow the [Agent Skills spec](https://github.com/anthropics/skills/tree/main/spec): a folder with a `SKILL.md` whose frontmatter has a `name` and a `description`.

## License

[MIT](LICENSE) © 2026 Canyon R
