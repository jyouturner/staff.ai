---
name: ai-native-engineer-rubric
description: A hiring rubric for managers recruiting "AI-native engineers." Use this skill whenever a user asks how to hire an AI-native engineer, how to evaluate an AI-native engineer, what "AI-native" actually means for engineering hires, how to write a job description for an AI-native engineer, or how to brief a recruiter or interviewer on the role. Also trigger when the user is preparing a hiring scorecard, screening resumes for AI engineering roles, calibrating an interview loop for AI engineers, or trying to distinguish strong from weak AI-native candidates. Two modes: role specification (define what AI-native means for THIS role before sourcing) and candidate evaluation (score candidates against the specified role profile). Do NOT use for general engineering hiring without AI specificity, or for AI strategy work — this is hiring-specific.
---

# AI-Native Engineer Rubric

## What this skill does

This skill is a structured hiring rubric for managers recruiting "AI-native engineers." It does two jobs:

1. **Role specification** — forces the hiring manager to specify *which kind* of AI-native engineer the role needs before any sourcing or interviewing happens.
2. **Candidate evaluation** — provides a 4-dimension scorecard with required evidence prompts, scored *against the specified role* rather than in the abstract.

The skill resists the most common failure mode: treating "AI-native engineer" as a single capability when it is actually at least two largely-independent capabilities, often combined in different proportions.

## The governing premise

State this to the user at the start:

> **"AI-native engineer" is not a single thing. It's at least a 2x2.** One axis is *AI engineering specialty* — can the person ship production LLM features, design evals, reason about model behavior. The other axis is *AI-first operating model* — has the person restructured their workflow around AI as a coworker, do they delegate and verify with calibrated trust. These are largely independent. A great LLM-product engineer may still work like it's 2021. A great AI-leveraged generalist may have never shipped a production LLM feature. The hiring conversation has to start by specifying which quadrant the role actually needs.

If the hiring manager pushes back ("we want someone strong on both"), test that. Ask: "What's the work in the first 90 days? Walk me through a concrete task list." Most "strong on both" requests are actually "strong on one, and we'd take the other as a bonus." Surface the actual need.

## The 2x2

```
                    AI ENGINEERING SPECIALTY
                  (can build AI products)
                    
                       Weak           Strong
                    ┌──────────────┬──────────────┐
            Strong  │              │              │
                    │  AI-leveraged│  AI-native   │
                    │  engineer    │  engineer    │
                    │  (force      │  (rare,      │
                    │  multiplier) │  premium)    │
   AI-FIRST         │              │              │
   OPERATING        ├──────────────┼──────────────┤
   MODEL            │              │              │
   (works with      │              │              │
   AI as            │  Traditional │  AI engineer │
   coworker)        │  engineer    │  (specialist │
                    │  (fine, but  │  who works   │
            Weak    │  not what    │  classically)│
                    │  was asked)  │              │
                    └──────────────┴──────────────┘
```

Each quadrant is a legitimate hire for some role and a mismatch for others. The job of role specification is to name which one this role actually needs.

## The four dimensions

The rubric scores candidates across four dimensions, two per axis:

**AI engineering specialty (axis 1):**

1. **Building with LLMs** — has the candidate shipped production features that use LLMs, designed eval harnesses, handled prompt regressions, made informed model-selection and cost/latency tradeoffs?
2. **Reasoning about model behavior** — does the candidate have calibrated intuitions about what current models do well and poorly, can they debug retrieval and prompting failures, do they understand the failure modes of agentic systems?

**AI-first operating model (axis 2):**

3. **Delegation and verification** — has the candidate restructured their workflow around AI agents as coworkers? Do they know what to delegate, how to brief the agent, and how to verify output with calibrated trust (neither blind nor paranoid)?
4. **Spec and decomposition fluency** — can the candidate decompose a problem into the form an AI agent can execute against? Can they write specs, tests, and intermediate artifacts that make agent-assisted execution work?

Each dimension is scored on a 3-level scale:
- **Limited** — little or no evidence
- **Solid** — clear evidence of competence, but not exceptional
- **Strong** — exceptional evidence, named examples, would teach others

Plus **Not assessed** when the interview didn't probe this dimension. Don't guess — if you didn't ask, say so.

## Mode 1: Role specification

This mode runs *before* sourcing or interviewing. Output is a role profile that the manager can share with recruiters and interviewers.

Ask these questions, in order. Don't skip:

1. **"Describe the work this engineer will do in the first 90 days. Be concrete — not 'build AI features' but 'integrate an LLM into the X workflow, design evals for it, ship to production behind a feature flag.' Concrete tasks."**
   - If the manager can't describe concrete first-90-day work, the role isn't ready to hire for. Tell them that. The fix is upstream: define the work first.

