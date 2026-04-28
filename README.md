# DropMeds Lead Generation Pipeline
### Automated lead qualification, scoring & outreach — powered by n8n

---

## What This Does
This workflow automatically captures leads from a Google Sheet, verifies
each email via Kickbox, scores and tiers every lead, sends personalised
outreach emails, alerts the sales team on Slack, logs all activity to
Google Sheets, and saves every lead to Airtable CRM — fully automated,
24/7.

---

## Workflow Architecture
Manual Trigger / Schedule (8am daily)
  → Google Sheets (Read Leads)
    → Set (Normalise Fields)
      → IF (Email Present?)
        → Kickbox API (Verify Email)
          → Set (Enrich + Score Lead)
            → IF (Hot Lead ≥ 60?)
              ├── TRUE  → Airtable CRM + Gmail Outreach + Slack Alert + Activity Log
              └── FALSE → Airtable CRM + Wait 3 Days + Gmail Nurture + Activity Log

---

## Integrations
| Tool | Purpose |
|---|---|
| Google Sheets | Lead source + activity logging |
| Kickbox API | Email verification |
| Airtable | CRM record creation |
| Gmail | Automated outreach emails |
| Slack | Real-time sales team alerts |

---

## Scoring Logic
| Signal | Points |
|---|---|
| Source: Referral | +30 |
| Source: Google Ads | +25 |
| Source: Organic | +20 |
| Email verified (Kickbox) | +25 |
| Company name present | +15 |
| Phone number present | +10 |

**Tiers:** A-Hot (80–100) · B-Warm (60–79) · C-Cold (40–59) · D-Disqualify (<40)

---

## Setup Instructions
1. Import `DropMeds_LeadGen_v3.json` into your n8n instance
2. Connect credentials: Google Sheets OAuth2, Gmail OAuth2, Airtable Token, Slack OAuth2
3. Update your Google Sheet ID and Sheet name in the Read Leads node
4. Update your Airtable Base ID and Table ID
5. Replace Calendly link and sender details in both Gmail nodes
6. Add your Kickbox API key in the HTTP node
7. Click **Active** to go live

---

## Required Credentials
- Google Sheets OAuth2
- Gmail OAuth2
- Airtable Personal Access Token
- Slack OAuth2
- Kickbox API Key

---

## Built By
**Promise** — CEO, DropMeds  
For enquiries: https://calendly.com/sundaepromix/30min
