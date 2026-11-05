# 12 — Industry Variations

> Educational portfolio piece. Content reflects general industry practice, not a verified compliance review. Regulatory points must be confirmed with a compliance specialist in a real engagement.

**Label:** Proposed future implementation (design only).

## 1. What stays the same in every industry

One identity per person or thing, agreed metric definitions, Bronze, Silver and Gold layers, data quality checks, controlled access, and phased delivery.

## 2. What changes: five questions to ask in any industry

1. What does the data look like?
2. Which systems must it connect to?
3. What business rules apply?
4. Which regulations apply?
5. How is success measured?

The deeper rule: the design stays the same, and what changes is how costly a mistake is. That sets how strict the rules, human review and logging must be.

## 3. Retail (the Brightwell baseline)

- **Data:** products, stock, orders, promotions, loyalty.
- **Integrations:** POS, website, ERP, CRM.
- **Business rules:** returns, refunds, promotions, stock levels, warranty status.
- **Regulation:** consumer privacy law (for example UK GDPR); card payment security rules (PCI DSS).
- **Success measures:** accurate stock, campaign return on investment, call handling time.
- **Cost of a wrong merge:** a wrong marketing email.

## 4. Banking

- **Data:** accounts, transactions, loans, cards; very high volumes with long, strict history.
- **Integrations:** core banking systems, payment systems, card networks, fraud monitoring tools.
- **Business rules:** identity verification of customers, detection of suspicious transactions, credit risk rules.
- **Regulation:** anti-money-laundering and know-your-customer rules, regulatory reporting, strict audit requirements.
- **Success measures:** reporting accuracy and timeliness, risk and fraud reduction, audit results.
- **What stays the same:** layered design, one customer identity, quality rules.
- **What changes:** complete audit trails for every change, exact (not approximate) reconciliation of totals, and identity matching tied to verified identity checks rather than email alone.
- **Why:** an error can mean wrong regulatory reports, missed suspicious activity or financial loss, so reconciliation and traceability must be exact and provable.
- **Cost of a wrong merge:** one customer's account activity attributed to another, which is a serious compliance and financial risk.

## 5. Healthcare

- **Data:** patient records, appointments, lab results, clinical notes (much of it free text).
- **Integrations:** hospital record systems, labs, billing; standard health data formats such as HL7 and FHIR.
- **Business rules:** matching the right patient to the right record, consent, who may view clinical data.
- **Regulation:** health privacy law (for example HIPAA in the US; special-category data rules under UK GDPR), patient safety requirements.
- **Success measures:** correct patient matching, shorter waiting times, fewer record errors, zero privacy incidents.
- **What stays the same:** layers and the matching idea.
- **What changes:** most uncertain matches go to a trained person for review; every view of a patient record is logged; clinical notes are visible only to staff treating that patient.
- **Why:** a wrong merge can place one patient's results in another's record, a safety and privacy risk.

## 6. Manufacturing

- **Data:** machine sensor readings arriving continuously, production runs, quality test results.
- **Integrations:** factory control systems, ERP, quality systems.
- **Business rules:** trace every part to a batch (for recalls); downtime and defect rules.
- **Regulation:** product safety and traceability rules; operational safety.
- **Success measures:** less downtime, fewer defects, faster recall response.
- **What changes:** streaming ingestion may be justified (in Brightwell's design streaming was rejected because no requirement needed it); the key identity is a part or batch, not a person.

## 7. Summary of design differences

- Matching strictness: low in retail, highest in healthcare and banking.
- Audit and logging: standard in retail, heavy in banking and healthcare.
- Ingestion: batch in retail; streaming possible in manufacturing.
- Human review: occasional in retail; routine in healthcare.
