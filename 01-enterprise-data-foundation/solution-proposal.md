# Solution Proposal: Trusted Customer and Revenue Data for Brightwell Home & Appliance

> Educational portfolio piece. Brightwell is a fictional company; all figures are invented. This is not a real client proposal and not an official implementation of any vendor's product.

**Label:** Proposed future implementation (design only).

## 1. The problem

Brightwell's customer, sales, warranty and service data sits in seven systems that share no common customer identity or agreed definitions. Leadership gets three different "active customer" counts, Finance spends about four days a month reconciling revenue, Marketing emails customers who already hold a warranty, and support agents open several systems per call (about nine minutes). The board wants an AI assistant, but the data is not yet ready for it.

## 2. What we will deliver

One trusted, secured view of customers, warranties, orders and service history, with agreed business definitions, so that reports match, staff stop duplicating work, and AI can later be built on reliable data.

## 3. How: three phases

- **Phase 1, quick win:** connect only the CRM and the warranty spreadsheets, stop warranty offers reaching customers who already hold a warranty, and add basic access control.
- **Phase 2, extend and agree the numbers:** connect the remaining five systems; deliver one agreed active-customer count, monthly revenue reconciliation and a one-screen customer view for support.
- **Phase 3, govern and prepare for AI:** full masking, audit logging, a data catalogue, an approved metric dictionary and an AI readiness review.

## 4. How we will know it worked

- Phase 1: with 100 test customers, 20 with active warranties, none of the 20 appear on the warranty email list. A new warranty appears in Marketing's list within one hour.
- Phase 2: one agreed active-customer count; a test month with 5 planted revenue differences reports all 5; 95% of customer lookups finish within 3 seconds.
- Phase 3: access tests pass for each role; the AI readiness checklist is complete.
- Business measures to validate with the client: support call time (baseline 9 minutes, target under 5), finance reconciliation effort (4 days, target 1 day or less).

## 5. Technology

Recommended platform: Microsoft Fabric, because Brightwell's team already works in the Microsoft environment. Trade-offs: closer tie to Microsoft, cost depends on capacity size, and the trial is for evaluation only. Confirm with a short proof of concept before committing. Alternatives considered: Snowflake, Databricks, Google BigQuery.

## 6. What we need from Brightwell

- IT access to each source system and a named owner for each dataset.
- Business owners to approve metric definitions (CEO and CFO for active customers and revenue).
- Legal confirmation of privacy and retention requirements.

## 7. Risks and assumptions

- Risk: warranty spreadsheet layout changes without warning. Mitigation: format checks and alerts.
- Risk: matching merges two different people. Mitigation: strict automatic rules, human review for uncertain pairs.
- Assumption: the ERP and POS can be read directly (to confirm).

## 8. Cost and timeline

No price or duration is quoted. Cost drivers are platform capacity and storage, the number of sources connected, the effort to build and test quality and matching rules, and Brightwell's own time for decisions. A range with stated assumptions would be prepared after a discovery workshop and a proof of concept, and checked against the vendor's current price list.

## 9. Next step

Hold a 90-minute discovery workshop with the CIO, Head of Customer Support and Marketing Director, plus a 30-minute session with the CFO, to confirm Phase 1 scope and metric definitions.
