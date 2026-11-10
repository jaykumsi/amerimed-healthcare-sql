# Amerimed Healthcare SQL: DML: Insert, Update, Delete

Change data with INSERT, UPDATE, DELETE and MERGE, safely: preview first, use transactions, and capture changes with OUTPUT. Every answer here is rolled back after it runs.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### DML-B01: Insert one row

Add a new patient: ID 101, name 'Ava Thompson', number PT-0000101, region West.

### DML-B02: Insert several rows

Add two doctors in one statement: (51, 'Dr. Maya Ross', MD-SIM-000051) and (52, 'Dr. Owen Hart', MD-SIM-000052), both Family Medicine.

### DML-B03: Update one row

Patient 3 moved to the North region. Update the record.

### DML-B04: Update several columns

Encounter 205 is finished: set Status to 'Closed' and Note to 'Completed visit'.

### DML-B05: Update with a calculation

Increase the unit cost of all Vitamin medications by 10%.

### DML-B06: Delete rows

Delete medications that have never been prescribed.

### DML-B07: Preview before you change

Before deleting Pending encounters that have no prescriptions, preview how many rows would be affected.

### DML-B08: Insert from a SELECT

Create a table #ClosedVisits and fill it with all Closed encounters (ID, patient, date).

### DML-B09: Set a value to NULL

Clear the BackupNote on encounter 17.

### DML-B10: Use a transaction

In a transaction, change patient 1's region to 'East', check it, then roll back and check again.


## Intermediate

### DML-I01: Update using a join

Add 5 to the charge of every encounter for patients in the East region.

### DML-I02: Delete using a join

Delete the prescriptions written during telehealth encounters (EncounterType 'C').

### DML-I03: OUTPUT the changed rows

Close all Open encounters from November 2024 and return the IDs with old and new status.

### DML-I04: Identity value after insert

Insert a row into a table with an IDENTITY key and get the new ID.

### DML-I05: Update from an aggregate

Add a VisitCount column to a copy of Patients and fill it with each patient's number of encounters (0 if none).

### DML-I06: Conditional update with CASE

Re-price medications: below 0.10 add 0.02, from 0.10 to 0.20 add 0.03, above 0.20 add 0.05. Show how many medications fall in each band.

### DML-I07: Upsert with IF EXISTS

If patient 101 exists, set the region to 'South'; otherwise insert them as 'Ava Thompson', PT-0000101, South.

### DML-I08: Delete the oldest rows in batches

Delete Closed encounters' prescriptions in batches of 50 rows, and report how many batches it took.

### DML-I09: Swap two values

Swap the Note and BackupNote values for encounter 17 in one statement.

### DML-I10: Insert only new rows

Insert patients 101-103 from a staging list, skipping any PatientID that already exists (patient 100 is in the list too).


## Advanced

### DML-A01: MERGE: sync a staging table

Sync medication prices from a staging list: update prices that changed, insert new medications, and report each action.

### DML-A02: Audit trail with OUTPUT INTO

Raise every Ibuprofen price by 0.01 and write the old and new prices into an audit table in the same statement.

### DML-A03: Remove exact duplicates

A staging copy of Patients accidentally received every North patient twice. Remove the duplicates, keeping one of each.

### DML-A04: Soft delete

Instead of deleting doctors, mark them inactive. Add IsDeleted (bit, default 0), soft-delete doctor 50, and show active doctors count.

### DML-A05: Slowly changing dimension (type 2)

Keep history of patient regions: create a #PatientHistory table with ValidFrom/ValidTo, load current rows, then record that patient 3 moved to North on 2025-01-01.

### DML-A06: Error handling in a data change

Move encounter 1's prescriptions to its follow-up, encounter 96, inside TRY/CATCH with a transaction, and roll back on any error.

### DML-A07: Update top N by order

Close only the 5 oldest Open encounters.

### DML-A08: Delete parents and children in order

Delete patient 4 and everything that depends on them (prescriptions, follow-ups and encounters) in the right order.

### DML-A09: Generate test rows with a set

Insert 20 test encounters for patient 96 in one statement, one per day starting 2025-01-01, with IDs 1001-1020.

### DML-A10: Lock-friendly update pattern

Update only rows that really change: set Note to 'Follow-up with established primary care physician' for type B encounters, skipping rows that already have that note. Report the rows changed.
