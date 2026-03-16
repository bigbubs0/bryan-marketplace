---
name: weekly-signals
description: Generate a weekly digest of all signals logged to Notion across funding, layoffs, and positive data databases. Defaults to past 7 days. Accepts custom timeframe.
disable-model-invocation: true
---

# Weekly Signal Digest

Generate a scannable digest of all biotech signals logged to Notion. Defaults to the past 7 days.

## Usage

- `/weekly-signals` - Past 7 days
- `/weekly-signals last 14 days` - Custom timeframe
- `/weekly-signals January 2026` - Specific month

## Database Sources

| Signal Type | Data Source |
|-------------|-----------|
| Funding $5-50M | `collection://9490e7cc-0504-4412-85ad-32b2ad7e906e` |
| Funding >=50M | `collection://927267bf-ec5b-4b20-9829-2b9d6371ba23` |
| Layoffs & Restructuring | `collection://21cf7674-0da8-4812-8708-04b65a252cac` |
| Positive Data & Milestones | `collection://c5a4112f-cd39-479f-a90f-3165a1ec7a60` |

Company Core: `collection://f371c4ed-be14-468e-a197-822154951845`

## Workflow

### Step 1: Determine Timeframe
Parse $ARGUMENTS for a custom timeframe. Default to past 7 days from today's date.

### Step 2: Query Each Signal Database
For each of the 4 signal databases, use `notion-search` or query the data source for entries created within the timeframe. Pull all entries.

### Step 3: Cross-Reference Company Core
For each signal, check if the company exists in Company Core and note:
- Client Status (is this an active client, prospect, or unknown?)
- Whether they're in the Active Accounts list (Ionis, Aditum, Xellar, IDEAYA, Structure/Wave, Karyopharm, Regeneron)

### Step 4: Format Digest

```
## Signal Digest: [date range]
Generated: [today]

### Funding Rounds ([count])
| Company | Amount | Round | Date | Client Status |
|---------|--------|-------|------|--------------|
[entries sorted by date, most recent first]

### Positive Data & Milestones ([count])
| Company | Readout | Outcome | Therapeutic Area | Date | Client Status |
|---------|---------|---------|-----------------|------|--------------|
[entries sorted by date]

### Layoffs & Restructuring ([count])
| Company | Event Type | Scale | Reason | Date | Client Status |
|---------|-----------|-------|--------|------|--------------|
[entries sorted by date]

### BD Opportunities
[Flag any signals that suggest immediate business development action:]
- Companies with recent funding AND no client status = new prospect
- Companies with positive data AND active client status = check-in opportunity
- Competitors of active clients with layoffs = talent sourcing opportunity
- Any signals involving Active Accounts = flag for immediate attention

### Stats
- Total signals: [count]
- By type: Funding [n] | Positive Data [n] | Layoffs [n]
- Active account signals: [list any]
```

### Step 5: Highlight Action Items
At the end, list 2-3 specific actions Bryan should take based on the signals:
- Companies to reach out to
- Accounts to check in with
- Talent pools to tap (from layoff signals)

## Notes
- If no signals found for a category, say "None logged this period"
- Keep the digest scannable - tables over paragraphs
- Bold any Active Account company names
