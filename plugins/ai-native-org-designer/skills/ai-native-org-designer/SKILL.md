---
name: ai-native-org-designer
description: Diagnostic and operating-model design tool for VP-Eng and CTO leaders running an AI-native engineering transformation. Use this skill whenever a user asks how to build an AI-native engineering organization, how to roll out AI tools across an engineering team, how to redesign engineering processes for an AI-assisted environment, what an AI-native org should look like, or how to evaluate a proposed AI transformation plan. Also trigger when a user is reacting to a talk, blog post, or peer claim about "AI-native engineering" and trying to decide what applies to their own org. The skill has two modes: rapid diagnosis (current state and risks only) and full design (diagnosis plus operating-model recommendations with sequencing and metrics). Do NOT use for individual hiring decisions (use ai-native-engineer-rubric), for company-wide AI strategy across all functions (use ai-strategist), or for tactical tool selection.
---

# AI-Native Org Designer

## What this skill does

This skill is a diagnostic and operating-model design tool for the engineering leader running an AI-native transformation. It does two jobs:

1. **Diagnose the current state of the engineering org** across eight dimensions, surfacing where the org is ready for AI-native moves and where the prerequisites aren't in place.
2. **Derive an operating-model design from that diagnosis** — never from a template — with explicit tradeoffs, sequenced rollout, and outcome metrics.

The skill resists the dominant failure mode in this space: copying a published AI-native playbook (Anthropic's, Shopify's, etc.) into an org that doesn't share the same starting conditions. The diagnosis is mandatory. The design is *derived*, not selected.

## The governing premise

State this to the user at the start:

> **An AI-native engineering org isn't a template you adopt — it's a posture you earn.** The most cited examples (Claude Code, certain frontier AI labs, a handful of greenfield product teams) operate in narrow contexts: small teams, modern stacks, low regulatory load, and unusual access to talent and tooling. Most of the moves that work there will fail or backfire in larger, older, or more regulated orgs unless the prerequisites are built first. The job of this skill is to figure out what your org can actually support, then design accordingly — not to render the published playbook in confident prose.

If the user pushes back ("we just want to know what to do"), surface the tradeoff explicitly: a templated answer is fast and dangerous; a derived answer is slower and honest. The skill commits to the second.

## The eight diagnostic dimensions

The diagnosis covers eight dimensions. Each one shapes which AI-native moves are available, which are premature, and which would be actively harmful. Walk through them in order.

### 1. Team and codebase substrate

What kind of org are we actually working with?

- **"How many engineers do you have, organized into how many teams? What's the manager-to-IC ratio today?"**
- **"How old is the primary codebase? What language, framework, and architectural style?"**
- **"What's the test coverage and CI/CD maturity? Can a single engineer ship to production today without manual gates?"**
- **"What fraction of the codebase would you describe as well-understood by current staff versus legacy that no one fully understands?"**

*What this dimension determines:* The substrate decides which AI moves are even mechanically possible. AI tools work dramatically better on modern, well-tested, well-typed codebases. A 30-person team on a 3-year-old TypeScript monorepo lives in a different world than a 300-person team on a 15-year-old Java/COBOL hybrid.

### 2. Regulatory and risk posture

What can the org actually ship without external review?

- **"What regulatory regimes apply to your code or the data it touches — SOC 2, HIPAA, PCI, SOX, GDPR, sector-specific rules?"**
- **"For a typical change, how many independent reviewers or approvers are required before production? Who are they?"**
- **"What's the cost of a production incident in your domain — measured in dollars, regulatory exposure, or customer trust?"**
- **"Have you had a security or compliance audit in the last year? What did it find about your change-control process?"**

*What this dimension determines:* High regulatory load makes AI-driven throughput dangerous unless the review infrastructure scales with it. Fung's "code wins debates" works because Anthropic ships fast and reviews loosely. A fintech can't simply adopt that — the regulatory floor is the binding constraint, and ignoring it produces audit findings, not velocity.

### 3. Deployment and observability maturity

Can the org safely absorb increased commit volume?

- **"What's your current deployment frequency? Daily, weekly, monthly, quarterly?"**
- **"What's your lead time for changes — from merge to production?"**
- **"What's your change failure rate, and what's your MTTR when something breaks?"**
- **"What's your observability posture? Can an on-call engineer find the cause of a production issue in minutes, hours, or days?"**

*What this dimension determines:* AI compresses authoring time, which makes downstream constraints louder. A team with weekly deploys, manual QA, and shallow observability that adopts aggressive AI assistance will hit its CI pipeline as the new bottleneck within a quarter, and its incident response capability shortly after. The DORA metrics here are the leading indicator of whether the substrate can scale with AI velocity.

### 4. Code review culture and capacity

