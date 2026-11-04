# 11 — Testing, Roadmap and Risks

> Educational portfolio piece. Brightwell Home & Appliance is fictional. Durations are not estimated here; they require discovery and vendor input.

**Label:** Proposed future implementation (design only).

## 1. Acceptance tests

The client signs off a phase when its tests pass. Tests come from the requirements in 02.

- **FR2 (support screen):** for 20 test customers, every item (contact details, orders, warranty status, open tickets) appears on one screen.
- **FR3 (warranty exclusion):** with 100 test customers, 20 with active warranties, none of the 20 appear on the generated email list.
- **FR1 (active customers):** the count matches the agreed definition on a test date.
- **FR5 (revenue reconciliation):** a test month with 5 planted differences reports all 5.
- **NFR1 (speed):** 95% of 50 timed customer searches finish within 3 seconds.
- **NFR2 (privacy):** logged in as a support agent, card numbers are masked and bulk export is blocked.
- **NFR3 (freshness):** a newly entered test warranty is excluded from the next hourly list.
- **Matching tests (07):** C001/C002 stay separate; C003/C004 and C005/C008 merge.

## 2. Roadmap

Principle: each phase delivers something the business can see, using only the sources that phase needs. Connecting everything first delays any visible benefit and raises risk.

### Phase 1: quick win (warranty emails and a first trusted customer view)
- Connect only the CRM and the warranty spreadsheets (hourly).
- Apply the matching rules and quality rules to those two sources.
- Stop warranty offers reaching customers who already hold a warranty (FR3).
- Basic role-based access for the people using this data.
- Why: it fixes a visible pain (Marketing), needs two sources, and proves the approach.

### Phase 2: extend and agree the numbers
- Connect POS, e-commerce, ERP, field service and support tool.
- Build the single "active customers" count (FR1) and the revenue reconciliation (FR5).
- Build the support one-screen customer view (FR2).
- Why: the CEO's and CFO's pains need several sources and agreed definitions.

### Phase 3: govern fully and prepare for AI
- Full masking, audit logging and catalogue (08).
- Metric dictionary approved by owners (09).
- AI readiness review before any assistant is built.

## 3. RAID

### Risks
- Warranty spreadsheet layout changes without warning. Mitigation: format checks and alerts.
- Matching merges two different people. Mitigation: strict automatic rules, human review for uncertain pairs.
- Business teams disagree on metric definitions. Mitigation: named owners approve each definition.

### Assumptions
- The ERP and POS can be read directly (to confirm).
- The e-commerce platform offers an API (stated in the scenario).
- Legal retention periods will be supplied by the client.

### Issues
- None yet (design stage).

### Dependencies
- IT access to each source system.
- A named owner for each dataset and metric.
- Legal confirmation of privacy requirements.
- Platform decision confirmed by a proof of concept (10).
