# RoofLead Rescue — Case Study

## Overview

RoofLead Rescue is an AI-powered lead recovery and follow-up automation system designed for residential roofing companies.

The system focuses on an important gap in the sales process:

> Roofing companies may already have valuable leads in their database, but some opportunities become inactive because follow-up is delayed, inconsistent, or difficult to prioritize.

RoofLead Rescue analyzes those existing leads and identifies which opportunities deserve attention first.

---

## Business Problem

A roofing company can receive leads from multiple sources:

- Website enquiries
- Google Ads
- Facebook
- Referrals
- Google Business
- Other marketing channels

The challenge begins after the lead enters the system.

Some homeowners:

- Stop responding
- Receive an estimate but do not reply
- Complete an inspection but do not move forward
- Miss scheduled appointments
- Ask about financing
- Compare multiple roofing estimates

Without a structured recovery process, valuable opportunities can become forgotten.

The sales team may have hundreds of records but no simple way to determine:

1. Which leads are most valuable?
2. Which leads show the strongest buying signals?
3. Which leads should be contacted first?
4. What should the sales team say?
5. Which leads should not be contacted?

RoofLead Rescue was designed around these questions.

---

# Solution

RoofLead Rescue creates an automated lead-recovery pipeline.

```text
Lead Data
   ↓
Normalization
   ↓
Duplicate Detection
   ↓
AI Lead Analysis
   ↓
Deterministic Scoring
   ↓
Priority Routing
   ↓
Company Configuration
   ↓
AI Follow-Up Strategy
   ↓
Validation
   ↓
Recovery Results
   ↓
Client Report
   ↓
PDF
   ↓
Email Delivery

The workflow combines deterministic business logic with AI reasoning.

AI is used where contextual interpretation is valuable, while deterministic logic handles scoring and validation where consistency is important.

Lead Analysis

Each lead is analyzed for business signals including:

Lead intent
Estimated opportunity value
Contact recency
Current status
Inspection status
Estimate status
Buying signals
Risk signals
Recoverability

The analysis engine is instructed not to invent information.

For example, it does not assume:

Insurance approval
Financing terms
Discounts
Deadlines
Guarantees
Company policies
Availability

This keeps the output grounded in the information provided by the business.

Deterministic Scoring

The AI analysis is followed by a deterministic scoring engine.

The scoring engine evaluates factors such as:

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

The result is a score between:

0–100

The system then assigns a priority:

70–100 → HOT
45–69  → WARM
0–44   → NURTURE

This separation between AI analysis and deterministic scoring makes the workflow easier to control and calibrate.

Priority Routing

The scoring engine routes each lead into a recovery category.

HOT

High-priority opportunities requiring prompt attention.

Typical actions may include:

Phone call
Email
Immediate follow-up
WARM

Potentially valuable opportunities requiring timely follow-up.

NURTURE

Lower-priority opportunities where a lower-pressure approach is more appropriate.

The workflow also protects against unnecessary outreach.

If a lead is explicitly marked as unrecoverable or the homeowner has already chosen another contractor, the system can prevent active follow-up.

AI Follow-Up Generation

The follow-up engine receives the complete scored lead context.

It determines:

Whether follow-up is required
Urgency
Communication channel
Follow-up objective
Personalized message
Phone talking points
Reason for the recommendation

The strategy changes depending on the situation.

For example:

Estimate sent + no response

The system focuses the message on helping the homeowner understand the estimate and answering questions.

Missed appointment

The system focuses on reconnecting and rescheduling rather than immediately pushing a sales message.

Financing inquiry

The system acknowledges the financing question without inventing financing terms.

Comparing quotes

The system helps the sales team approach the conversation around scope, questions, and proposal differences without disparaging competitors.

Quality Control

AI output is not sent directly to the final report.

A validation layer checks the generated response before it continues through the workflow.

Validation includes:

JSON parsing
Lead identity verification
Allowed urgency values
Allowed communication channels
Required message validation
Recoverability protection
Closed-lost protection
Output structure

This provides an additional control layer between the AI model and business-facing output.

Company Configuration

The workflow separates company identity from the core lead-analysis process.

The company configuration contains information such as:

Company Name
Company Phone
Company Email

This allows the same automation architecture to be adapted for different roofing companies.

For example:

Company A
   ↓
Same Lead Recovery Engine

Company B
   ↓
Same Lead Recovery Engine

Company C
   ↓
Same Lead Recovery Engine

Only the company-specific configuration changes.

Demonstration Results

The demonstration dataset contained:

10 leads analyzed

The system identified:

1 HOT
6 WARM
3 NURTURE

The combined estimated opportunity was:

$139,500

The system identified:

9 leads requiring follow-up
1 lead requiring no follow-up

The highest-value opportunity identified in the demonstration was:

David Brown
$27,000 estimated opportunity
HOT
Score: 77
Immediate
Phone + Email

The system generated a personalized recovery strategy rather than simply labeling the lead.

Automated Client Report

After processing the leads, the workflow creates a client-facing recovery report.

The report includes:

Total leads analyzed
Estimated opportunity
Priority breakdown
HOT opportunity
WARM opportunity
NURTURE opportunity
Top recovery opportunities
Recommended actions
Suggested follow-up messages
Leads requiring no follow-up

The report is converted to PDF and stored in Google Drive.

A summary email is then sent with access to the report.

Example Follow-Up

For a stalled estimate, the system can generate a message such as:

Hi David, I wanted to follow up regarding the roof replacement estimate we sent after your inspection. If you have any questions or would like to discuss the details or next steps, please feel free to reach out. We're here to help make the process as smooth as possible.

The message is based on the supplied lead information rather than a generic template.

Architecture Decisions
AI + Deterministic Logic

AI is used for:

Understanding context
Identifying buying signals
Identifying risk signals
Generating personalized communication

Deterministic code is used for:

Scoring
Thresholds
Validation
Data preservation
Closed-lost protection
Report calculations

This reduces the risk of allowing an AI model to control every part of the workflow.

Validation Before Delivery

The workflow validates AI-generated output before allowing it into the final reporting pipeline.

This provides a safety layer for business-facing automation.

Separate Reporting Layer

Lead processing and reporting are separated.

The processing pipeline creates validated lead records.

The reporting pipeline then aggregates those records into a client-facing report.

This makes the architecture easier to extend.

Technology Stack
Technology	Purpose
n8n	Workflow orchestration
OpenAI	AI lead analysis and follow-up generation
Google Sheets	Lead input and results
Google Drive	Report storage
Gmail	Report delivery
HTML/CSS	Report presentation
PDF generation	Client report delivery
Potential Business Applications

Although the first implementation targets residential roofing companies, the underlying architecture can be adapted to other high-ticket service businesses.

Potential applications include:

Roofing
Remodeling
HVAC
Solar
Plumbing
Landscaping
Windows and doors
Other home-service businesses

The core idea remains the same:

Identify valuable opportunities that are no longer receiving appropriate follow-up.

Future Development

Potential future versions could add:

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

These features are intentionally outside the initial MVP.

The V1 focus is proving the core business value before adding additional complexity.

Project Outcome

RoofLead Rescue demonstrates how an automation workflow can combine:

AI reasoning + deterministic business logic + validation + reporting + communication

into a practical business automation system.

The objective is not simply to automate data processing.

The objective is to turn existing lead data into:

clear priorities → actionable follow-up → measurable sales opportunities.

Author

Ogheneochuko Godswill

AI Automation Engineer

AI • APIs • Workflows • Automation

Portfolio: https://godswillai.dev

GitHub: https://github.com/godswillmamus54-max