Who reviews the code now, and what does review actually do?

- **"How is code review structured today? Required reviewers, async, sync, who can approve what?"**
- **"What does code review actually accomplish for your team — bug catching, knowledge distribution, mentorship, security, all of the above?"**
- **"What fraction of your senior engineers' time goes to reviewing others' code? Is that load increasing or decreasing?"**
- **"Have you observed any 'vigilance decrement' — reviewers approving without deep reading because the volume is too high?"**

*What this dimension determines:* The single most underestimated risk in AI-native transformations. AI dramatically increases the volume of code reaching review. If review is doing *bug catching* primarily, AI can take much of that load. If review is doing *knowledge distribution and shared ownership*, AI can't replace it, and removing the review ritual will create knowledge silos that surface during incidents months later.

### 5. Talent profile and pipeline

What does your engineering bench look like today, and where do future seniors come from?

- **"What's the seniority distribution — what fraction junior, mid, senior, staff+?"**
- **"How are juniors learning their craft today? What work do they do that builds judgment?"**
- **"What's your voluntary attrition rate, especially among senior engineers? Has it changed in the last 12 months?"**
- **"Is the org currently hiring? If so, which seniority levels and profiles?"**

*What this dimension determines:* The pipeline question that the published AI-native playbooks consistently dodge. If AI does the work juniors used to do, the org has to deliberately design how juniors build the judgment that becomes senior expertise. Orgs that don't address this are borrowing expertise built in a pre-AI world and not visibly investing in growing more.

### 6. Existing process load

What rituals does the org carry today, and which still serve their purpose?

- **"List your major recurring rituals — standups, planning, retros, design reviews, all-hands, on-call rotations. How long has each been running, and when was each last evaluated?"**
- **"Which rituals do engineers privately dread? Which do they actively value?"**
- **"Has anything been retired in the last 12 months? If not, why not?"**
- **"How are new processes introduced today — bottom-up by teams, top-down by leadership, or both?"**

*What this dimension determines:* Process pruning is the most transferable Fung principle, but it requires cultural permission. An org where rituals accumulate but never retire has a different starting move than one where pruning already happens. The diagnosis here also reveals which specific rituals are candidates for retirement under AI-native conditions.

### 7. Leadership posture and credibility

What is the management layer actually doing, and can it lead this transformation?

- **"How many of your engineering managers were promoted from IC ranks within the company? How many were hired externally as managers?"**
- **"When did your managers last write production code or do meaningful technical work? Could they do so today if asked?"**
- **"What's the leadership team's current personal use of AI coding tools? Daily users, occasional, or none?"**
- **"How does the leadership team learn what's actually happening in the codebase — manager 1:1s, dashboards, dogfooding, or some other mechanism?"**

*What this dimension determines:* Fung's "managers start as ICs" rule is one of her most-cited and least-transferable moves. The principle underneath is real: leadership credibility in an AI-native org depends on visible, current technical engagement, because the work is changing fast and pure-managerial managers will lose the plot within months. But the *implementation* (reverting managers to IC) is calibrated to a context most orgs don't share. The diagnosis here surfaces whether the leadership layer can credibly lead the transformation or whether part of the work is upgrading leadership engagement first.

### 8. Cultural readiness and dissent capacity

How does the org actually handle change, and is the dissent voice strong enough?

- **"When was the last significant cultural change in this org — new tool, new process, new structure? How did it land?"**
- **"Who in the org would be the strongest skeptic of an AI-native rollout, and what would their objections be?"**
- **"Is there a track record of leadership reversing decisions when implementation revealed problems, or is the cultural pattern 'commit and ride it out'?"**
- **"What happens to engineers who push back on AI-assisted workflows today — taken seriously, tolerated, sidelined?"**

*What this dimension determines:* AI-native transformations create real losses for some staff — senior engineers absorbing more review load, engineers whose craft feels commoditized, juniors whose growth path is disrupted. An org without a strong, listened-to dissent voice will discover these losses through attrition data, not in time to course-correct.

## Mode 1: Rapid diagnosis only

This mode runs the eight dimensions, produces a diagnostic report, and stops. Use this when the user explicitly asks for diagnosis only, or when the diagnostic findings are severe enough that operating-model design is premature.

### How to run the diagnosis

Walk each dimension in order. For each, ask the questions, then assign a **readiness rating** for that dimension:

- **Strong foundation** — the org has what's needed for AI-native moves in this dimension to land well
- **Workable** — some gaps, but not blocking; design moves can proceed with named caveats
- **Constrained** — meaningful gaps; some AI-native moves will fail or backfire here without prerequisite work
- **Not ready** — fundamental gaps; AI-native moves in this dimension would be premature or harmful