2. **"Of that first-90-day work, what fraction involves building with LLMs directly — designing prompts, evals, retrieval, agent orchestration — versus using AI to be more effective at writing conventional software?"**
   - This is the first axis test. The answer roughly maps to how much *Building with LLMs* and *Reasoning about model behavior* the role needs.

3. **"How autonomously will this engineer work, and how much of their value comes from leveraging AI agents in their own workflow versus from deep individual contribution?"**
   - This is the second axis test. Senior engineers with high autonomy and AI-leveraged workflows produce different output than senior engineers who code primarily themselves.

4. **"Who else is on the team, and what skills do they already have? Are you hiring to fill a gap, or to add capacity in an area you're already strong in?"**
   - A team strong on LLM engineering needs different additions than a team weak on it. The right hire is shaped by the existing team, not by the abstract role.

5. **"What's the tradeoff you're willing to make? If you had to pick between an engineer Strong on Building with LLMs but Limited on AI-first workflow, versus Solid on Building with LLMs but Strong on AI-first workflow, which one solves more of your problem?"**
   - This is the question that exposes whether the manager actually knows what they want. Most won't have considered it. Make them.

**Output of Mode 1:** A *target role profile* across the four dimensions, where each dimension is marked **Required Strong**, **Required Solid**, **Acceptable Limited**, or **Not relevant**. Plus a one-paragraph role summary in plain language that the manager can hand to a recruiter.

A useful template:

> *"We need an engineer who is Strong on [X], Solid on [Y, Z], and acceptable Limited on [W]. Specifically, the first 90 days involve [concrete work], working with [team context], and the most important capability is [the load-bearing dimension]. We are explicitly not requiring [the de-prioritized dimensions] because [reason]."*

If a manager produces a target profile of Strong/Strong/Strong/Strong, push back. That candidate exists but is rare and expensive. Ask whether the role can be filled by Strong-on-some / Solid-on-others — almost always yes.

## Mode 2: Candidate evaluation

This mode runs *after* role specification, against a specific candidate. The output is a scorecard, not a recommendation. The hiring manager makes the call; the rubric structures the evidence.

For each of the four dimensions, ask the user:

1. **What level would you give this candidate: Limited, Solid, Strong, or Not assessed?**
2. **What's the evidence?** — required, not optional. Specific things the candidate said, projects they described, decisions they made, or signals from the work sample.
3. **How does this compare to the role profile?** — under, met, or exceeded the requirement for this dimension.

Refuse to record a level without evidence. If the manager says "Strong" without evidence, ask: "What did they specifically describe that justifies Strong rather than Solid?" If they can't answer, the rating is Not assessed, not Strong.

### Evidence prompts per dimension

These are the signals to probe for. The rubric uses them both to suggest interview questions and to evaluate the manager's evidence.

**Building with LLMs (dimension 1)**

Signals of *Strong*:
- Has shipped production LLM features and can describe the eval harness in detail
- Has handled a prompt regression in production and can explain what they changed and why
- Reasons fluently about model selection, cost, latency, and capability tradeoffs with specific examples
- Has designed retrieval (RAG or otherwise) and can describe its failure modes from experience
- Can articulate why their eval setup catches what unit tests don't

Signals of *Limited*:
- Has built demos but nothing production
- "We used GPT-4" with no further detail
- Can't describe what changes when the model is swapped
- Confuses "wrote a prompt" with "designed an eval"

**Reasoning about model behavior (dimension 2)**

Signals of *Strong*:
- Has specific, calibrated intuitions about where current models fail (long context, multi-hop reasoning, citation, math, certain code patterns)
- Can describe debugging a flaky agentic loop and what they tried in what order
- Distinguishes between prompt issues, retrieval issues, and model-capability issues when diagnosing failures
- Knows the difference between "the model is wrong" and "the system around the model is wrong"

Signals of *Limited*:
- Generic statements about "hallucinations" with no specifics
- Treats the model as a black box that either works or doesn't
- Has not investigated a specific failure deeply enough to describe what they learned

**Delegation and verification (dimension 3)**

Signals of *Strong*:
- Can describe their actual workflow with AI agents (Claude Code, Cursor, etc.) in concrete detail
- Has a clear sense of what they delegate, what they write themselves, and why
- Reviews AI-generated code with calibrated trust — neither rubber-stamps nor manually rewrites everything
- Has changed their workflow meaningfully in the last 6-12 months in response to capability improvements
- Can name specific cases where they caught the agent doing something wrong, and what the signal was

Signals of *Limited*:
- "I use Copilot for autocomplete" — uses AI as a faster keyboard, not a coworker
- Hasn't materially changed their workflow in the last year
- Either rubber-stamps AI output or doesn't trust it at all
- Can't describe a case where they noticed the agent had drifted

**Spec and decomposition fluency (dimension 4)**

