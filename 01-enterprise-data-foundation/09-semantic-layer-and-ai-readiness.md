# 09 — Semantic Layer and AI Readiness

> Educational portfolio piece. Brightwell Home & Appliance is fictional. Definitions are proposals to be approved by the named owners.

**Label:** Proposed future implementation (design only).

## 1. Purpose

A semantic layer is one agreed dictionary of business metrics on top of the Gold layer. Dashboards, reports and any future AI assistant ask the dictionary instead of calculating numbers their own way. This fixes the problem of leadership receiving different numbers for the same question.

Rule: a metric has exactly one definition. If the business needs a different view, it becomes a separate, clearly named metric.

## 2. Metric cards

### Net Revenue
- **Definition:** money earned from sales after refunds, excluding VAT.
- **Rules:** refunds are subtracted (a refunded sale is not income). VAT is excluded (it is collected for the tax authority). The date used is the **invoice date**, so the figure agrees with the ERP, which Finance treats as the source of truth.
- **Source:** Gold sales table, built from ERP invoices reconciled with POS and e-commerce.
- **Owner:** CFO approves; Finance data team maintains.
- **Related metric:** "Sales by order date" is a separate named metric for the sales team and is never labelled Net Revenue.

### Active Customers
- **Definition:** customers who made a purchase of any Brightwell product, or had a service visit for any Brightwell product, in the last 12 months.
- **Rules:** fully refunded purchases excluded (to confirm with CEO and CFO); the date used is order date or visit date (to confirm).
- **Source:** Gold customer table.
- **Owner:** CEO's office approves; data team maintains.

### Warranty Coverage
- **Definition:** share of active customers who hold a warranty whose end date has not passed.
- **Source:** Gold warranty table.
- **Owner:** Marketing Director.

### Duplicate Customer Rate
- **Definition:** share of customer records that are merged duplicates of another record, measured monthly (target under 1%, NFR5).
- **Owner:** data steward.

### Average Support Call Handling Time
- **Definition:** average minutes from call start to ticket resolution.
- **Baseline:** 9 minutes (fictional). **Target (assumption):** under 5 minutes.
- **Owner:** Head of Customer Support.

## 3. AI readiness checklist

- **Correct:** quality rules in 07 pass. Status: designed, not yet implemented.
- **Connected:** one customer ID across systems (matching rules in 07). Status: designed, tested by hand on sample data.
- **Defined:** metrics agreed in this document. Status: proposed, owners to approve.
- **Governed:** role-based access and masking (08). Status: designed.
- **Fresh and documented:** hourly warranty refresh, catalogue entry for every table. Status: designed.

Conclusion for the client: the data is not yet ready for an AI assistant. Build the foundation first; an assistant on top of inconsistent data would give confident but wrong answers. This sets up Project 2.
