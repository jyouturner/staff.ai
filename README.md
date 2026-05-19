# staff.ai

A growing team of AI staff for Claude Code — installable role by role.

The idea is simple: instead of one monolithic assistant trying to be everything, you hire individual *roles* — a strategist, an advisor, a coach, a reviewer — and only the ones you need. Each role is a Claude Code plugin in this marketplace. Each plugin is opinionated, operator-grade, and refuses to fake expertise it doesn't have.

## Install the marketplace

Inside Claude Code:

```
/plugin marketplace add jyouturner/staff.ai
```

That registers the catalog. No plugins are installed yet — you choose which roles to hire.

## The team

### `ai-strategist`

A Socratic AI-strategy advisor. Walks an executive (or interview candidate) through the five-piece framework — **value → feasibility → sequencing → governance → execution** — and produces a board-ready slide-deck outline.

- Operator-grade questions, not consultant-grade. "Name the three metrics on this quarter's board slide" is the first question.
- Treats safety, security, compliance, and operating governance as a full strategic pillar (Phase 4), not a sub-bullet inside execution. For regulated industries this is often the difference between a strategy that ships and one the board pauses.
- Pressure-tests thin answers. Refuses to synthesize confidence the user hasn't earned.
- Tags every output slide as `[GROUNDED]`, `[THESIS]`, or `[THIN]` so the user knows what's ready for the room and what isn't.

Install:

```
/plugin install ai-strategist@staff-ai
```

Then run `/reload-plugins` and trigger the skill by asking something like "help me think through an AI strategy for my company" or "what's my AI strategy."

### `ai-native-engineer-rubric`

A hiring rubric for managers recruiting "AI-native engineers." Treats "AI-native" not as a single capability but as a 2x2 — *AI engineering specialty* (can build AI products) crossed with *AI-first operating model* (works with AI as coworker) — and forces the manager to specify which quadrant the role actually needs before sourcing.

- **Mode 1 (role specification):** walks the manager through defining the target role profile across four dimensions, before any candidates are screened. Output is a profile the manager can hand to recruiters.
- **Mode 2 (candidate evaluation):** scores a specific candidate against the specified role with evidence prompts for each dimension. Refuses ratings without evidence.
- No averaging, no single-score collapse. Output is a *shape of match*, not a recommendation.
- Calls out the most common AI-native hiring anti-patterns: "uses Cursor" treated as a signal, RAG demos treated as production experience, AI-strategy fluency confused for AI-engineering fluency.

Install:

```
/plugin install ai-native-engineer-rubric@staff-ai
```

Then run `/reload-plugins` and trigger the skill by asking something like "help me hire an AI-native engineer" or "I need to evaluate a candidate for an AI engineering role."

### `ai-native-org-designer`

A diagnostic and operating-model design tool for VP-Eng and CTO leaders running an AI-native engineering transformation. Built on the premise that the published AI-native playbooks (Anthropic, Shopify, frontier labs) are *existence proofs, not templates*. Diagnoses the org across eight dimensions — substrate, regulatory posture, deployment maturity, code review culture, talent pipeline, process load, leadership posture, dissent capacity — then derives an operating-model design from the diagnosis.

- **Mode 1 (rapid diagnosis):** eight-dimension readiness assessment with honest ratings. Stops there. Useful when the substrate isn't ready for design.
- **Mode 2 (full design):** diagnosis plus an operating-model design with principles, context-specific moves (each with cost and panel-objection-internalized), three-horizon sequencing, and non-negotiable outcome metrics.
- Internalizes the DORA-grade critique: refuses to ship a design without specifying change failure rate, MTTR, lead time, and senior attrition as the real success measures.
- Refuses to recommend moves that don't trace back to specific diagnostic findings. No templating.

Install:

```
/plugin install ai-native-org-designer@staff-ai
```

Then run `/reload-plugins` and trigger by asking something like "help me design an AI-native engineering org" or "we're rolling out AI tools across engineering, where do we start?"

*More roles to come.*

## Design principles

These principles shape every plugin in this marketplace:

1. **One plugin = one role.** A role is a senior practitioner with a defined scope. We don't ship grab-bag plugins.
2. **Opinionated over flexible.** Each role has a point of view. Frameworks run in order; phases don't get skipped just because the user wants to.
3. **Refuse to fabricate.** When the user's inputs are thin, the output says so. We don't reward bad inputs with polished outputs.
4. **Operator language, not consultant language.** "Who gets paged when this breaks" instead of "what's the operational ownership model."
5. **Earn the user's judgment within three questions.** A user should know quickly whether the role is wasting their time or giving them something they can use.

## Contributing a new role

Each role lives in `plugins/<role-name>/` with this structure:

```
plugins/<role-name>/
├── .claude-plugin/
│   └── plugin.json          # name, description, version
└── skills/
    └── <skill-name>/
        └── SKILL.md         # the actual instructions
```

Add a corresponding entry to `.claude-plugin/marketplace.json` and the role is part of the team.

When adding a role, ask: would a senior practitioner in that field recognize this as competent work? If the answer is "this is what an AI thinks a strategist sounds like" rather than "this is what a strategist sounds like," it isn't ready.

## License

MIT. See [LICENSE](./LICENSE).
