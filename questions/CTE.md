# Amerimed Healthcare SQL: CTE (WITH Clause)

Common Table Expressions name a query step so the next step can use it. They make long queries readable, can be referenced more than once, and can be recursive for hierarchies and calendars.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### CTE-B01: Your first CTE

Using a CTE named NorthPatients, list the patients in the North region.

### CTE-B02: CTE with a calculation

Use a CTE to calculate the pack cost (UnitCost × 30) for each medication, then list those with a pack cost above 6.

### CTE-B03: CTE with GROUP BY

Use a CTE to count encounters per patient, then show the patients with 3 encounters.

### CTE-B04: Join a CTE to a table

Use a CTE that totals charges per patient, then join it to Patients to show the patient's name and total.

### CTE-B05: Two CTEs

Use one CTE for Open encounters and another for Pending encounters, then show the count of each in one row.

### CTE-B06: Readable column names

Write a CTE with a column list (ID, Name) over Doctors, and select from it.

### CTE-B07: Use a CTE twice

Use one CTE of patient totals to show each patient total next to the highest patient total.

### CTE-B08: Count numbers with a recursive CTE

Use a recursive CTE to produce the numbers 1 to 10.

### CTE-B09: Semicolon before WITH

Declare a variable @Region = 'South', then use a CTE to count patients in that region.

### CTE-B10: Prescriptions with names via CTE

Use a CTE that joins Prescriptions to Medications, then return the 5 largest quantities with medication names.


## Intermediate

### CTE-I01: Chained CTEs

Step 1: total charge per patient. Step 2: average of those totals. Final: patients above the average.

### CTE-I02: Latest visit per patient

Using a CTE with ROW_NUMBER, show each patient's latest encounter with the patient's name.

### CTE-I03: Recursive calendar

Generate every date in January 2024 with a recursive CTE.

### CTE-I04: Days with zero encounters

List every date in January 2024 and the number of encounters on that date, including 0.

### CTE-I05: Monthly calendar with totals

Show all 12 months of 2024 with the encounter count and total charge for each month.

### CTE-I06: Visit chain from one encounter

Starting from encounter 1, use a recursive CTE to list it and every follow-up below it (follow-ups point to their parent through ParentEncounterID), with a level number.

### CTE-I07: Count per type, then pivot

Use a CTE to count encounters per region and encounter type, then show one row per region with A, B and C columns.

### CTE-I08: Update through a CTE

Use a CTE to close (Status = 'Closed') every Open encounter dated before 2024-12-01. Show how many Open encounters remain. (Rolled back here.)

### CTE-I09: Patient summary in steps

Build a summary per patient: number of visits, total charge and number of prescriptions, using one CTE per measure.

### CTE-I10: MAXRECURSION

Generate numbers 1 to 200 with a recursive CTE. (The default limit is 100 levels.)


## Advanced

### CTE-A01: Top 3 medications by spend per region

For each region, show the 3 medications with the highest total spend (quantity × unit cost).

### CTE-A02: Month-over-month with a calendar

For all 12 months of 2024 (even empty ones), show total charge, previous month's total and growth %.

### CTE-A03: Full follow-up tree with path

For every original visit (no parent), list its whole follow-up tree with the level and a path like 1 > 96 > 191.

### CTE-A04: Deepest chain

Which visit chains are the longest? Show the root encounter ID and the depth of its deepest follow-up.

### CTE-A05: Patients above their region's average

Show patients whose total charge is above the average patient total of their own region.

### CTE-A06: Find missing IDs

Interview classic: find missing numbers in an ID column. Medications 5 and 10 were never prescribed and get deleted (the DELETE is part of the setup and is rolled back here). Then find every missing MedicationID between 1 and the highest ID.

### CTE-A07: Running totals and share per region

For each region, list months of 2024 in order with the month total, the running total for the region, and the month's share of the region's yearly total.

### CTE-A08: Split a list into rows

A report stores regions as one text value 'North,South,East'. Use a CTE with STRING_SPLIT to turn it into rows and count patients for each region in the list.

### CTE-A09: Rank within rank

For each region, rank patients by total charge, then show the region's #1 patient along with how far ahead they are of the #2 patient.

### CTE-A10: CTE vs temp table

Store the per-patient totals in a temp table #Totals, then use it twice: once to get the average and once to list patients above it. (In an interview, explain when you would choose a temp table over a CTE.)
