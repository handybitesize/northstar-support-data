# Technical Assessment: The Reusable Ingestion Pattern

Estimated time: 90-120 minutes

## Background

Vesta is acquiring a new Business Unit (BU) that manages customer support in a legacy ticketing environment. Closed support tickets need to be ingested into a central knowledge store to support a new AI Copilot experience.

The BU has changed systems over time, and you have been provided with two exports from that support operation:

- `legacy_support_tickets_dirty.csv`
- `legacy_support_tickets_pre_migration_dirty.csv`

These files are intentionally imperfect and reflect the kind of issues you would expect in a real-world support data export.

## The Task

Build a proof-of-concept ingestion pattern for this scenario.

Your solution should demonstrate how you would take messy support ticket data, shape it into something useful for downstream AI search, and design the pattern so it can be reused as other Business Units are onboarded.

## What The Data Includes

Expect a mixture of:

- inconsistent date formats
- blank or null fields
- HTML in notes or comment fields
- different field names across the two files
- non-closed records mixed in with closed records
- records that should be rejected, flagged, or routed for review

## What Your Solution Should Do

Your proof of concept should:

- ingest the provided sample data
- filter to the relevant closed or resolved support tickets
- clean and transform the content into a structured, AI-ready format
- handle records that fail validation through a human-in-the-loop step or clear error path
- produce simple telemetry or logging to show what happened during processing

## Output

Produce a structured output that could reasonably be sent to an AI search index or used in a retrieval workflow.

At minimum, the output should make it easy to identify:

- a unique document identifier
- a title or subject
- cleaned body text
- normalized dates
- source metadata
- any additional metadata you believe would improve retrieval quality

The exact output format is up to you.

## Reusability

Assume Vesta will need to onboard additional Business Units in future, each with different ticketing systems and export formats.

Your solution should make it clear how this pattern could be extended without starting again from scratch each time.

## Handover Artifact

As part of your handover, please provide:

- the cleaned and transformed output produced by your solution
- a short README or runbook, approximately one page, covering:

- how the source data is configured in your solution
- how to run the ingestion flow
- how you would handle a timeout or partial processing failure
- how you would adapt the pattern for multiple Business Units and multiple source systems

## What We Are Assessing

We are looking for:

- pragmatism
- engineering hygiene
- AI readiness of the final output
- reusability of the approach
- use of AI agent driven development
- clarity of handover and documentation

## Submission

Please provide:

- your implementation
- your transformed output
- your README or runbook

## Notes

- This is a proof-of-concept exercise, not a production build.
- You do not need to introduce additional infrastructure unless you believe it is necessary.
- Clear reasoning and sensible tradeoffs matter more than complexity.
- If you make assumptions, state them clearly.
