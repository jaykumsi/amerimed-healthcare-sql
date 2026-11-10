# Amerimed Healthcare SQL: Constraints & Data Integrity

Rules the database enforces on every insert and update: PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK, DEFAULT and NOT NULL. Answers that break a rule catch the error with TRY/CATCH so you can see the message. Everything is rolled back.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### CONSTRAINTS-B01: List a table's constraints

List all constraints on the Encounters table and their types.

### CONSTRAINTS-B02: Primary key rejects duplicates

Try to insert a patient with PatientID 1, which already exists. Show the error.

### CONSTRAINTS-B03: NOT NULL rejects missing values

Try to insert a doctor without a DoctorName.

### CONSTRAINTS-B04: UNIQUE constraint

Try to insert a new medication with a MedicationCode that already exists (MED-00001).

### CONSTRAINTS-B05: CHECK constraint

Try to set a medication's UnitCost to -5.

### CONSTRAINTS-B06: FOREIGN KEY rejects orphans

Try to add an encounter for PatientID 5000, which does not exist.

### CONSTRAINTS-B07: DEFAULT fills a value

Insert an encounter without giving a Status, then check which Status it got.

### CONSTRAINTS-B08: Add a CHECK constraint

Add a rule that Patients.Region must be North, South, East or West.

### CONSTRAINTS-B09: Add a UNIQUE constraint

Make sure no two doctors share the same name by adding a UNIQUE constraint on DoctorName.

### CONSTRAINTS-B10: Drop a constraint

Add a CHECK that Quantity is at most 365 on Prescriptions, then drop it.


## Intermediate

### CONSTRAINTS-I01: Composite primary key

Create a table healthcare.DoctorSchedule with a primary key on (DoctorID, WorkDate), and show that the same doctor cannot be scheduled twice on one date.

### CONSTRAINTS-I02: Multi-column CHECK

Add a rule to Encounters: when Status is 'Closed', Charge must not be NULL.

### CONSTRAINTS-I03: ON DELETE CASCADE

Create healthcare.PatientContacts with a foreign key to Patients that deletes contacts automatically when the patient is deleted. Test it with patient 96, who has no encounters.

### CONSTRAINTS-I04: Find foreign keys

List every foreign key in the healthcare schema: child table, child column, parent table, parent column.

### CONSTRAINTS-I05: Load order from foreign keys

Why must Patients and Doctors be loaded before Encounters, and Encounters before Prescriptions? Show it by deleting a patient who has encounters.

### CONSTRAINTS-I06: Disable and re-enable a constraint

Disable the CHECK on Medications.UnitCost, insert a bad row, then re-enable the CHECK WITH CHECK and see what happens.

### CONSTRAINTS-I07: Untrusted constraints

Find any CHECK or FOREIGN KEY constraints that are disabled or not trusted.

### CONSTRAINTS-I08: Unique but allow many NULLs

Add an optional NationalID column to Patients that must be unique when it has a value, while many patients can leave it NULL.

### CONSTRAINTS-I09: CHECK using a function

Add a rule that PatientNumber must start with 'PT-' and be exactly 10 characters long.

### CONSTRAINTS-I10: Default from a function

Add a CreatedOn column to Medications that defaults to today's date.


## Advanced

### CONSTRAINTS-A01: Find data that breaks a new rule

Before adding CHECK (Charge <= 240) to Encounters, find the rows that would break it.

### CONSTRAINTS-A02: CHECK passes on NULL

Show that CHECK (Charge >= 0) allows NULL: set encounter 1's Charge to NULL and read it back.

### CONSTRAINTS-A03: Self-referencing foreign key

Encounters.ParentEncounterID references Encounters.EncounterID. Try to point encounter 2 to a parent that does not exist, and try to point encounter 2 to itself.

### CONSTRAINTS-A04: Cascade risks with self-references

Explain why ON DELETE CASCADE cannot be added to the self-referencing key on Encounters. Try it.

### CONSTRAINTS-A05: Business rule across tables

A CHECK cannot look at other tables. Write a trigger that stops prescriptions being added to Pending encounters, then test it.

### CONSTRAINTS-A06: Constraint vs trigger vs app

Write a query that shows, for each table, how many PK, FK, UNIQUE, CHECK and DEFAULT constraints it has.

### CONSTRAINTS-A07: Find orphans before adding a FK

A copy of Prescriptions has a row pointing to a missing medication. Find the orphan rows before adding a foreign key.

### CONSTRAINTS-A08: Cascade an update

Create a small parent/child pair (Wards, Beds) with ON UPDATE CASCADE, change a ward code, and show the beds follow.

### CONSTRAINTS-A09: Validate before insert with MERGE-free logic

Insert three new prescriptions from a staging list, but only those whose EncounterID and MedicationID exist, so no FK error is raised. Show how many were inserted.

### CONSTRAINTS-A10: Constraint error handling in a transaction

In one transaction, insert a good patient and then a duplicate. Use XACT_ABORT and TRY/CATCH so that neither row is saved, and report what happened.
