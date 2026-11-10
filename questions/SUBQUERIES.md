# Amerimed Healthcare SQL: Subqueries

A query inside another query: single-value subqueries, IN / NOT IN lists, EXISTS, correlated subqueries and derived tables. Interviewers use them to test how you think about sets.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### SUBQUERIES-B01: Compare with the average

List encounters whose charge is higher than the average charge.

### SUBQUERIES-B02: Most expensive medication

Show the name of the medication with the highest unit cost.

### SUBQUERIES-B03: Filter with IN

List the patients who have at least one encounter, using IN.

### SUBQUERIES-B04: Filter with NOT IN

List the patients who have never had an encounter, using NOT IN.

### SUBQUERIES-B05: Subquery on another table

List the encounters of patients in the East region (do not use a join).

### SUBQUERIES-B06: Subquery in SELECT

Show each medication with the overall average unit cost next to it.

### SUBQUERIES-B07: Medications that were prescribed

List the medications that appear in at least one prescription.

### SUBQUERIES-B08: Derived table

Use a subquery in FROM that counts encounters per patient, then show patients with 3 encounters.

### SUBQUERIES-B09: Latest date

Show the encounter(s) on the most recent encounter date.

### SUBQUERIES-B10: Cheaper than a given drug

List medications cheaper than 'Omeprazole 20mg tablet'.


## Intermediate

### SUBQUERIES-I01: EXISTS

List patients who have at least one Open encounter, using EXISTS.

### SUBQUERIES-I02: NOT EXISTS

List medications that were never prescribed, using NOT EXISTS.

### SUBQUERIES-I03: Correlated subquery

List encounters whose charge is higher than the average charge of the same encounter type.

### SUBQUERIES-I04: Count in a SELECT subquery

Show each doctor with the number of encounters they handled, using a subquery in SELECT.

### SUBQUERIES-I05: Latest visit per patient (correlated)

Show each patient's latest encounter using a correlated subquery.

### SUBQUERIES-I06: Patients above their own average

List encounters where the charge is higher than that patient's own average charge.

### SUBQUERIES-I07: ANY / ALL

List medications that cost more than ALL Ibuprofen medications.

### SUBQUERIES-I08: Derived table with a join

Show patient names with their total charge, using a derived table for the totals.

### SUBQUERIES-I09: Region with the most patients

Which region has the most patients?

### SUBQUERIES-I10: Prescriptions of the costliest medication

List the prescriptions for the most expensive medication that was actually prescribed.


## Advanced

### SUBQUERIES-A01: NOT IN and the NULL trap

Interview trap: show why NOT IN fails when the list contains NULL. Find encounters that are not a parent of any other encounter, first with NOT IN (wrong), then with NOT EXISTS (right).

### SUBQUERIES-A02: Second-highest per group

For each encounter type, find the second-highest distinct charge using a correlated subquery.

### SUBQUERIES-A03: Patients with refills

Find patients who were prescribed the same medication more than once (refills), using EXISTS.

### SUBQUERIES-A04: Running total with a correlated subquery

Show encounters in ID order with a running total of charges, without window functions.

### SUBQUERIES-A05: Doctors whose every encounter is Closed

List doctors who have encounters and all of them are Closed.

### SUBQUERIES-A06: Rank without window functions

Rank medications by unit cost (1 = most expensive) using a correlated subquery instead of RANK().

### SUBQUERIES-A07: Top patient per region

Using only subqueries (no window functions), show the patient with the highest total charge in each region.

### SUBQUERIES-A08: Visits after a patient's first prescription

For each patient who has a prescription, count how many of their encounters happened after the encounter of their first prescription.

### SUBQUERIES-A09: IN vs EXISTS vs JOIN

Return patients with at least one Pending encounter three ways (IN, EXISTS, JOIN with DISTINCT). Each should return the same count.

### SUBQUERIES-A10: Medications priced above their group's average

Medications come in families (the first word of the name, e.g. 'Ibuprofen'). List medications that cost more than the average of their own family.
