# Amerimed Healthcare SQL: DQL: SELECT Basics

Reading data with SELECT, WHERE, ORDER BY, TOP, DISTINCT, aliases and CASE. Every query in SQL starts here.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### DQL-B01: See every patient

Show all columns and all rows from the Patients table.

### DQL-B02: Pick specific columns

Show only the patient ID, name and region for every patient.

### DQL-B03: Filter with WHERE

List the patients who live in the North region.

### DQL-B04: Sort the result

List all doctors sorted by name from A to Z.

### DQL-B05: Most expensive medications

Show the 5 medications with the highest unit cost.

### DQL-B06: Unique values with DISTINCT

Which regions do our patients come from? Show each region once.

### DQL-B07: Rename columns with aliases

List medication names and costs, but show the column headings as Medicine and Price.

### DQL-B08: Calculated column

For every prescription show the quantity and the quantity doubled (for a two-month supply). Call the new column TwoMonthQty.

### DQL-B09: Count the rows

How many encounters (visits) are recorded in total?

### DQL-B10: Combine two conditions

Show the encounters that are Open and whose charge is more than 200.


## Intermediate

### DQL-I01: Sort by two columns

List patients sorted by region, and inside each region by patient name.

### DQL-I02: Label rows with CASE

Show each encounter with its charge and a label: 'High' if the charge is 200 or more, 'Medium' if 100 to 199.99, otherwise 'Low'.

### DQL-I03: Translate codes into words

EncounterType A means Office visit, B means Follow-up, C means Telehealth. Show each encounter ID with the readable visit type.

### DQL-I04: Pagination with OFFSET / FETCH

Patients are shown 10 per page in an app. Return page 3 (patients 21 to 30) ordered by PatientID.

### DQL-I05: Missing values with IS NULL

Find encounters that are NOT linked to a parent encounter (ParentEncounterID is empty).

### DQL-I06: Replace NULL for display

Show encounter ID and BackupNote, but print 'No backup note' when BackupNote is empty.

### DQL-I07: Distinct combinations

Which combinations of encounter type and status exist? Show each pair once.

### DQL-I08: Top rows with ties

Show the top 3 charges, but include any extra encounters that tie with the third-highest charge.

### DQL-I09: Sort by a calculated value

List medications by the cost of a 30-tablet pack, most expensive first. Show the name and the pack cost.

### DQL-I10: Logical order of a query

Show encounters from 2024-06-01 onward with charge at least 150, newest first, returning ID, date and charge.


## Advanced

### DQL-A01: Second-highest charge

Interview classic: find the second-highest distinct charge in Encounters.

### DQL-A02: Nth-highest with OFFSET

Return the 3rd-highest distinct charge using OFFSET / FETCH.

### DQL-A03: Custom sort order

List encounters so Open come first, then Pending, then Closed. Inside each status, newest date first.

### DQL-A04: Conditional counting in one pass

In one row, show how many encounters are Open, Pending and Closed.

### DQL-A05: Find duplicates

Interview classic: are any patient names used by more than one patient? Show the name and how many times it appears.

### DQL-A06: Every Nth row

Return every 10th encounter by EncounterID (10, 20, 30, ...) for a quick audit sample.

### DQL-A07: Random sample

Pick 5 random patients for a satisfaction survey.

### DQL-A08: Search on optional filters

A screen lets users filter by region, but the filter can be empty. Write a query that returns all patients when @Region is NULL, otherwise only that region. Test it with @Region = 'East'.

### DQL-A09: Percent of total in the same row

Show each medication's unit cost and what percent it is of the total of all unit costs, rounded to 2 decimals. Highest first.

### DQL-A10: Visits per patient in a range

List patients who visited between 3 and 4 times, with their visit count, most visits first.
