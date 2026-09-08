# RoofLead Rescue

### AI-Powered Roofing Lead Recovery & Follow-Up Automation

RoofLead Rescue is an AI-powered lead recovery system built with **n8n** for residential roofing companies.

It analyzes existing roofing leads, identifies opportunities that may have been lost through delayed or incomplete follow-up, prioritizes them, generates personalized follow-up strategies, and produces a professional recovery report.

The goal is simple:

> **Recover roofing opportunities that would otherwise disappear.**

---

## The Problem

Roofing companies can generate a large number of leads through:

- Websites
- Google Ads
- Facebook
- Referrals
- Google Business
- Other marketing channels

But generating a lead is only the beginning.

Leads can become inactive after:

- An estimate is sent
- An inspection is completed
- A scheduled appointment is missed
- A homeowner asks about financing
- A homeowner stops responding
- A homeowner starts comparing competing quotes

Traditional CRM systems can store these leads, but the business still has to determine:

**Which leads should we contact first, why should we contact them, and what should we say?**

RoofLead Rescue addresses this specific gap.

---

# Solution

RoofLead Rescue turns existing lead data into actionable recovery opportunities.

```text
Existing Roofing Leads
        ↓
Lead Normalization
        ↓
Duplicate Detection
        ↓
AI Lead Analysis
        ↓
Deterministic Lead Scoring
        ↓
Priority Routing
        ↓
AI Follow-Up Strategy
        ↓
Validation & Quality Control
        ↓
Recovery Report
        ↓
PDF Generation
        ↓
Google Drive + Email Delivery. 

Core Capabilities
1. Lead Normalization

Incoming lead records are standardized before analysis.

The workflow cleans fields such as:

Lead name
Phone number
Email
Service
Status
Estimate value
Contact date
Appointment status
Notes

Phone numbers are normalized into an international format for reliable downstream processing.

2. Duplicate Detection

The system checks leads for duplicates using available identifiers such as:

Phone number
Email address
Source row

This prevents the same opportunity from being analyzed multiple times.

3. AI Lead Analysis

Each lead is analyzed individually by an AI analysis engine.

The system evaluates signals such as:

Lead intent
Estimated opportunity value
Recency of contact
Current lead status
Inspection status
Estimate status
Insurance-related signals
Financing interest
Quote comparison
Risk of losing the opportunity
Recoverability

The AI does not determine the final numerical score.

4. Deterministic Lead Scoring

The system combines business rules and AI-derived signals to produce a consistent lead score.

Scoring considers factors including:

Estimated job value
Roof replacement vs. repair
Estimate sent
Inspection completed
Inspection scheduled
No response
Insurance claim
Financing interest
Quote comparison
Days inactive
Recoverability

Each lead receives a score from:

0 → 100

The workflow then assigns a priority:

70–100  → HOT
45–69   → WARM
0–44    → NURTURE

The scoring layer is intentionally deterministic so that the same business rules are applied consistently rather than relying entirely on an AI model.

Priority Routing

Leads are automatically routed into three recovery categories.

🔥 HOT

High-value or high-intent opportunities requiring prompt attention.

Recommended action may include:

Phone call
Email
Immediate follow-up
🟡 WARM

Legitimate opportunities that require timely follow-up but do not necessarily require immediate action.

🔵 NURTURE

Lower-priority opportunities where a lower-pressure strategy is more appropriate.

Leads that are clearly unrecoverable are prevented from receiving active follow-up.

AI Follow-Up Strategy

The system generates a personalized follow-up strategy based on the actual lead context.

It can determine:

Whether follow-up is required
Urgency
Recommended communication channel
Follow-up goal
Email subject
Personalized message
Phone talking points
Reason for the recommendation

The AI is explicitly instructed not to invent:

Discounts
Financing terms
Insurance outcomes
Guarantees
Deadlines
Availability
Company policies
Other unsupported information

This keeps the generated communication grounded in the available lead data.

Quality Control

AI-generated output is passed through a validation layer before being used in the final report.

The validator checks:

JSON validity
Lead identity
Allowed urgency values
Allowed communication channels
Required follow-up messages
Recoverability
Closed-lost protection
Required output fields

This creates a controlled pipeline rather than sending raw AI output directly to the client.

Company Configuration

The workflow supports a separate company configuration layer.

This allows the same system to be adapted for different roofing companies without rebuilding the core lead-analysis logic.

Example configuration:

Company Name
Company Phone
Company Email

The configuration is merged with the lead data before follow-up generation.

Automated Reporting

After all leads are processed, the system generates a consolidated recovery report.

The report includes:

Total leads analyzed
Total estimated opportunity
HOT leads
WARM leads
NURTURE leads
Follow-up requirements
Opportunity breakdown
Top recovery opportunities
Recommended actions
Leads that should not be contacted
Example Result

In the demonstration dataset:

10 leads analyzed

$139,500
Total estimated opportunity

1 HOT lead
6 WARM leads
3 NURTURE leads

9 leads requiring follow-up
1 lead requiring no follow-up

The system identified the highest-priority opportunities and generated specific recommended actions for each.

For example:

David Brown
$27,000 estimated opportunity
HOT
Score: 77
Immediate
Phone + Email

Recommended action:
Clarify questions about the estimate and discuss
next steps for the roof replacement.
Client Report

The workflow automatically generates a professional PDF report containing the recovery analysis.

The report can be:

Saved to Google Drive
Delivered through email
Reviewed by the roofing company's sales team

The report is designed to give the business a clear answer to:

Which leads should we work on first?

Workflow Architecture
┌──────────────────────┐
│   Roofing Lead Data  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│  Lead Normalizer     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Duplicate Detection  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ AI Lead Analyzer     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Lead Scoring Engine  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Priority Router    │
└──────┬───────┬───────┘
       ↓       ↓       ↓
     HOT     WARM    NURTURE
       └───────┬───────┘
               ↓
┌──────────────────────┐
│ Company Configuration│
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ AI Follow-Up Engine  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Follow-Up Validator  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Rescue Results       │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Recovery Report      │
└──────────┬───────────┘
           ↓
     ┌─────┴─────┐
     ↓           ↓
   PDF       Google Drive
     ↓
   Email
Technology Stack
n8n — workflow automation
OpenAI — lead analysis and follow-up strategy generation
Google Sheets — lead data and results
Google Drive — report storage
Gmail — report delivery
HTML/CSS — client report presentation
PDF generation — professional report delivery
Business Value

RoofLead Rescue is not designed to replace a roofing company's CRM.

It focuses on a specific problem:

What happens to the leads that already exist but are no longer being actively followed up?

The system provides a recovery layer around existing lead-management processes.

Potential business outcomes include:

Identifying high-value stalled opportunities
Reducing manual lead review
Prioritizing sales-team attention
Improving follow-up consistency
Providing personalized follow-up recommendations
Giving management a clear recovery report
Designed For

RoofLead Rescue is primarily designed for:

Residential roofing contractors
Roofing sales teams
Roofing companies running paid advertising
Companies receiving website enquiries
Companies with existing lead lists
Businesses with estimates that require follow-up

The system can also be adapted to other high-ticket home-service businesses.

Portfolio Screenshots
Workflow

Recovery Report

Email Delivery

Project Status

Version: V1

Status: Working demonstration / client-ready MVP

Current capabilities include:

Lead ingestion
Normalization
Deduplication
AI analysis
Deterministic scoring
Priority routing
AI follow-up generation
Follow-up validation
Company configuration
Recovery reporting
PDF generation
Google Drive storage
Email delivery
Future Improvements

Potential future versions may include:

CRM integrations
Website lead capture
Missed-call detection
SMS automation
WhatsApp integration
Automated estimate follow-up
Sales-team notifications
Daily recovery alerts
Lead-status synchronization
Recovery performance analytics
Automated follow-up sequences
Security & Workflow Distribution

The production n8n workflow configuration is intentionally not included in this public repository.

This repository demonstrates the system architecture, implementation approach, capabilities, and results without exposing private workflow configuration, credentials, or client-specific information.

Production workflow access can be provided privately where appropriate.

Author

Ogheneochuko Godswill

AI Automation Engineer

Building AI-powered automation systems using:

AI • APIs • Workflows • Automation

Portfolio:
https://godswillai.dev

GitHub:
https://github.com/godswillmamus54-max

Interested in a Similar Automation?

If your business has leads that are being generated but not consistently followed up, RoofLead Rescue can be adapted to your existing workflow.

Contact me to discuss a custom implementation.