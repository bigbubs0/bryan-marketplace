# The Unbundle seed prompt (canonical)

This is the verbatim prompt that the `/unbundle` skill is built around.
It also ships as a click-to-copy asset on the `/unbundle/thanks` delivery page
so users can paste it into any LLM (Claude, ChatGPT, Gemini) without installing
the skill.

When the skill needs to translate a bundled term, it should run this prompt
internally with `TERM` filled in, then layer the track-specific framing from
SKILL.md on top.

---

```
XYZ is a "bundled" term. Assume it houses a lot of connotative and intangible
meaning that is hard to train and understand. Your mission is to "Unbundle"
and operationalize this term.

Operationalizing means to turn the phrase or word into a set of trainable
and learnable and visible actions that when mastered, encompass the real
meaning of the term.

For example: "Charisma" is a bundled term that stands for the feeling of
warmth, power, and presence other people feel when they interact with you.
The actions that it encircles include making eye contact, active listening,
speaking slowly, asking questions about the other person, smiling genuinely,
having a firm handshake, and setting a collaborative frame for the
conversation, etc.

Provide CONCRETE examples for daily activities in work or life, business or
relationships, interpersonal or mindset, in a way that someone could take
action on without necessarily feeling the emotion that might naturally lead
to the behavior.

TERM:
```

---

## Track-specific framing (append after TERM)

When using this skill (rather than the raw prompt), add the appropriate
framing for the selected track:

### Workflow
> Output a numbered SOP. Every prerequisite is its own step.
> No steps skipped. Each step lists its input and output.
> Failure modes attach to the step they apply to.

### Soft Skill
> Output observable behaviors (gestures, words, silences, pacing) bound
> to specific contexts. Never internal states. Each behavior includes
> one rehearsal exercise.

### Belief / Identity
> Output daily practices with frequency (daily / 3×week / weekly) and
> duration (≤15 min each). Arrange as a one-week schedule.
