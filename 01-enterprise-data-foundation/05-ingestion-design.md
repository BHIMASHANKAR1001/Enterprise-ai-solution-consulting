# 05 — Ingestion Design

> Educational portfolio piece. Brightwell Home & Appliance is fictional. Costs are relative (low, medium, high), not quotes. Real pricing is reviewed in milestone 1.10.

**Label:** Proposed future implementation (design only).

## 1. Approach: ELT with batch loads

Load raw copies of source data into the central platform first, then clean and reshape them there (ELT). Reasons: the raw copy is kept for audit and re-processing, and cleaning rules can change without re-fetching data. Exception: any data that must not be stored (for example full card numbers) is removed before loading (ETL step for that field only).

Streaming is not recommended at this stage because no requirement needs sub-minute freshness.

## 2. Ingestion by source

- **Warranty spreadsheets:** file pickup, hourly batch. Reason: NFR3 requires new warranties to reach Marketing within 24 hours, and hourly keeps a wide safety margin. Longer-term option: replace the spreadsheet with a proper application.
- ****E-commerce platform**: API (JSON), hourly batch. No current requirement needs real-time; streaming can be reconsidered if live stock availability or fraud checks are added later..
- **CRM:** nightly file or database read (to confirm).
- **POS and ERP:** database read, nightly (to confirm); revenue reconciliation (FR5) is monthly.
- **Field service app and support tool:** export or API, frequency to confirm.

## 3. Options considered for warranty data

- **A. Nightly batch:** low cost. Meets NFR3 but a same-day buyer could still be emailed.
- **B. Hourly batch (recommended):** low to medium cost. Meets NFR3 comfortably.
- **C. Near real-time:** high cost. Exceeds the requirement; spreadsheets cannot trigger it.
- **D. Replace the spreadsheet with a proper system:** highest cost. Removes the root cause (manual typing errors). Proposed as a later phase.

## 4. Steps in an hourly batch run

1. **Extract:** pick up the latest file or records from the source.
2. **Land raw:** store an untouched copy with a timestamp (Bronze layer, see 06).
3. **Check completeness:** compare row counts and totals with the source; stop and alert if they differ.
4. **Validate:** apply data quality rules (07).
5. **Transform:** clean, standardise and match customers (Silver layer).
6. **Load:** publish trusted tables for reporting and marketing (Gold layer).
7. **Monitor:** log success or failure and alert a named owner on failure.

## 5. Business impact (rationale, to validate)

Excluding customers who already hold a warranty from promotion lists avoids wasted sends and customer annoyance. The size of the benefit is unknown until Finance provides the cost of an unwanted send and the volume sent (discovery question 16). No ROI figure is claimed here.

## 6. Risks

- A failed batch could leave Marketing with stale data. Mitigation: alert on failure and show the data's last refresh time.
- Manual spreadsheet edits can break the file layout. Mitigation: format checks at step 4.
