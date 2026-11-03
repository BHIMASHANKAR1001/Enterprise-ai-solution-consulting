# 02 — Requirements

> Educational portfolio piece. Brightwell Home & Appliance is fictional. Requirements are assumptions for teaching, not real client commitments.

**Label:** Demonstrated using synthetic data (fictional client scenario).

## 1. Success measures (to validate with the client)

- **S1:** Average support call handling time. Baseline 9 minutes. Target (assumption): under 5 minutes within 6 months of launch.
- **S2:** Warranty promotions sent to customers with an active warranty. Baseline unknown. Target: zero.
- **S3:** Finance days spent reconciling revenue each month. Baseline 4 days. Target: 1 day or less.
- **S4:** Number of different "active customer" counts reported. Baseline 3. Target: 1 agreed count.

## 2. Functional requirements (what the system must do)

- **FR1** (source: CEO): The system shall provide one agreed count of active customers, using a definition approved by the CEO and CFO. Test: the count matches the agreed definition on a test date.
- **FR2** (source: Head of Support): The system shall give support agents one screen showing a customer's contact details, orders, warranty status and open tickets. Test: for 20 test customers, every item appears on one screen.
- **FR3** (source: Marketing Director): The system shall exclude customers with an active warranty from warranty promotion lists, using warranty start and end dates. Test: with 100 test customers (20 with active warranties), none of the 20 appear on the generated list.
- **FR4** (source: Marketing Director): The system shall list customers by warranty status: expired first, then by days remaining until expiry, soonest first. Test: on 100 test customers, the list order matches expiry dates exactly.
- **FR5** (source: CFO): The system shall reconcile revenue between the sales dashboard and the finance system and report any differences by order. Test: a test month with 5 planted differences reports all 5.
- **FR6** (source: CIO, Head of Support): The system shall let an authorised user search by customer name or customer ID and return that customer's details drawn from all connected source systems. Test: search 20 test customers by name and by ID; each result includes data from every source holding that customer.

## 3. Non-functional requirements (how well it must work)

- **NFR1 Performance** (source: Head of Support): A customer record shall load within 3 seconds of the agent searching. Test: 95% of 50 timed searches finish within 3 seconds.
- **NFR2 Security and privacy** (source: Head of Support, Privacy): Agents shall see only the fields needed for support, and card numbers shall be masked. Test: log in as an agent; payment fields are hidden.
- **NFR3 Data freshness** (source: Marketing Director): A newly purchased warranty shall appear in Marketing's lists within 24 hours. Test: create a test warranty; confirm it is excluded from the next day's list.
- **NFR4 Auditability** (source: CIO, CFO): Access to sensitive and financial data shall be logged and reviewable. Test: access a test record; the log shows who, what and when.
- **NFR5 Data quality** (source: CEO): Duplicate customer records shall be under 1%, measured monthly. Test: run the duplicate check on test data.

## 4. Assumptions and open questions

- Numbers above are teaching assumptions and must be validated in discovery.
- **Active customer (proposed definition, by Vector):** a customer who made a purchase of any Brightwell product, or had a service visit for any Brightwell product, in the last 12 months.
- To confirm with the CEO and CFO: whether fully refunded purchases count, whether a customer holding only a running warranty counts, and which date is used (order date, payment date or visit date).
- Which systems feed the support screen? Answered in milestone 1.3.