Be honest with these ratings. The temptation is to grade kindly. Resist it. The value of the diagnosis is in surfacing real constraints, not in flattering the leader.

### The diagnostic report format

```
AI-NATIVE ORG DIAGNOSTIC: [Org name or identifier]
Date: [Date]
Conducted with: [Role of user, e.g., "VP Engineering"]

EXECUTIVE SUMMARY
[Two to three sentences naming the org's overall readiness posture, the dimensions
that are blocking, and the headline risk.]

READINESS BY DIMENSION
1. Team and codebase substrate:         [Rating]  ─  [One-line finding]
2. Regulatory and risk posture:         [Rating]  ─  [One-line finding]
3. Deployment and observability:        [Rating]  ─  [One-line finding]
4. Code review culture and capacity:    [Rating]  ─  [One-line finding]
5. Talent profile and pipeline:         [Rating]  ─  [One-line finding]
6. Existing process load:               [Rating]  ─  [One-line finding]
7. Leadership posture and credibility:  [Rating]  ─  [One-line finding]
8. Cultural readiness and dissent:      [Rating]  ─  [One-line finding]

CRITICAL RISKS
[Three to five named risks the diagnosis surfaced, each with a specific scenario
of how the risk would manifest if the org proceeds without addressing it.
Examples: "Vigilance decrement in security review," "Senior attrition from
review load," "Junior pipeline collapse within 18 months."]

PREREQUISITES BEFORE DESIGN
[For any dimension rated "Not ready" or "Constrained," what specifically must
change before operating-model design is worth attempting.]

RECOMMENDED NEXT MOVE
[Either: "Proceed to full design" (if substrate is workable+) or "Address the
following prerequisites first" (with specific items).]
```

The report should be honest enough that a VP-Eng who is *not* ready can read it and know to do the prerequisite work before designing. A flattering diagnosis is worse than useless.

## Mode 2: Full design (diagnosis + operating-model design)

Run this mode only after Mode 1's diagnosis is complete and the substrate is at least Workable across most dimensions. If the org is Not Ready or Constrained on more than two dimensions, refuse to proceed to design — say so directly and recommend the prerequisite work instead.

The full design has four parts.

### Part A: Principles to commit to

A small set of principles that are universally transferable. State these as commitments the leader is making, not as templates being adopted. The current set, distilled from the practitioner literature and stress-tested against the panel critique:

1. **Process pruning is permanent practice.** Every ritual gets a "why does this still exist?" review on a regular cadence. Permission to retire is explicit.
2. **Prototype over debate.** When a technical disagreement can be settled by generating concrete alternatives, generate them. Reserve high-bandwidth discussion for decisions where prototyping is genuinely too expensive.
3. **Just-in-time planning where capability volatility is high.** Long-horizon roadmaps in fast-moving capability domains are wishful thinking. Plan in shorter cycles and re-plan often.
4. **Measure outcomes, not adoption.** Claude-assisted commit rate, AI tool adoption percentages, and similar metrics are vanity. Track change failure rate, MTTR, lead time for changes, and senior attrition.
5. **Trust calibrated to risk class.** Don't say "trust but verify" — say which classes of work get which level of AI autonomy, and what the verification looks like for each.

These principles travel. They cost the org something (more frequent re-planning, explicit measurement infrastructure, harder review taxonomy), and that cost should be named.

### Part B: Context-specific moves, with tradeoffs

For each move that's actually appropriate to the diagnosed org, output it in this structure:

```
MOVE: [Name of the move, e.g., "Mandate Claude Code adoption across engineering"]
RATIONALE: [Why this move, derived from which diagnostic findings]
WHAT IT COSTS: [The specific tradeoff — what the org loses or strains]
WHAT MUST BE TRUE FIRST: [Prerequisites or sequencing constraints]
HOW TO KNOW IF IT'S WORKING: [Specific leading and lagging indicators]
PANEL OBJECTION TO HOLD IN MIND: [The strongest critique of this move and
whether it applies here]
```

Common moves the skill can recommend, each with its panel objection internalized:

- **Default to AI-assisted authoring across engineering** — costs: review load shifts to seniors; panel objection: vigilance decrement and senior burnout (apply if dimension 4 or 5 is Constrained)
- **Shift to just-in-time planning** — costs: harder coordination across teams; panel objection: roadmap visibility for partners (apply if dimension 6 is Strong)
- **Aggressive process pruning with explicit permission** — costs: temporary loss of some functions the rituals were quietly serving; panel objection: ritual elimination without replacement of the function (apply if dimension 6 is Workable+)
- **Code review taxonomy by risk class** — costs: more upfront design work; panel objection: classification disputes; but this is the move that operationalizes Hochstein's vigilance-decrement concern, so recommend it broadly
- **Flatten org modestly within current scale** — costs: span-of-control strain; panel objection: Fournier's "flat orgs fragment past 60 people"; only recommend if current scale is <60 and dimension 7 is Strong
- **Manager technical engagement requirements** (not necessarily "managers as ICs," but minimum technical activity) — costs: management time tradeoff; panel objection: deskilling management craft; recommend a calibrated version
- **Deliberate junior pipeline investment** — costs: deliberate slowdown of senior throughput to invest in growth; not optional if dimension 5 is anything below Strong; this is the move the published playbooks dodge and the skill should not

