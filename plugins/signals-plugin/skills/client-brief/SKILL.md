---
name: client-brief
description: Generate a client intelligence brief by pulling company data, recent signals, active searches, and talent pool from Notion
user-invocable: true
---

# Client Brief

Generate a comprehensive intelligence brief for a client or prospect company by pulling data across all Notion databases. Designed for call prep, business development, and account reviews.

## Data Sources

| Database | Data Source | What to Pull |
|----------|-----------|--------------|
| Company Core | `collection://f371c4ed-be14-468e-a197-822154951845` | Company profile, client status, therapeutic areas, headcount, last contact |
| Layoffs | `collection://21cf7674-0da8-4812-8708-04b65a252cac` | Recent restructuring events |
| Positive Data | `collection://c5a4112f-cd39-479f-a90f-3165a1ec7a60` | Clinical milestones, data readouts |
| Funding 5-50M | `collection://9490e7cc-0504-4412-85ad-32b2ad7e906e` | Recent smaller funding rounds |
| Funding >=50M | `collection://927267bf-ec5b-4b20-9829-2b9d6371ba23` | Megaround funding |
| Job Alerts | `collection://e83b1888-f65a-486d-bc1f-c0071623f9af` | Open roles, hiring signals |

## Workflow

### Step 1: Find the Company
Search Company Core using `notion-search` for the company name provided by the user.
- Try exact match first, then strip suffixes
- If not found, tell the user and offer to create a Company Core entry

### Step 2: Pull Company Core Data
Fetch the full Company Core page to get:
- Client Status
- Country
- Therapeutic areas
- Headcount band
- Most recent signal type + date
- Last Contact Date
- Last Submission
- ATS Type
- Any notes or content on the page

### Step 3: Pull Related Signals
Search each signal database for the company name:
- Layoffs & Restructuring
- Positive Data & Milestones
- Funding (both 5-50M and >=50M)

Sort by date, most recent first.

### Step 4: Pull Job Alerts
Search Job Alerts for roles linked to this company.
- Note: Job Alerts uses a `Company` relation, so search by company name

### Step 5: Format the Brief

Output this format:

```
## [Company Name] - Client Brief
Generated: [today's date]

### Company Profile
- **Client Status**: [status]
- **Therapeutic Areas**: [areas]
- **Headcount**: [band]
- **Country**: [country]
- **Last Contact**: [date]
- **Last Submission**: [date]
- **ATS**: [type]

### Recent Signals
[List all signals chronologically, most recent first, with type/date/details]

### Active Job Alerts
[List open roles with job family, level, status]

### Talking Points
[Based on the data above, suggest 2-3 specific talking points for a call:
- Reference recent signals as conversation starters
- Note any gaps in engagement (long since last contact)
- Identify potential hiring needs based on signals]
```

## Usage

**User**: `/client-brief Ionis`

Pulls everything across all databases for Ionis and formats the brief.

**User**: `/client-brief Regeneron` (prospect account)

Same format but talking points should focus on business development angle - what signals suggest they need GQR's services.
