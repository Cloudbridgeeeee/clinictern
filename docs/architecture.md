# ClinicTern — proposed AWS architecture

ClinicTern uses AWS to de-identify patient feedback first, then classify and analyse it — keeping privacy at the centre of every step.

## Request flow

1. Feedback
2. Amazon S3
3. Comprehend
4. AWS Lambda
5. Bedrock
6. DynamoDB
7. Manager review

## Services

### Amazon Comprehend

**Role:** Detect personal information

Detects names, phone numbers, addresses and record identifiers in feedback text so they can be removed before any analysis or storage.

### Amazon Bedrock

**Role:** Classify themes and summarise

Classifies de-identified comments into service themes and sentiment, and drafts monthly summaries for managers — with guardrails against clinical advice.

### Amazon S3

**Role:** Store de-identified feedback

Holds incoming files briefly for processing and keeps only de-identified feedback for analysis, encrypted at rest.

### Amazon DynamoDB

**Role:** Hold themes, issues and tasks

Stores classified feedback, recurring issues, improvement tasks and review decisions for fast dashboards.

### AWS Lambda

**Role:** Run de-identification and analysis

Orchestrates detection, redaction, classification and aggregation for every new batch of feedback.

## Principles

- **De-identify first** — Personal details are removed before analysis.
- **Administrative only** — No clinical records, no clinical decisions.
- **Aggregate reporting** — Reports show themes, never individuals.

## Safeguards

- **De-identified by default** — Names, contacts and record numbers are removed before analysis.
- **No clinical use** — ClinicTern never processes clinical records or supports diagnosis or treatment.
- **Managers decide** — Themes and summaries are reviewed by managers before action.
- **Aggregate only** — Reports show patterns, never identifiable patients.

## MVP scope

We import several months of patient feedback for one facility, de-identify and classify it, and deliver service dashboards and a monthly report your patient services team reviews.

- Feedback import (paper, SMS, web)
- Automatic de-identification
- Theme and sentiment classification
- Service dashboards
- Monthly service report
