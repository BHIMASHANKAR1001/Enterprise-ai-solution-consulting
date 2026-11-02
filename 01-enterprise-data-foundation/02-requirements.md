02 — Requirements
> Educational portfolio piece. Brightwell Home & Appliance is fictional. Requirements are assumptions for teaching, not real client commitments.
> **Label:** Demonstrated using synthetic data (fictional client scenario).
> **Status:** DRAFT v1. ✏️ marks items for Vector to add.
1. Success measures (business outcomes, to validate with the client)
ID	Measure	Baseline	Target (assumption)
S1	Average support call handling time	9 minutes	Under 5 minutes within 6 months of launch
S2	Warranty promotions sent to customers with an active warranty	Unknown (✏️ discovery)	Zero
S3	Finance days spent reconciling revenue each month	4 days	1 day or less
S4	Number of different "active customer" counts reported	3	1 agreed count
2. Functional requirements (what the system must do)
ID	Requirement	Source	Test
FR1	The system shall provide one agreed count of active customers, using a definition approved by the CEO and CFO	CEO	The count matches the agreed definition on a test date
FR2	The system shall give support agents one screen showing a customer's contact details, orders, warranty status and open tickets	Head of Support	For 20 test customers, every item appears on one screen
FR3	The system shall exclude customers with an active warranty from warranty promotion lists, using warranty start and end dates	Marketing Director	With 100 test customers (20 with active warranties), none of the 20 appear on the generated list
FR4	The system shall list customers by warranty status: expired first, then by days remaining until expiry, soonest first	Marketing Director	On 100 test customers, the list order matches expiry dates exactly
FR5	The system shall reconcile revenue between the sales dashboard and the finance system and report any differences by order	CFO	A test month with 5 planted differences reports all 5
FR6	The system shall let an authorised user search by customer name or customer ID and return that customer's details drawn from all connected source systems	CIO, Head of Support	Search 20 test customers by name and by ID; each result includes data from every source holding that customer
FR7	✏️ Vector to add (optional): a catalogue listing every data source, its owner and its contents	CIO	✏️
3. Non-functional requirements (how well it must work)
ID	Category	Requirement	Source	Test
NFR1	Performance	A customer record shall load within 3 seconds of the agent searching	Head of Support	95% of 50 timed searches finish within 3 seconds
NFR2	Security and privacy	Agents shall see only the fields needed for support, and card numbers shall be masked	Head of Support, Privacy	Log in as an agent; payment fields are hidden
NFR3	Data freshness	A newly purchased warranty shall appear in Marketing's lists within 24 hours	Marketing Director	Create a test warranty; confirm it is excluded from the next day's list
NFR4	Auditability	Access to sensitive and financial data shall be logged and reviewable	CIO, CFO	Access a test record; the log shows who, what and when
NFR5	Data quality	Duplicate customer records shall be under 1%, measured monthly	CEO	Run the duplicate check on test data
4. Assumptions and open questions
Numbers above are teaching assumptions and must be validated in discovery.
Active customer (proposed definition, by Vector): a customer who made a purchase of any Brightwell product, or had a service visit for any Brightwell product, in the last 12 months. To confirm with the CEO and CFO: whether fully refunded purchases count, whether a customer holding only a running warranty counts, and which date is used (order date, payment date or visit date).
Which systems feed the support screen? Answered in milestone 1.3.
