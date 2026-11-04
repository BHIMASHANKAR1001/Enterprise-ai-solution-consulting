# 10 — Technology Options and Trade-offs

> Educational portfolio piece. Brightwell Home & Appliance is fictional. Vendor information comes from vendors' own documentation (checked November 2026) and describes plan terms, not independently verified performance. No prices are quoted; real prices must be confirmed on each vendor's current price list.

**Label:** Proposed future implementation (design only).

## 1. What is being chosen

A hosted online platform where Brightwell stores its data in Bronze, Silver and Gold layers and runs reports on it (a "lakehouse", see 06). All four options below can do this basic job.

## 2. Evaluation criteria (proposed, to confirm with the client)

Brightwell profile: mid-sized UK retailer, small IT team, Microsoft Office in daily use, holds customers' personal data.

Proposed priority order:
1. **Security and privacy:** personal data must be protected (08).
2. **Skills and ease of use:** the small team must be able to run it.
3. **Ecosystem fit:** works with the Microsoft tools already in use.
4. **Cost:** run cost must be predictable.
5. **Fit for requirements:** hourly batch loads, role-based access, masking.
6. **Lock-in:** how hard it is to switch later.

Ranking is confirmed with the client in discovery, because trade-offs force choices.

## 3. Options

- **Microsoft Fabric:** 60-day trial for evaluation, not production; trial limits include 1 TB of OneLake storage. Fits an organisation already using Microsoft 365 and Power BI. Source: Microsoft Learn Fabric trial page.
- **Databricks:** Free Edition is for non-commercial use only, with usage quotas, so it suits learning and not a real client. Source: Databricks documentation.
- **Snowflake:** 30-day trial, no credit card needed to sign up; the account is suspended when the trial ends unless upgraded. Source: Snowflake documentation.
- **Google BigQuery:** free sandbox with no billing account; 10 GiB storage cap, 1 TiB of queries per month, tables expire after 60 days, and no streaming or DML statements. Source: Google Cloud documentation.

## 4. Recommendation

**Microsoft Fabric**, mainly because Brightwell's team already works in the Microsoft environment (ecosystem fit and skills).

### Trade-offs to tell the client

- **Closer tie to Microsoft** (lock-in).
- **Cost depends on capacity size**, so usage must be monitored.
- **Trial is for evaluation only**; production needs a paid capacity.
- The client's technical team should confirm fit with a short proof of concept before committing.

## 5. Architecture decision record (summary)

- **Decision:** use Microsoft Fabric for the data foundation.
- **Context:** Microsoft-centred client, small IT team, personal data.
- **Alternatives considered:** Snowflake, Databricks, BigQuery.
- **Consequences:** faster adoption by existing staff; stronger dependence on Microsoft; capacity costs to manage.
- **Status:** proposed, subject to a proof of concept and confirmation by the client's technical lead.

## 6. Open questions

- Does Brightwell already hold Microsoft cloud agreements or licences?
- Are there data residency requirements (for example UK or EU hosting)?
- Who will run the platform day to day?
