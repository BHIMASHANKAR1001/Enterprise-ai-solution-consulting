# 08 — Governance and Security

> Educational portfolio piece. Brightwell Home & Appliance is fictional. This is a design proposal, not legal advice. Privacy law requirements (for example UK GDPR) must be confirmed with the client's legal team.

**Label:** Proposed future implementation (design only).

## 1. Principles

- **Least privilege:** each role gets only the data its job needs. Access depends on roles and responsibilities.
- **Every dataset has a named owner** who is accountable for its quality and approves access requests.
- **Personal data is protected by default:** masked where not needed, kept only as long as needed, and every access is logged.

## 2. Access by role and layer

- **Marketing analyst:** Gold only. Sees name, email, warranty status and consent to be contacted. Does not see payment details or support complaint notes.
- **Customer support agent:** Gold only, for the customer on the call. Sees contact details, orders, warranty status and open tickets. Card numbers are masked. Cannot export the whole customer list.
- **Finance analyst:** Gold only. Sees transactions, amounts and customer ID. Does not see phone or email, because reconciliation does not need contact details.
- **Executive (CEO, CFO):** Gold, aggregated metrics only.
- **Field service engineer:** only the customers on today's jobs: address, product, warranty and repair history.
- **Data steward and data engineer:** Silver (to fix and match records). Bronze only for named engineers, with approval, because it holds the most raw personal data.
- **Privacy or security officer:** read-only access to audit logs.

## 3. Sensitive fields

- **Payment card numbers:** never stored in full in the platform. Remove or tokenise before loading (the one case where transformation happens before loading).
- **Phone, email, address:** personal data; masked for roles that do not need them.
- **Free-text support notes:** may contain personal details; restricted to Support.

## 4. Metadata and lineage

- A data catalogue lists every table and field with a plain-language meaning, an owner and a last-refreshed time.
- Lineage shows how each Gold figure was built. Example: monthly revenue comes from ERP invoices (Bronze), cleaned (Silver), summed (Gold).

## 5. Retention and audit

- Retention periods are agreed with Legal (to confirm); data past retention is deleted or anonymised.
- Access to sensitive data is logged (who, what, when) and reviewed regularly (NFR4).
- Leavers lose access promptly; access is reviewed periodically.

## 6. Open questions for the client

- Which privacy regulations and customer consents apply?
- Who owns each dataset and approves access?
- What are the legal retention periods for sales and warranty records?

## 7. Risks

- Over-wide access to Bronze. Mitigation: named-engineer access with approval and logging.
- Masking applied inconsistently. Mitigation: apply masking in the platform, not in each report.
