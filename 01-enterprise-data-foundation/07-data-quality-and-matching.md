# 07 — Data Quality, Matching and Reconciliation

> Educational portfolio piece. Brightwell Home & Appliance is fictional and all data is synthetic.

**Label:** Demonstrated using synthetic data (rules tested by hand on the sample files; not implemented in software).

## 1. Data quality rules

- **Completeness:** every customer record should have an email or a phone number. Test: C006 has no phone but has an email, so it passes with a warning for the missing phone. Warranty W03 has no email, so it is flagged.
- **Validity:** a warranty end date must be later than its start date. Test: W03 fails and goes to a review list.
- **Accuracy (status):** a warranty whose end date has passed must not have status "Active". Test: W02 fails.
- **Consistency:** the same person's name should be spelled the same across systems. Test: "Maria Lopez" (CRM) vs "Maria Lopes" (warranty) is flagged for review.
- **Uniqueness:** a person must not appear twice in the trusted customer table. Test: C003/C004 and C005/C008 are merged.
- **Timeliness:** a new warranty must be visible to Marketing within 24 hours (NFR3).

Failing records are not deleted. They go to a review list with the reason, and the original stays in Bronze.

## 2. Matching rules (deciding if two records are the same person)

- **Match (merge automatically):** same email address, or same phone number and same postcode.
- **Possible match (send to a person to review):** similar name and same postcode, or similar name and same phone number, but different email.
- **No match:** name is the same but email, phone and postcode all differ. A matching name alone is never enough.

### Tested on the sample CRM data

- **C003 and C004:** same email, so match. (Names differ: "James O'Neil" and "Jim ONeil". Name is not needed for the match.)
- **C005 and C008:** same email, so match. ("Aisha Khan" and "A. Khan".)
- **C001 and C002:** same name, but email, phone and postcode all differ, so no match.
- **C007 (CRM) and W05 (warranty):** same email, so match. "Lopes" vs "Lopez" is flagged as a spelling difference.

### Why not require the name to match first

Names are the least reliable field: nicknames, initials and typos all occur, so a rule starting with "same name" would miss C003/C004 and C005/C008. Email and phone are stronger identifiers, though they change. That is why uncertain pairs go to human review instead of being merged or ignored automatically.

### Risk trade-off

Too strict means duplicates remain (customers get two emails). Too loose means two different people are merged, which can expose one person's details to another. For this reason, automatic merges use only strong rules.

## 3. Reconciliation

- **Revenue (FR5):** each month, total POS sales and online orders are compared with ERP revenue. Any difference is listed by receipt or order and given a cause (timing, refund, missing record, different definition).
- **Ingestion completeness:** after every batch, row counts and totals in Bronze are compared with the source.
- **POS examples to catch:** R1006 is a negative amount (an unlabelled refund), and R1004/R1005 may be a duplicated sale.

## 4. Acceptance tests

- All six planted warranty and CRM problems in `sample-data/` are detected.
- C001 and C002 stay separate.
- C003/C004 and C005/C008 are merged.
- A planted revenue difference is reported by receipt.