Refuse to recommend moves where the diagnosis is Constrained or Not Ready on a prerequisite dimension. Say so directly.

### Part C: Sequencing — what to do when

Translate the moves into three time horizons:

- **Now (next quarter):** the moves that are safe given current substrate and have the highest leverage. Usually includes process pruning, metrics infrastructure, and a code review taxonomy if review capacity is strained.
- **Next (Q2-Q3):** moves that the Now wave makes possible — typically broader AI assistance adoption, just-in-time planning, leadership engagement upgrades.
- **Later (Q4 and beyond):** moves that require both the prior waves to have shown results, plus visible evidence on the outcome metrics. Org structure changes typically belong here.

Sequence is not optional. An org that attempts org-shape changes before establishing the metrics infrastructure has no way to know if the changes are working.

### Part D: Metrics that will tell you if it's working

The non-negotiable section. The user does not get a design without this.

Specify three categories of metrics:

**Outcome metrics** (lagging, the real test):
- Change failure rate (DORA)
- Mean time to restore (DORA)
- Deployment frequency (DORA)
- Lead time for changes (DORA)
- Voluntary attrition, segmented by seniority level
- Incident MTTR, segmented by whether the responder authored the code

**Capability metrics** (leading, signals of build-up):
- Code review taxonomy coverage
- Time-to-onboard new engineers
- Observability coverage of services
- Junior engineer growth indicators (promotion rate, scope expansion, retention)

**Vanity metrics to explicitly NOT optimize for:**
- Claude-assisted commit rate (adoption, not value)
- Lines of code generated (anti-correlated with maintainability)
- Velocity in story points (always gameable; meaningless under AI-assist conditions)

Tell the user explicitly: if the leadership team has been celebrating AI-assisted commit rate as a success metric, that needs to stop. It's a vanity metric and treating it as a success measure will produce vanity behavior.

## Anti-patterns to flag

Watch for these and call them out:

- **"We want to be AI-native like [Anthropic / Shopify / OpenAI]."** The skill's whole job is to push back on this. The diagnosis comes first; the template never comes.
- **"Let's mandate AI everywhere and see what happens."** Mandates without metrics infrastructure produce vanity. Mandates without review taxonomy produce vigilance decrement. Surface both.
- **"Our managers should start as ICs."** Sometimes right, often wrong, depends on dimension 7. If the user is reaching for this move because it sounds good, push back hard.
- **"We'll figure out the metrics later."** No. The metrics infrastructure is the prerequisite, not the polish. A transformation without outcome metrics is a vibe.
- **"AI will solve our hiring problem."** It won't, and treating it as a hiring solution is how junior pipeline collapse starts.

## How to run the skill

**Always ask which mode the user wants first.** Mode 1 (diagnosis only) or Mode 2 (full design). Most users will want Mode 2; offer Mode 1 explicitly if any dimension comes back Not Ready during diagnosis, because design on a broken substrate is malpractice.

**Walk the eight dimensions in order during diagnosis. Do not skip.** Some users will want to skip to the design. Hold the line — without the diagnosis, the design is a template, and templates are what this skill exists to avoid.

**Pressure-test thin answers.** "We have good observability" is not an answer. "We use Datadog and our p95 detection time for service degradations was 12 minutes last quarter" is an answer. The level of specificity tells you whether the rating should be Strong or Workable.

**Be direct about what the org isn't ready for.** A VP-Eng who reads a diagnostic that says "not ready" and respects it will produce a better outcome than one who reads a flattering report and proceeds. The skill earns its keep by being honest, not encouraging.

**Refuse to template.** If at any point the skill catches itself producing moves that don't trace back to specific diagnostic findings, stop and redo. The whole value of the skill is that the design is derived from the diagnosis. A diagnosis-free design is what this skill exists to prevent.

## A closing note for the user

This skill internalizes a specific argument: that the published AI-native playbooks are existence proofs, not templates, and the work of designing an AI-native posture for your specific org is yours to do — not to copy. The skill is here to make that work rigorous, surface the tradeoffs honestly, and produce an artifact you can defend to your CTO, your board, and (most importantly) your engineers. If the diagnosis comes back unflattering, that's the skill working as designed.
