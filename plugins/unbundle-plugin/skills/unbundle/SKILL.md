---
name: unbundle
description: Use when the user wants to operationalize a "bundled" term — a soft skill (charisma, executive presence, active listening), a fuzzy workflow (client onboarding, content batch, weekly review), or an identity/belief (strategic, disciplined, curious) — into concrete, trainable, daily actions. Trigger phrases include "unbundle this", "operationalize", "what does X actually mean", "how do I actually become more Y", "break this workflow into steps", "what does a [role] actually do daily", "turn this into a checklist", "I keep hearing be more X but don't know what to do". Walks the user through a three-track interview (Workflow / Soft Skill / Belief) using AskUserQuestion, then returns 5-12 daily-trainable actions with optional micro-routines.
---

# Unbundle

A **bundled term** is one that houses connotative, intangible meaning that's hard
to train and hard to act on. "Charisma." "Leadership." "Strategic thinking."
"Build in public." "Be more disciplined." The phrases imply behavior but don't
describe it.

**Unbundling** turns a bundled term into a set of trainable, learnable, *visible*
actions that — when mastered — encompass the real meaning of the term. The user
walks away with things to *do*, not feelings to *have*.

## When to invoke

Trigger this skill when the user:
- Names a vague quality they want to develop ("I want to be more present in meetings")
- Reads a piece of advice they can't act on ("everyone says go niche but what do I actually do")
- Wants to turn a fuzzy workflow into a step-by-step procedure
- Wants to define what someone in a role/identity *actually does* day-to-day
- Says "unbundle", "operationalize", "turn this into a checklist"

## How to run the skill

### Step 1 — Confirm the term

If the user hasn't already named one explicitly, ask:

> "What's the bundled term, workflow, or identity you want to unbundle?"

Single short reply. Don't pile on context-gathering questions yet.

### Step 2 — Pick a track (AskUserQuestion)

Three tracks exist because the same prompt produces different shapes of output
depending on the target. Use `AskUserQuestion` to let the user choose:

```
Question: "Which track fits what you're unbundling?"
Header:   "Track"
Options:
  - "Workflow — a fuzzy process I want step-by-step"
    description: For things like client onboarding, content batching, weekly review,
                 incident response. Output = a numbered SOP with no skipped steps.
  - "Soft Skill — a quality I want others to feel from me"
    description: For things like charisma, presence, executive presence, active
                 listening, gravitas. Output = observable behaviors bound to contexts.
  - "Belief / Identity — a trait I want to install in myself"
    description: For things like "strategic", "disciplined", "curious", "high-agency".
                 Output = daily practices on a one-week schedule.
```

### Step 3 — Gather track-specific context (AskUserQuestion or quick reply)

One or two short questions, *specific to the track*:

**WORKFLOW**
1. "What's the *input* (what you start with) and the *output* (what counts as done)?"
2. "Where does this currently break down or get skipped?"

**SOFT SKILL**
1. "Who's the person you want to feel this from you? In what context (sales call, team meeting, dinner party)?"
2. "What's one moment you've seen someone embody this *well*?"

**BELIEF / IDENTITY**
1. "What does someone who already has this trait *do* on a Tuesday morning?"
2. "How will you know in 30 days whether you've installed it?"

### Step 4 — Apply the seed prompt

The seed prompt is at `references/seed-prompt.md` — read it. Run it with the
TERM filled in and **track-specific framing** appended:

- WORKFLOW: "Output a numbered SOP. Every prerequisite is its own step. No steps skipped."
- SOFT SKILL: "Output observable behaviors (gestures, words, silences, pacing) bound to contexts. Never internal states."
- BELIEF: "Output daily practices with frequency (daily / 3×week / weekly) and duration (≤15 min). Arrange as a one-week schedule."

### Step 5 — Return the actions

5–12 items. Cut to the highest-leverage. For each item include:
- The action (concrete verb, observable)
- *What good looks like* (one sentence)
- *Where to do it* (specific context, not "everywhere")

### Step 6 — Offer a micro-routine

After the list, ask:

> "Want me to expand any of these into a daily micro-routine (when, how long, what to track)?"

If yes, return: trigger ("right after morning coffee"), action ("write down the
three things I want this meeting to produce"), duration ("90 seconds"), tracking
("⃝ tally in journal").

## The core principle

A bundled term houses connotative and intangible meaning. **Operationalizing** is
the work of translating it into trainable, learnable, visible actions —
actions the user can take *without first feeling the emotion that would
naturally cause the behavior*.

The reference example, **Charisma**, decomposes into: eye contact for one full
beat, speaking 15% slower, asking one question about the other person before
mentioning yourself, repeating a phrase they used, smiling genuinely on greeting
*and* goodbye, weight on both feet, collaborative framing ("let's figure this
out together").

Anyone can do those without feeling charismatic first. That's the whole point.

## Anti-patterns

- ❌ **Returning abstract advice** ("be more present", "communicate clearly").
  If you catch yourself doing this, re-run with the seed prompt and the
  track-specific framing.
- ❌ **Items that require feeling an emotion first** ("when you feel confident,
  speak up"). The skill exists to *bypass* the emotion-first chain.
- ❌ **More than 12 actions.** Long lists feel rigorous but produce no action.
  Cut to the highest-leverage 5–12.
- ❌ **Acting before picking a track.** The tracks materially change what good
  output looks like.
- ❌ **Skipping Step 3.** Without context, the actions default to generic.

## Track rules (canonical)

### WORKFLOW
- No steps skipped. Every prerequisite is its own step.
- Each step has a clear input and output.
- Failure modes belong on the step they apply to, not in a separate appendix.
- Output = a numbered SOP.

### SOFT SKILL
- Behaviors are *physical and observable* — gestures, words, silences, pacing.
- Each behavior is bound to a context (when to do it).
- Output includes one rehearsal exercise per behavior.

### BELIEF / IDENTITY
- Identity-level traits decompose into *daily practices*, not annual goals.
- Each practice has a frequency and a duration (≤15 min).
- Output = a one-week schedule.

## Closing the loop

If the user is going to actually do this, end with:

> "Pick one action. Do it today. Reply tomorrow and tell me what happened."

The skill is wasted if the actions sit in a doc. The micro-commitment is the
delivery vehicle.
