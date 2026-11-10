# Amerimed Healthcare SQL: Joins

Combine rows from two or more tables. Patients → Encounters → Prescriptions → Medications, with Doctors linked to Encounters. Encounters also link to themselves through ParentEncounterID.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### JOINS-B01: Patient name on each visit

Show each encounter ID, its date and the patient's name.

### JOINS-B02: Doctor on each visit

Show each encounter ID with the name of the doctor who saw the patient.

### JOINS-B03: Medication name on each prescription

List each prescription reference with the medication name and quantity.

### JOINS-B04: Join and filter

Show encounters for patients in the West region: encounter ID, patient name, region and charge.

### JOINS-B05: Keep every patient: LEFT JOIN

List every patient and their encounter IDs. Patients with no visits must still appear.

### JOINS-B06: Patients who never visited

Which patients have no encounters at all?

### JOINS-B07: Three tables in one query

Show encounter ID, patient name and doctor name for every encounter.

### JOINS-B08: Count after a join

How many encounters are there per region? Show region and count.

### JOINS-B09: RIGHT JOIN

Using RIGHT JOIN, list every doctor and the encounters they handled (doctors with none must still appear).

### JOINS-B10: Medications never prescribed

Which medications have never been prescribed?


## Intermediate

### JOINS-I01: Four-table chain

For every prescription show the patient name, encounter date, medication name and quantity.

### JOINS-I02: ON vs WHERE in a LEFT JOIN

List every patient with their Open encounters only. Patients with no Open encounter must still appear (with NULL).

### JOINS-I03: Self join: follow-up and original visit

Each follow-up encounter points to its original visit through ParentEncounterID. Show the follow-up ID and date next to the original encounter's ID and date.

### JOINS-I04: Days between visit and follow-up

Using the self join, show how many days passed between each original visit and its follow-up. Show the 5 longest gaps.

### JOINS-I05: Total charge per doctor

Show each doctor's name, number of encounters and total charge. Highest total first.

### JOINS-I06: Counting zero correctly

Show every patient with their number of encounters, including patients with 0.

### JOINS-I07: Medication cost per prescription

For each prescription show the medication, quantity, unit cost and the line cost (quantity × unit cost). Most expensive first.

### JOINS-I08: FULL OUTER JOIN

Show every medication and every prescription in one result: medications never prescribed and prescriptions with no matching medication both appear.

### JOINS-I09: CROSS JOIN for a grid

Build a grid of every region with every encounter type (A, B, C), for a report template.

### JOINS-I10: Patients with repeat prescriptions

Which patients have received 3 or more prescriptions? Show the patient name, the number of prescriptions and the number of different medications.


## Advanced

### JOINS-A01: Fill the grid with real counts

Build the full region × encounter type grid and show the number of encounters in each cell, including 0 for empty cells.

### JOINS-A02: Top-earning doctor per region

For each patient region, find the doctor with the highest total charge. If two doctors tie, show both.

### JOINS-A03: Patient's latest visit with doctor

For every patient who has visited, show their most recent encounter date and the doctor they saw on that visit.

### JOINS-A04: Joins that multiply rows

Show each patient's total encounter charge and total number of prescriptions. Make sure the charge is not double counted.

### JOINS-A05: Patients who got a specific drug and visited again

Find patients who were prescribed any 'Ibuprofen' medication and also have a later encounter after that prescription's visit. Show patient name, the prescription visit date and the next visit date.

### JOINS-A06: Doctors with no Open encounters

List doctors who have encounters but none of them are Open.

### JOINS-A07: Revenue share by region

Show each region's total charge and its percentage of all charges, rounded to 1 decimal place.

### JOINS-A08: Visit chains two levels deep

Some follow-ups have their own follow-ups. Show chains of three visits: original → follow-up → second follow-up, with their IDs.

### JOINS-A09: Patients sharing a doctor

Find pairs of different patients who were seen by the same doctor. Show the doctor name and both patient names, each pair once.

### JOINS-A10: Most prescribed medication per encounter type

For each encounter type, show the medication prescribed most often (by number of prescriptions). Keep ties.