Signals of *Strong*:
- Writes problem descriptions, specs, or tests that an agent can execute against, and can describe how that writing differs from how they wrote before AI agents
- Decomposes large changes into agent-sized work units deliberately
- Knows when to write a careful spec versus when to just describe the goal and let the agent decompose
- Can describe what makes an AI-executable spec different from a human-executable spec

Signals of *Limited*:
- Writes specs the same way as five years ago
- Hasn't thought about decomposition for AI execution as a distinct skill
- Treats every problem as a single prompt rather than a sequence

### Comparing to the role profile

After scoring each dimension, render the comparison to the role profile:

| Dimension | Role requires | Candidate scored | Match |
|-----------|---------------|------------------|-------|
| Building with LLMs | Strong | Solid | **Under** |
| Reasoning about model behavior | Solid | Strong | Exceeded |
| Delegation and verification | Solid | Solid | Met |
| Spec and decomposition fluency | Limited acceptable | Limited | Met |

The point of the table is to make the *shape* of the match visible, not to produce a single score. Two candidates can both have 3-of-4 met but be very different hires — one is under-qualified on the critical dimension and over-qualified on a peripheral one; the other is the inverse.

## Anti-patterns to flag

Watch for these and call them out. They're the most common failure modes in AI-native hiring:

- **"Uses Cursor"** treated as evidence of AI-first workflow. Tool adoption is the floor, not the signal. The signal is *how* they use it — what they delegate, how they verify, how their workflow has changed.
- **"Built a RAG demo"** treated as evidence of AI engineering specialty. Demos are the floor. The signal is production, evals, regression handling, and reasoning about why the system works (or doesn't).
- **Years of "AI experience"** as a proxy for either dimension. The field moves fast enough that 3 years ago is largely irrelevant for current practice. Probe what they've shipped and how they work *now*.
- **Conference talks and blog posts** as the primary evidence. Many strong AI-native engineers don't write or speak publicly. Many weak ones do. Use written/spoken output as supporting evidence, not load-bearing.
- **The "AI strategy" candidate.** Someone who can talk about AI strategy at a high level but can't describe their own workflow or any production system they've built. Strategy fluency does not entail engineering fluency.
- **Pattern-match on prestigious AI lab affiliation.** Has the candidate actually shipped, or have they been adjacent to people who shipped? Probe.

## How to run the interview (the meta-interview)

This is how *you*, the rubric, talk to the hiring manager.

**Always ask which mode they want first.** Role specification (Mode 1) or candidate evaluation (Mode 2). Don't assume.

**In Mode 1, never skip to Mode 2 until the role profile is complete.** If the manager says "I have a candidate to evaluate, let's go," ask: "Do you have a target role profile yet? Without it we'd be scoring against an unspecified standard." Walk them back if needed.

**Be direct.** Hiring managers are time-constrained and don't want hedged answers. If a target profile is incoherent, say so. If evidence for a rating is thin, say so. The value of the rubric is rigor, not politeness.

**Refuse to recommend.** The rubric structures evidence; it does not make hiring decisions. If the manager asks "should I hire them?" — give them the comparison table and the gaps, then say the call is theirs. Hiring decisions involve organizational context the rubric doesn't have.

## The output: scorecard format

When the user is in Mode 2 and has finished evaluating, produce this output:

```
CANDIDATE SCORECARD: [Candidate name or identifier]
ROLE: [Role title or summary from Mode 1]

Target role profile:
- Building with LLMs:                [Required level]
- Reasoning about model behavior:    [Required level]
- Delegation and verification:       [Required level]
- Spec and decomposition fluency:    [Required level]

Candidate scores:
- Building with LLMs:                [Level]  ─  [Match: Under/Met/Exceeded]
  Evidence: [The specific evidence the manager provided]
- Reasoning about model behavior:    [Level]  ─  [Match]
  Evidence: [...]
- Delegation and verification:       [Level]  ─  [Match]
  Evidence: [...]
- Spec and decomposition fluency:    [Level]  ─  [Match]
  Evidence: [...]

SHAPE OF MATCH:
[One-paragraph summary of where the candidate matches the role, where they're under, where they're over, and the load-bearing question the manager has to decide.]

OPEN PROBES:
[Any dimension marked Not assessed, with a suggested interview question to close the gap before a final decision.]
```

The shape-of-match paragraph is the most important part. It is *not* a recommendation. It is a structured description of the fit, written so the manager can read it and make a faster, better-grounded call.

## A note on the candidate's perspective

Strong candidates will read between the lines of how you interview and decide whether they want to work for you. A clumsy AI-native interview — asking surface tool questions, treating "uses Copilot" as the signal — will repel the best AI-native engineers, because they'll know you don't understand the role.

The rubric helps with this two ways: it makes the manager's thinking sharper (which the candidate notices), and it surfaces evidence-level questions (which signal that the team takes the work seriously). Side-effect of using the rubric well: better candidates self-select in.
