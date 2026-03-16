---
name: outreach
description: Generate personalized outreach emails using Notion intel and Voice DNA profiles. Accepts company/person name + outreach type (client-bd, candidate-approach, follow-up, intro).
disable-model-invocation: true
---

# Outreach Email Generator

Generate ready-to-send outreach emails personalized with Notion intelligence and Bryan's Voice DNA profiles.

## Usage

`/outreach [target] [type]`

Examples:
- `/outreach Regeneron client-bd` - BD outreach to a prospect
- `/outreach John Smith candidate-approach for Aditum CMO` - Candidate sourcing email
- `/outreach Sarah Chen follow-up after interview at IDEAYA` - Post-interview follow-up
- `/outreach Ionis intro new VP Clinical candidate` - Client intro of a candidate

## Outreach Types

| Type | Voice DNA Profile | Purpose |
|------|------------------|---------|
| `client-bd` | Client-facing: professional, consultative, data-driven | New business development |
| `candidate-approach` | Candidate advancement: direct, CLABVISSS control | Source/approach a candidate |
| `candidate-coach` | Candidate coaching: supportive, preparation-focused | Interview prep, offer guidance |
| `follow-up` | Context-dependent | Post-meeting or post-interview |
| `intro` | Client-facing: fact-forward, structured | Introduce a candidate to a client |

## Workflow

### Step 1: Gather Intel
Based on the target:
- **Company target**: Search Company Core (`collection://f371c4ed-be14-468e-a197-822154951845`) for company data
- **Pull recent signals**: Check Positive Data, Funding, and Layoffs databases for the company
- **Check Job Alerts**: Look for open roles at the company (`collection://e83b1888-f65a-486d-bc1f-c0071623f9af`)
- **Person target**: If a specific person is named, note their context (candidate, client contact)

### Step 2: Select Voice Profile
Apply the correct Voice DNA based on outreach type:
- **Client-facing**: Professional, consultative, question-oriented. Use "intelligence-driven search", "the data tells us..."
- **Candidate advancement**: Direct, CLABVISSS control language. Focus on opportunity, not selling.
- **Candidate coaching**: Supportive but honest, preparation-focused
- **Transactional**: Efficient, structured, fact-forward

### Step 3: Personalize with Signals
Weave relevant signals into the email as conversation hooks:
- Recent funding = growth signal, hiring likely
- Positive clinical data = pipeline advancing, team scaling
- Layoffs at competitors = talent availability angle
- Open roles on Job Alerts = direct relevance

### Step 4: Draft Email

**Formatting rules (mandatory):**
- Greeting: `Hi [Name],`
- Use hyphens (-) never em dashes
- Use 'CV' not 'resume'
- Use 'Search Consultant' never 'recruiter'
- Keep it scannable - no fluff, no corporate jargon
- Casual, conversational, likable tone
- 150 words max for initial outreach, 100 words max for follow-ups

**Structure for client-bd:**
1. Signal-based hook (1 sentence referencing something specific)
2. Value prop (1-2 sentences on what GQR brings)
3. Soft ask (question, not demand)

**Structure for candidate-approach:**
1. Why them specifically (1 sentence)
2. The opportunity (2-3 sentences, highlight what matters to candidates)
3. Next step (direct ask for a call)

**Structure for intro:**
1. Candidate headline (name, current role, key differentiator)
2. Why this candidate for this role (2-3 bullets)
3. CV attached note

### Step 5: Output
Present the email ready to copy/paste. Include:
- Subject line
- Email body
- Any signals used as context (for Bryan's reference, not in the email)

## Anti-Patterns (avoid these)
- Don't use "I hope this finds you well" or any variant
- Don't use "touching base" or "circling back"
- Don't over-explain GQR - let the intel speak
- Don't write more than 3 paragraphs for any outreach type
- Don't use buzzwords: synergy, leverage, robust, streamline, holistic
