# Amerimed Healthcare SQL Assignments

**Tinitiate AI Academy · Instructor: Jayathirth Kumsiravinder**

16 topics × 30 questions = 480 questions. Each topic has 10 Beginner, 10 Intermediate and 10 Advanced questions. Work through them in order; the Advanced questions are the kind asked in SQL interviews.

## Before you start

1. **Create a practice database** in SQL Server Management Studio (for example `AmerimedPractice`) and select it.
2. **Load the data:** open `data_setup.sql` from the healthcare folder and run it once. It creates the `healthcare` schema and fills
   Patients (100), Doctors (50), Medications (50), Encounters (240) and Prescriptions (164).
3. **Questions that change data or tables** (DDL, Constraints, DML): wrap your work in `BEGIN TRAN ... ROLLBACK TRAN`
   so the data stays the same for the next question, or reload the database afterwards.

## The tables

| Table | What it holds | Key columns |
|---|---|---|
| healthcare.Patients | One row per patient | PatientID (PK), PatientName, PatientNumber, Region |
| healthcare.Doctors | One row per doctor | DoctorID (PK), DoctorName, LicenseNumber, Specialty |
| healthcare.Medications | Medication price list | MedicationID (PK), MedicationName, MedicationCode, UnitCost |
| healthcare.Encounters | One row per visit | EncounterID (PK), PatientID (FK), DoctorID (FK), EncounterType (A office, B follow-up, C telehealth), Status (Open, Closed, Pending), Charge, EncounterDate, StartedAt, RecordedAt, Note, BackupNote, ParentEncounterID (FK to the original visit) |
| healthcare.Prescriptions | Medications given in a visit | PrescriptionID (PK), EncounterID (FK), MedicationID (FK), PrescriptionReference, Quantity |

## How to submit

- Save one `.sql` file per topic, named `TOPIC_YourName.sql` (for example `JOINS_PriyaSharma.sql`).
- Put the question ID as a comment above each answer, e.g. `-- JOINS-B03`.
- Under each query, add a comment with the number of rows your query returned.
- For questions that ask you to explain something, write your answer as a comment.

## Topics

1. Introduction: Database Concepts
2. Database, Schema & Security
3. Data Types & Conversion
4. DDL: Create, Alter, Drop
5. Constraints & Data Integrity
6. DML: Insert, Update, Delete
7. DQL: SELECT Basics
8. Operators & Filtering
9. Joins
10. Set Operations
11. Aggregates: GROUP BY & HAVING
12. String Functions
13. Date Functions
14. Subqueries
15. Analytical (Window) Functions
16. CTE (WITH Clause)

---

# Topic 1: Introduction: Database Concepts

The theory interviewers ask before any query: tables, keys, relationships, normalization, ACID, OLTP vs OLAP and how SQL Server runs a query. Some answers are explanations only; others prove the idea with a query on the Amerimed data.

## Beginner

### INTRODUCTION-B01: What is a relational database?

In two or three sentences, explain what a relational database is, using the Amerimed tables as the example.

### INTRODUCTION-B02: Table, row and column

How many tables are in the healthcare schema, and how many columns does each have? Answer with a query.

### INTRODUCTION-B03: Primary key

What is a primary key? Show that PatientID in Patients is unique by comparing the row count with the distinct count.

### INTRODUCTION-B04: Foreign key

What is a foreign key? Explain the link between Encounters and Patients.

### INTRODUCTION-B05: SQL command families

Name the main families of SQL commands and give one example of each.

### INTRODUCTION-B06: What does NULL mean?

What does NULL mean, and how many encounters have a NULL ParentEncounterID?

### INTRODUCTION-B07: One-to-many relationship

Give an example of a one-to-many relationship at Amerimed, and prove it with a query showing the most encounters for a single patient.

### INTRODUCTION-B08: Many-to-many relationship

How are Encounters and Medications related? Which table makes it work?

### INTRODUCTION-B09: Schema

What is a schema? List the objects that belong to the healthcare schema.

### INTRODUCTION-B10: Which SQL Server am I on?

Show the SQL Server version, the current database and the current login.


## Intermediate

### INTRODUCTION-I01: Normalization (1NF, 2NF, 3NF)

Explain the first three normal forms using Amerimed examples.

### INTRODUCTION-I02: Why not store everything in one table?

Show the problem with a denormalized design: how many times is each doctor's name repeated if we put it on every encounter row?

### INTRODUCTION-I03: ACID

What does ACID stand for? Give a healthcare example for each letter.

### INTRODUCTION-I04: OLTP vs OLAP

Explain the difference between OLTP and OLAP systems. Which one is the Amerimed schema?

### INTRODUCTION-I05: Logical query processing order

In what order does SQL Server logically process the clauses of a SELECT? Prove that WHERE cannot use a SELECT alias but ORDER BY can.

### INTRODUCTION-I06: Clustered vs nonclustered index

Explain clustered and nonclustered indexes, and list the indexes on Encounters.

### INTRODUCTION-I07: Natural vs surrogate keys

PatientNumber (PT-0000001) and PatientID (1) both identify a patient. Which is the natural key, which is the surrogate key, and why does the schema use PatientID as the primary key?

### INTRODUCTION-I08: DELETE vs TRUNCATE vs DROP

Explain the differences between DELETE, TRUNCATE and DROP.

### INTRODUCTION-I09: WHERE vs HAVING

Explain WHERE vs HAVING with one query that uses both.

### INTRODUCTION-I10: Views vs tables

What is a view and when would you use one? What is the difference from a table?


## Advanced

### INTRODUCTION-A01: Execution plan basics

What is an execution plan? Show the estimated plan for a query that finds encounters of patient 1, and name the main operator.

### INTRODUCTION-A02: Scan vs seek

Explain the difference between an index scan and an index seek. Which predicates allow a seek?

### INTRODUCTION-A03: Isolation levels

Name SQL Server's transaction isolation levels and the problem each one prevents. Show the current level.

### INTRODUCTION-A04: Star schema from OLTP

Sketch how the Amerimed OLTP tables would become a star schema for reporting. Then write the query that would load a FactEncounter table.

### INTRODUCTION-A05: Deadlock

What is a deadlock, how does SQL Server resolve it, and how do you prevent it?

### INTRODUCTION-A06: Statistics and cardinality

What are statistics, and why do they matter? Show the statistics objects on Encounters.

### INTRODUCTION-A07: Transaction log and recovery models

What is the transaction log, and what is the difference between the FULL and SIMPLE recovery models? Show this database's recovery model.

### INTRODUCTION-A08: Parameter sniffing

Explain parameter sniffing and one way to handle it.

### INTRODUCTION-A09: SARGability test

Run both versions of a 2024 filter and show they return the same rows. Explain which one can use an index.

### INTRODUCTION-A10: Design question: add appointments

Interview design question: Amerimed wants to store future appointments that become encounters. How would you model it?

---

# Topic 2: Database, Schema & Security

Databases, schemas, logins, users, roles and permissions: who can see and change Amerimed's patient data. Instance-level statements (CREATE DATABASE, CREATE LOGIN) are shown but not run here; everything else runs and is rolled back.

## Beginner

### DATABASE_SCHEMA_USER-B01: Create a database

Write the statement to create a database called AmerimedTraining.

### DATABASE_SCHEMA_USER-B02: List databases

List all databases on the server with their creation date.

### DATABASE_SCHEMA_USER-B03: Switch database

Switch to the database you are practising in and confirm the current database name.

### DATABASE_SCHEMA_USER-B04: Create a schema

Create a schema called reporting.

### DATABASE_SCHEMA_USER-B05: List schemas

List all user schemas in the current database (skip the built-in role schemas).

### DATABASE_SCHEMA_USER-B06: Objects in a schema

How many tables does each schema have?

### DATABASE_SCHEMA_USER-B07: Login vs user

What is the difference between a login and a database user?

### DATABASE_SCHEMA_USER-B08: Create a user without a login

Create a database user called report_reader that has no login (useful for testing permissions).

### DATABASE_SCHEMA_USER-B09: Grant SELECT

Give report_reader permission to read the Patients table.

### DATABASE_SCHEMA_USER-B10: Who am I?

Show the current database user and login.


## Intermediate

### DATABASE_SCHEMA_USER-I01: Move a table to another schema

Create a table dbo.TempReport, then move it into the reporting schema.

### DATABASE_SCHEMA_USER-I02: Grant on a whole schema

Give report_reader read access to every table in the healthcare schema with one statement.

### DATABASE_SCHEMA_USER-I03: Test permissions with EXECUTE AS

Give report_reader SELECT on Patients only. Then, acting as report_reader, check which tables it can read.

### DATABASE_SCHEMA_USER-I04: Database roles

Create a role clinical_reader, give it SELECT on Encounters and Prescriptions, and add report_reader to it.

### DATABASE_SCHEMA_USER-I05: REVOKE vs DENY

Explain the difference between REVOKE and DENY, and show DENY overriding a role grant.

### DATABASE_SCHEMA_USER-I06: Column-level permissions

Allow report_reader to read only PatientID and Region from Patients (not names).

### DATABASE_SCHEMA_USER-I07: Default schema

Create a user whose default schema is healthcare, then check it.

### DATABASE_SCHEMA_USER-I08: View as a security layer

Create a view that hides patient names, and give report_reader access to the view only.

### DATABASE_SCHEMA_USER-I09: Remove access cleanly

report_reader is leaving the team. Remove them from the clinical_reader role and drop the user. Confirm they are gone.

### DATABASE_SCHEMA_USER-I10: Fixed database roles

List the fixed database roles and explain db_datareader and db_datawriter.


## Advanced

### DATABASE_SCHEMA_USER-A01: Row-level security

Make report_reader see only North-region patients using row-level security.

### DATABASE_SCHEMA_USER-A02: Dynamic data masking

Mask PatientNumber so non-privileged users see only the last 3 characters.

### DATABASE_SCHEMA_USER-A03: Effective permissions

List every permission that report_reader effectively has on healthcare.Encounters, including those from roles.

### DATABASE_SCHEMA_USER-A04: Audit who has access

Write an audit query: every user or role with any permission on objects in the healthcare schema.

### DATABASE_SCHEMA_USER-A05: Stored procedure as the only door

Let app_user add encounters only through a stored procedure, with no direct INSERT permission on the table.

### DATABASE_SCHEMA_USER-A06: Contained database users

Explain contained database users and when you would use them.

### DATABASE_SCHEMA_USER-A07: Synonym across schemas

Create a synonym reporting.Visits that points to healthcare.Encounters and query through it.

### DATABASE_SCHEMA_USER-A08: Least-privilege setup script

Create a complete read-only analyst role for reporting: SELECT on the healthcare schema, DENY on the Patients name column, and a member user. Show what the member can read.

### DATABASE_SCHEMA_USER-A09: Ownership chain broken

Show that ownership chaining breaks when the view and table have different owners. (Explain only.)

### DATABASE_SCHEMA_USER-A10: Find orphaned users

Find database users whose login no longer exists on the server (orphaned users after a restore).

---

# Topic 3: Data Types & Conversion

Choosing the right type and converting safely: int family, decimal vs float, char/varchar/nvarchar, date and time types, bit, CAST, CONVERT, TRY_CAST, rounding and implicit conversion.

## Beginner

### DATATYPES-B01: See a table's data types

List every column in Encounters with its data type, length, precision and scale.

### DATATYPES-B02: Integer types

Show the storage size of tinyint, smallint, int and bigint using DATALENGTH.

### DATATYPES-B03: CAST a number to text

Show each PatientID as text joined to the word 'Patient #'.

### DATATYPES-B04: Decimal precision and scale

What do the numbers in decimal(12,2) mean? Show the precision and scale of Medications.UnitCost.

### DATATYPES-B05: varchar vs nvarchar

Compare the bytes used by the same text stored as varchar and as nvarchar.

### DATATYPES-B06: char vs varchar

Store 'AB' in char(5) and varchar(5). Show the length and the bytes of each.

### DATATYPES-B07: Date and time types

Show the same moment as date, time, datetime, datetime2 and datetimeoffset.

### DATATYPES-B08: bit type

Count encounters with and without a BackupNote, using a bit flag.

### DATATYPES-B09: Text to date

Convert the text '20240315' into a date and add 10 days.

### DATATYPES-B10: Round a decimal

Show 152.7675 rounded to 2 decimals, rounded to the nearest 10, and cut (truncated) to 2 decimals.


## Intermediate

### DATATYPES-I01: TRY_CAST for bad data

A staging column has the values '120', 'abc', '75.5' and NULL. Convert them to decimal without errors and flag the bad ones.

### DATATYPES-I02: CONVERT styles

Show the date 2024-03-15 as text in styles 101, 103, 112 and 120.

### DATATYPES-I03: Integer division

Show the difference between 7 / 2, 7 / 2.0 and CAST(7 AS decimal(5,2)) / 2.

### DATATYPES-I04: float is not exact

Add 0.1 three times as float and as decimal, and compare each with 0.3.

### DATATYPES-I05: Overflow

What happens when you put 300 into a tinyint? Use TRY_CAST to show it safely.

### DATATYPES-I06: Implicit conversion

PatientNumber is varchar. Show a query that compares it with an nvarchar literal and one that compares with a varchar literal. Explain why it matters.

### DATATYPES-I07: Data type precedence

What type is the result of 1 + '2'? And of 1 + 2.5? Use SQL_VARIANT_PROPERTY to show the base types.

### DATATYPES-I08: Money calculation with the right scale

Calculate each prescription's cost (Quantity × UnitCost) and show it as decimal(10,2).

### DATATYPES-I09: ISDATE and TRY_CONVERT

Validate the date strings '2024-02-29', '2023-02-29' and '31/12/2024' (UK style).

### DATATYPES-I10: Unicode literals

Show what happens when a non-Latin name is stored without the N prefix.


## Advanced

### DATATYPES-A01: Choose types for a new table

Design types for an Invoices table: invoice number like INV-2024-000001, amount up to 999,999.99, currency code like USD, issued timestamp with time zone, paid yes/no. Create it and show the column sizes.

### DATATYPES-A02: Date range bug with datetime

Show why `BETWEEN '2024-03-01' AND '2024-03-31'` misses rows on a datetime2 column such as StartedAt, and write the correct filter.

### DATATYPES-A03: Find values that would not fit

Before changing Encounters.Note from nvarchar(100) to nvarchar(30), find the rows that would not fit.

### DATATYPES-A04: Safe numeric parsing from codes

Extract the number at the end of each EncounterReference (after the last '-') as an int, safely.

### DATATYPES-A05: Time zone math

RecordedAt is stored in UTC. Show encounter 1's RecordedAt in India (+05:30) and in New York, and the offset of each.

### DATATYPES-A06: Rounding money correctly

Split a 100.00 charge equally across 3 payers so the parts add back to exactly 100.00.

### DATATYPES-A07: uniqueidentifier keys

Create a table using a uniqueidentifier key with NEWSEQUENTIALID(), insert 3 rows, and show the bytes per key compared with int.

### DATATYPES-A08: sql_variant and type checking

Show the base type, precision and scale of Charge, UnitCost * Quantity, and AVG(Charge).

### DATATYPES-A09: JSON as a data type

Store a small JSON document of encounter 1's details in a variable, check it is valid JSON, and read two values from it.

### DATATYPES-A10: Pick types to save space

Estimate the row size saving if ServiceUnits (int) became tinyint and Status (varchar(10)) became a tinyint code, for 240 rows and for 10 million rows.

---

# Topic 4: DDL: Create, Alter, Drop

Data Definition Language builds and changes database objects: CREATE / ALTER / DROP / TRUNCATE for tables, plus views, indexes and computed columns. Every answer here runs inside a transaction that is rolled back, so nothing is changed permanently.

## Beginner

### DDL-B01: Create a table

Create a table healthcare.Departments with DepartmentID (int, primary key) and DepartmentName (nvarchar(60), required).

### DDL-B02: Create and check

Create healthcare.Rooms (RoomID int primary key, RoomName varchar(30) not null), then confirm it exists using sys.tables.

### DDL-B03: Add a column

Add an optional Email column (varchar(120)) to healthcare.Patients.

### DDL-B04: Add a column with a default

Add a column IsActive (bit, not null) to healthcare.Doctors with a default value of 1.

### DDL-B05: Change a column's size

Make Patients.Region longer: change it to varchar(20), still NOT NULL.

### DDL-B06: Drop a column

Add a temporary column TempNote to Medications, then drop it.

### DDL-B07: Drop a table safely

Create a table healthcare.Scratch, then drop it only if it exists.

### DDL-B08: Rename a column

Rename the column Note in Encounters to VisitNote.

### DDL-B09: TRUNCATE vs DELETE

Copy Prescriptions into a temp table #Rx, then remove all rows from the copy with TRUNCATE and check the count.

### DDL-B10: Copy a table with SELECT INTO

Create a new table healthcare.NorthPatients containing only North-region patients.


## Intermediate

### DDL-I01: Table with identity and defaults

Create healthcare.Appointments with AppointmentID as an auto-number starting at 1000, PatientID, AppointmentAt datetime2, Status defaulting to 'Booked' and CreatedAt defaulting to the current time.

### DDL-I02: Computed column

Add a computed column LineTotal to a copy of Prescriptions that equals Quantity × 0.15.

### DDL-I03: Create a view

Create a view healthcare.vEncounterDetails showing encounter ID, date, patient name, doctor name and charge.

### DDL-I04: Create an index

Create a nonclustered index on Encounters(PatientID, EncounterDate) to speed up "visits of a patient" queries.

### DDL-I05: Covering index with INCLUDE

Create an index on Encounters(Status) that also includes Charge, so 'total charge by status' can be answered from the index alone.

### DDL-I06: Alter a view

Create a view of Open encounters, then change it to show Open and Pending encounters.

### DDL-I07: Temp table vs table variable

Store the North patients in a table variable @North and count them.

### DDL-I08: Add a foreign key to a new table

Create healthcare.Allergies (AllergyID primary key, PatientID that must exist in Patients, Allergen nvarchar(60)).

### DDL-I09: Find columns that allow NULL

List every column in the Encounters table that allows NULL, with its data type.

### DDL-I10: Schema-bound view

Create a view WITH SCHEMABINDING over Medications and confirm it is schema-bound.


## Advanced

### DDL-A01: Indexed (materialized) view

Create an indexed view that stores the encounter count and total charge per patient.

### DDL-A02: Filtered index

Create an index that only covers Open encounters, sorted by EncounterDate.

### DDL-A03: Add a column to a big table safely

Add a NOT NULL column Priority (tinyint) with default 3 to Encounters, then confirm all rows got 3.

### DDL-A04: Temporal (history) table

Create a system-versioned table healthcare.PriceList that automatically keeps the history of price changes.

### DDL-A05: Partition-ready design

Create a partition function that splits dates into quarters of 2024 and a scheme that maps all partitions to PRIMARY. Show the boundaries.

### DDL-A06: Dependencies before a change

Before renaming Encounters.Charge, find all views that reference it. (Create one test view first.)

### DDL-A07: Rebuild an index and check fragmentation

Create an index on Encounters(DoctorID), rebuild it, and show its fragmentation percentage.

### DDL-A08: Script a table structure

Show the column list of Encounters as one CREATE TABLE-style text, built from metadata.

### DDL-A09: Change a column type with data

Change Medications.UnitCost from decimal(12,2) to decimal(12,4) and confirm the values are kept.

### DDL-A10: SEQUENCE vs IDENTITY

Create a sequence healthcare.seqInvoice that starts at 5000 and increases by 10, then take the next 3 values.

---

# Topic 5: Constraints & Data Integrity

Rules the database enforces on every insert and update: PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK, DEFAULT and NOT NULL. Answers that break a rule catch the error with TRY/CATCH so you can see the message. Everything is rolled back.

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

---

# Topic 6: DML: Insert, Update, Delete

Change data with INSERT, UPDATE, DELETE and MERGE, safely: preview first, use transactions, and capture changes with OUTPUT. Every answer here is rolled back after it runs.

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

---

# Topic 7: DQL: SELECT Basics

Reading data with SELECT, WHERE, ORDER BY, TOP, DISTINCT, aliases and CASE. Every query in SQL starts here.

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

---

# Topic 8: Operators & Filtering

Comparison, logical, arithmetic and pattern operators: =, <>, >, BETWEEN, IN, LIKE, IS NULL, AND, OR, NOT, % and operator precedence.

## Beginner

### OPERATORS-B01: Equal to

List encounters with status 'Pending'.

### OPERATORS-B02: Not equal to

List encounters whose status is not 'Closed'.

### OPERATORS-B03: Greater than or equal

List medications that cost 0.25 or more per unit.

### OPERATORS-B04: BETWEEN for a range

List encounters with a charge between 100 and 120 (both included).

### OPERATORS-B05: IN for a list

List patients from the East or West region using IN.

### OPERATORS-B06: Starts with (LIKE)

Find medications whose name starts with 'Vitamin'.

### OPERATORS-B07: Contains (LIKE)

Find medications with '500mg' anywhere in the name.

### OPERATORS-B08: OR

List encounters that are Open OR have a charge above 240.

### OPERATORS-B09: NOT

List patients who are NOT in the South region, using NOT.

### OPERATORS-B10: Arithmetic operators

For each prescription, show quantity, quantity divided by 30 (months of supply), and the remainder of quantity divided by 30.


## Intermediate

### OPERATORS-I01: AND / OR precedence

List encounters that are Open or Pending AND have a charge of at least 200. Make sure the charge condition applies to both statuses.

### OPERATORS-I02: Date range

List encounters in March 2024.

### OPERATORS-I03: Single-character wildcard

Find patient numbers where the second-to-last digit is 5 (pattern PT-00000_5_ style: any digits, then 5, then one more digit).

### OPERATORS-I04: Character ranges in LIKE

Find patients whose first name starts with A, B or C.

### OPERATORS-I05: NOT LIKE

List medications whose strength is NOT measured in mg (the name does not contain 'mg').

### OPERATORS-I06: NOT IN

List encounters whose type is not A and not B, using NOT IN.

### OPERATORS-I07: IS NOT NULL

List encounters that have a BackupNote.

### OPERATORS-I08: NULL in comparisons

Count encounters where BackupNote <> 'Reviewed by operations'. Why is the answer not 240 − 14?

### OPERATORS-I09: Combining many operators

List type B encounters from the second half of 2024, with charge from 150 to 200, for patients 1 to 50.

### OPERATORS-I10: String concatenation operator

Show each doctor as 'Name (License)', for example 'Dr. Olivia Chen (LIC-...)'.


## Advanced

### OPERATORS-A01: Escape a wildcard character

Find encounter references that contain an underscore character '_' (there may be none). Show how to search for the literal character.

### OPERATORS-A02: Search ignoring case and spaces

Find medications whose name contains 'acid' in any letter case.

### OPERATORS-A03: Sargable date filters

Two ways to get 2024-06 encounters: with MONTH()/YEAR() and with a date range. Write the range version and explain why it is preferred.

### OPERATORS-A04: Divide-by-zero safety

Show each medication's cost per mg-free unit as UnitCost divided by (MedicationID % 5). Avoid errors when the divisor is 0.

### OPERATORS-A05: Integer division trap

Show the share of Open encounters as a percentage. First write it the wrong way (integer division), then the right way.

### OPERATORS-A06: Dynamic ranges with variables

Use variables @From and @To to list encounters in a date range, with @From = '2024-11-01' and @To = '2024-11-30' (inclusive of the last day).

### OPERATORS-A07: Bitwise flags

Encode patients' region as bit flags (North = 1, South = 2, East = 4, West = 8), then find patients whose flag matches the mask 1 | 4 (North or East).

### OPERATORS-A08: Pattern for structured codes

Encounter references look like HEA-YYYYMMDD-NNNNN. Find references that do NOT follow exactly that pattern.

### OPERATORS-A09: CASE with complex conditions

Classify each encounter: 'Review' if Open and charge ≥ 200, 'Chase' if Pending, 'Done' if Closed, otherwise 'Monitor'. Count each class.

### OPERATORS-A10: Short-circuit is not guaranteed

Return medications where the name has a space and the text before the first space is longer than 8 characters. Write it safely so CHARINDEX never gives a negative length.

---

# Topic 9: Joins

Combine rows from two or more tables. Patients → Encounters → Prescriptions → Medications, with Doctors linked to Encounters. Encounters also link to themselves through ParentEncounterID.

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

---

# Topic 10: Set Operations

Stack or compare whole result sets with UNION, UNION ALL, INTERSECT and EXCEPT. Both queries must return the same number of columns with compatible types.

## Beginner

### SET_OPERATIONS-B01: UNION two lists

List the IDs of patients in North together with the IDs of patients in South, in one result.

### SET_OPERATIONS-B02: UNION ALL keeps duplicates

List the patient IDs from Open encounters and from Pending encounters, keeping duplicates.

### SET_OPERATIONS-B03: UNION vs UNION ALL count

Count the rows from UNION and from UNION ALL of the patient IDs in Encounters and Patients.

### SET_OPERATIONS-B04: INTERSECT

Which patient IDs appear both in Patients from the West region and in Encounters?

### SET_OPERATIONS-B05: EXCEPT

Which patients have no encounters? Use EXCEPT.

### SET_OPERATIONS-B06: Medications never prescribed with EXCEPT

List medication IDs that have never been prescribed.

### SET_OPERATIONS-B07: Sorting a UNION

Combine North and East patients' names and sort the full result by name.

### SET_OPERATIONS-B08: Column names come from the first query

Combine doctor names and patient names into one list with a column called PersonName and a Role column.

### SET_OPERATIONS-B09: Matching column count

Combine medication names (text) with medication codes (text) in one column called Label.

### SET_OPERATIONS-B10: Status list from two sources

Show every distinct status that appears in Encounters, plus the value 'Cancelled' (which is planned but not yet used).


## Intermediate

### SET_OPERATIONS-I01: Combine different summaries

Show the number of encounters per status and per encounter type in one result, with a Category column saying which one it is.

### SET_OPERATIONS-I02: Add a total row

Show total charge per region, then a final row labelled 'TOTAL' with the grand total.

### SET_OPERATIONS-I03: Patients active in both halves

Which patients had encounters in both the first half and the second half of 2024?

### SET_OPERATIONS-I04: Seen in December but not November

Which patients had an encounter in December 2024 but none in November 2024?

### SET_OPERATIONS-I05: Doctors without Open work

Using EXCEPT, list doctors who have encounters but none that are Open.

### SET_OPERATIONS-I06: Set operators treat NULLs as equal

Compare the BackupNote values of type A and type B encounters with INTERSECT. Note how NULL behaves.

### SET_OPERATIONS-I07: UNION with a join

List every person with an encounter on 2024-12-31: the patient's name and the doctor's name, each on its own row with a Role column.

### SET_OPERATIONS-I08: Compare two versions of a table

Data check: copy Medications into #MedCopy, change one price, then use EXCEPT to show which rows differ.

### SET_OPERATIONS-I09: Count of a UNION

How many distinct patients had either a type A or a type C encounter?

### SET_OPERATIONS-I10: Precedence of set operators

Show (patients in West UNION patients in East) EXCEPT patients with encounters. Use brackets to control the order.


## Advanced

### SET_OPERATIONS-A01: Symmetric difference

Find patient IDs that appear in exactly one of these sets: patients with type A encounters, patients with type C encounters.

### SET_OPERATIONS-A02: Reconcile two summaries

Check that total charge by region equals total charge by status. Use EXCEPT to prove both give the same grand total (an empty result means they match).

### SET_OPERATIONS-A03: Monthly status report with UNION ALL + pivot

Build a list of (month, metric, value) rows: encounter count and total charge for each month, using UNION ALL. Order by month and metric.

### SET_OPERATIONS-A04: Full outer join with UNION

Without FULL OUTER JOIN, list all medication IDs from Medications and Prescriptions with a flag showing where each appears (Both, Medications only, Prescriptions only).

### SET_OPERATIONS-A05: Find duplicate rows across tables

Which first names are used by both a patient and a doctor? (Doctor names start with 'Dr. ', which must be removed first.)

### SET_OPERATIONS-A06: Gaps between two sets

List the dates in December 2024 that had no encounters, using a recursive calendar and EXCEPT.

### SET_OPERATIONS-A07: Set compare: identical lists?

Check whether the set of patients with prescriptions is exactly the same as the set of patients with Closed encounters. Return the count of differences in each direction.

### SET_OPERATIONS-A08: UNION ALL for an audit trail

Build one timeline for patient 1: each encounter (as 'Visit') and each prescription (as 'Prescription') with its date, ordered by date.

### SET_OPERATIONS-A09: EXCEPT vs NOT EXISTS with duplicates

Compare EXCEPT and NOT EXISTS for 'encounters of patients without prescriptions'. Show the row count from each and explain the difference.

### SET_OPERATIONS-A10: INTERSECT across three sets

Which patients had a type A, a type B and a type C encounter?

---

# Topic 11: Aggregates: GROUP BY & HAVING

Summarise many rows into totals: COUNT, SUM, AVG, MIN, MAX, GROUP BY, HAVING, ROLLUP and GROUPING SETS. These questions come up in almost every SQL interview.

## Beginner

### AGGREGATES-B01: Total charges

What is the total of all encounter charges?

### AGGREGATES-B02: Average charge

What is the average charge per encounter?

### AGGREGATES-B03: Lowest and highest

Show the lowest and highest encounter charge in one row.

### AGGREGATES-B04: Count per group

How many patients are there in each region?

### AGGREGATES-B05: Sum per group

Show the total charge for each encounter status.

### AGGREGATES-B06: Earliest and latest visit

What are the first and last encounter dates in the data?

### AGGREGATES-B07: COUNT(*) vs COUNT(column)

How many encounters are there, and how many of them have a BackupNote?

### AGGREGATES-B08: Distinct count

How many different patients have had at least one encounter?

### AGGREGATES-B09: Filter groups with HAVING

Show encounter types that have more than 30 encounters.

### AGGREGATES-B10: Average medication cost

What is the average unit cost of all medications, rounded to 2 decimals?


## Intermediate

### AGGREGATES-I01: Group by two columns

Count encounters for each combination of encounter type and status.

### AGGREGATES-I02: WHERE and HAVING together

Only for Closed encounters, show patients whose total charge is above 400.

### AGGREGATES-I03: Monthly totals

Show the number of encounters and total charge for each month of 2024.

### AGGREGATES-I04: Average with decimals

On average, how many prescriptions does a patient with prescriptions have? Show the answer with decimals.

### AGGREGATES-I05: Medication spend by medication

For each medication that was prescribed, show the total quantity and total cost (quantity × unit cost). Top 10 by cost.

### AGGREGATES-I06: Region totals with grand total (ROLLUP)

Show total charge per region plus a grand total row at the bottom.

### AGGREGATES-I07: Pivot counts into columns

Show one row per region with columns for the number of A, B and C encounters.

### AGGREGATES-I08: Visit-count histogram

How many patients had 1 visit, how many had 2, how many had 3, and so on?

### AGGREGATES-I09: STRING_AGG: list in one cell

For each region, list all patient names in one comma-separated cell, sorted by name.

### AGGREGATES-I10: Average of averages trap

Show the overall average charge, and the average of the per-region averages. Are they the same?


## Advanced

### AGGREGATES-A01: Above-average patients

Find patients whose total charge is greater than the average total charge per patient.

### AGGREGATES-A02: Region subtotals and grand total (GROUPING SETS)

In one query, show totals by region and status, subtotals by region, and a grand total. Label the summary rows clearly.

### AGGREGATES-A03: Month-over-month change

For each month, show total charge, the previous month's total and the change.

### AGGREGATES-A04: Top 3 patients per region by charge

For each region, show the 3 patients with the highest total charge.

### AGGREGATES-A05: Median charge

Find the median encounter charge.

### AGGREGATES-A06: Share of each status within its region

For each region and status, show the count and what percent it is of that region's encounters.

### AGGREGATES-A07: Busiest weekday

Which day of the week has the most encounters? Show weekday name and count, busiest first.

### AGGREGATES-A08: Patients active in several quarters

Find patients who had encounters in at least 2 different quarters of 2024. Show how many quarters each was active in.

### AGGREGATES-A09: Running total of charges by month

Show each month's total charge and the running total for the year so far.

### AGGREGATES-A10: Doctors above their region's average

For each doctor, compare their total charge with the average doctor total in the same patient region. Show only doctors above their region's average.

---

# Topic 12: String Functions

Clean, split, search and format text: LEN, UPPER, LOWER, TRIM, LEFT, RIGHT, SUBSTRING, CHARINDEX, REPLACE, CONCAT, FORMAT, STRING_AGG and STRING_SPLIT.

## Beginner

### STRING_FUNCTIONS-B01: Length of text

Show each medication name and how many characters it has.

### STRING_FUNCTIONS-B02: Upper and lower case

Show each doctor's name in UPPER case and in lower case.

### STRING_FUNCTIONS-B03: First characters

Show the first 3 characters of each medication code.

### STRING_FUNCTIONS-B04: Last characters

Show the last 5 characters (the number part) of each patient number.

### STRING_FUNCTIONS-B05: Middle characters

From each encounter reference (HEA-YYYYMMDD-NNNNN), extract the 8-digit date part.

### STRING_FUNCTIONS-B06: Join text with CONCAT

Show each patient as 'Name - Region'.

### STRING_FUNCTIONS-B07: Replace text

Show doctor names without the 'Dr. ' title.

### STRING_FUNCTIONS-B08: Trim spaces

Remove spaces from both ends of the text '   Amerimed Clinic   '.

### STRING_FUNCTIONS-B09: Find a character's position

For each patient name, find the position of the space between first and last name.

### STRING_FUNCTIONS-B10: Reverse text

Show each medication code written backwards.


## Intermediate

### STRING_FUNCTIONS-I01: Split first and last name

Split each patient's name into FirstName and LastName.

### STRING_FUNCTIONS-I02: Initials

Show each patient's initials, e.g. 'Olivia Bennett' → 'O.B.'.

### STRING_FUNCTIONS-I03: Number from a code

Turn the numeric part of each medication code (MED-00012) into an integer.

### STRING_FUNCTIONS-I04: Pad with zeros

Show each PatientID as a 6-digit code with leading zeros, e.g. 7 → 000007.

### STRING_FUNCTIONS-I05: Medication strength

Extract the strength (e.g. '500mg') from each medication name. The strength is the second word.

### STRING_FUNCTIONS-I06: Count a character

Count how many spaces are in each medication name.

### STRING_FUNCTIONS-I07: Format a date as text

Show each encounter date as 'Mon DD, YYYY' text, e.g. 'Jan 01, 2024'.

### STRING_FUNCTIONS-I08: Case-insensitive search

Find medications that contain 'ACID' regardless of case, and show the position where it starts.

### STRING_FUNCTIONS-I09: STRING_AGG

For each doctor, list their patients' names in one comma-separated cell.

### STRING_FUNCTIONS-I10: Proper case a word

Turn 'NORTH', 'south' and 'eAST' into 'North', 'South', 'East'.


## Advanced

### STRING_FUNCTIONS-A01: Last word of a name

Return the last word of each medication name (e.g. 'tablet'), using REVERSE.

### STRING_FUNCTIONS-A02: Validate a code format

Find medication codes that are not 'MED-' followed by exactly 5 digits.

### STRING_FUNCTIONS-A03: Split a string into rows

Split the text 'Fever, Cough, Headache' into one row per symptom, with the extra spaces removed.

### STRING_FUNCTIONS-A04: Mask sensitive data

Show patient numbers masked except the last 3 characters, e.g. PT-0000001 → *******001.

### STRING_FUNCTIONS-A05: Most common last name

Which patient last names are the most common? Show the top 5 with counts.

### STRING_FUNCTIONS-A06: Drug family summary

Group medications by family (the first word of the name) and show the number of strengths and the price range as 'min - max'.

### STRING_FUNCTIONS-A07: Find names with repeated letters

Find patient first names that contain the same letter twice in a row (like 'Emma').

### STRING_FUNCTIONS-A08: Build a JSON-like label

For patient 1, build a single text value like {"id":1,"name":"Olivia Bennett","visits":3}.

### STRING_FUNCTIONS-A09: TRANSLATE several characters

Make encounter references 'safe' by turning both '-' and digits 0-4 into '_' in one call (just for demonstration). Show the first 5.

### STRING_FUNCTIONS-A10: Compare text ignoring spaces and case

Check whether ' dr. olivia CHEN ' matches any doctor's name when spaces at the ends and case are ignored.

---

# Topic 13: Date Functions

Work with dates and times: GETDATE, YEAR/MONTH/DAY, DATEPART, DATENAME, DATEADD, DATEDIFF, EOMONTH, DATEFROMPARTS, DATETRUNC-style grouping, CONVERT and time zones.

## Beginner

### DATE_FUNCTIONS-B01: Today's date and time

Show the current date and time, and today's date without the time.

### DATE_FUNCTIONS-B02: Year, month and day

Show each encounter date with its year, month number and day number.

### DATE_FUNCTIONS-B03: Month and weekday names

Show each encounter date with the month name and the weekday name.

### DATE_FUNCTIONS-B04: Add days

Show each encounter date and a follow-up date 30 days later.

### DATE_FUNCTIONS-B05: Days between two dates

How many days are there between the first and the last encounter date?

### DATE_FUNCTIONS-B06: Filter by year and month

List encounters in December 2024.

### DATE_FUNCTIONS-B07: Quarter

Show each encounter date and its quarter (1-4).

### DATE_FUNCTIONS-B08: End of month

Show each encounter date and the last day of that month.

### DATE_FUNCTIONS-B09: Build a date from parts

Build the date for the first day of each encounter's month.

### DATE_FUNCTIONS-B10: Format as text with CONVERT

Show encounter dates in US format (MM/DD/YYYY) and in UK format (DD/MM/YYYY).


## Intermediate

### DATE_FUNCTIONS-I01: Encounters per month

Count encounters per month and show the month as 'YYYY-MM'.

### DATE_FUNCTIONS-I02: Age of a record

For each encounter show how many days ago it was, counting from 2025-01-01 (a fixed reporting date).

### DATE_FUNCTIONS-I03: Weekend visits

List encounters that happened on a Saturday or Sunday.

### DATE_FUNCTIONS-I04: Time of day

Show each encounter's start time and the hour it started. Count encounters per hour.

### DATE_FUNCTIONS-I05: Recording delay in seconds

For each encounter, how many seconds passed between StartedAt and RecordedAt? Show the 5 longest delays.

### DATE_FUNCTIONS-I06: Convert to another time zone

Show RecordedAt (UTC) converted to US Eastern time for the first 5 encounters.

### DATE_FUNCTIONS-I07: Month-to-date

Using @AsOf = '2024-12-15', count encounters from the 1st of that month up to and including @AsOf.

### DATE_FUNCTIONS-I08: Last 30 days

Using @AsOf = '2024-12-31', list encounters in the 30 days up to and including @AsOf.

### DATE_FUNCTIONS-I09: Leap day

Is 2024 a leap year? Show the number of days in February 2024 and February 2025.

### DATE_FUNCTIONS-I10: Week number

Count encounters per ISO week number in January 2024.


## Advanced

### DATE_FUNCTIONS-A01: Age in years done right

A patient was born on 1990-12-31. Show their age in whole years on 2024-12-30 and on 2024-12-31.

### DATE_FUNCTIONS-A02: Monthly totals with missing months

Show all 12 months of 2024 with the encounter count, including months with 0, without a recursive CTE.

### DATE_FUNCTIONS-A03: Same period last year

Compare encounters in December 2024 with December 2023 in one row.

### DATE_FUNCTIONS-A04: Business days between dates

Count the working days (Monday to Friday) between 2024-12-01 and 2024-12-31 inclusive.

### DATE_FUNCTIONS-A05: Average days between visits per patient

For patients with 2 or more visits, show the average number of days between consecutive visits.

### DATE_FUNCTIONS-A06: Week starting Monday

Group encounters by the Monday of their week and count them, for January 2024. Do not depend on SET DATEFIRST.

### DATE_FUNCTIONS-A07: Fiscal year

Amerimed's fiscal year starts on 1 July. Show each encounter's fiscal year (e.g. FY2025 for dates from 2024-07-01 to 2025-06-30) and count encounters per fiscal year.

### DATE_FUNCTIONS-A08: Overlapping time windows

Each encounter covers StartedAt to RecordedAt. Find pairs of encounters whose windows overlap (there may be none). Show each pair once.

### DATE_FUNCTIONS-A09: First and last visit per month

For each month, show the first and last encounter date, and the number of distinct days with visits.

### DATE_FUNCTIONS-A10: Quarter-to-date vs previous quarter

Using @AsOf = '2024-11-15', compare encounters from the start of its quarter to @AsOf with the same span in the previous quarter.

---

# Topic 14: Subqueries

A query inside another query: single-value subqueries, IN / NOT IN lists, EXISTS, correlated subqueries and derived tables. Interviewers use them to test how you think about sets.

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

---

# Topic 15: Analytical (Window) Functions

Window functions compute across related rows without collapsing them: ROW_NUMBER, RANK, DENSE_RANK, NTILE, LAG, LEAD, running totals, moving averages and FIRST_VALUE. These are the most-asked advanced SQL interview topics.

## Beginner

### ANALYTICAL_FUNCTIONS-B01: Number the rows

Number all encounters 1, 2, 3 ... in date order (oldest first).

### ANALYTICAL_FUNCTIONS-B02: Number inside each group

Number each patient's encounters 1, 2, 3 ... in date order.

### ANALYTICAL_FUNCTIONS-B03: RANK by charge

Rank all encounters by charge, highest first. Equal charges should share the same rank.

### ANALYTICAL_FUNCTIONS-B04: DENSE_RANK by charge

Rank encounters by charge, highest first, with no gaps in the rank numbers.

### ANALYTICAL_FUNCTIONS-B05: ROW_NUMBER vs RANK vs DENSE_RANK

Show the three ranking functions side by side for medications ordered by unit cost (highest first).

### ANALYTICAL_FUNCTIONS-B06: Total next to each row

Show each encounter's charge next to the grand total of all charges.

### ANALYTICAL_FUNCTIONS-B07: Patient total next to each visit

Show each encounter with the patient's total charge across all their encounters.

### ANALYTICAL_FUNCTIONS-B08: Previous visit date

For each encounter, show the date of the same patient's previous encounter.

### ANALYTICAL_FUNCTIONS-B09: Next visit date

For each encounter, show the date of the same patient's next encounter.

### ANALYTICAL_FUNCTIONS-B10: Split into quartiles

Split medications into 4 equal price bands (1 = most expensive) using NTILE.


## Intermediate

### ANALYTICAL_FUNCTIONS-I01: Running total

Show each encounter in date order with a running total of charges.

### ANALYTICAL_FUNCTIONS-I02: Running total per patient

For each patient, show a running total of their charges in visit order.

### ANALYTICAL_FUNCTIONS-I03: Days since previous visit

For each encounter, show how many days passed since the same patient's previous encounter.

### ANALYTICAL_FUNCTIONS-I04: Change from previous charge

For each patient, show each charge and how much it went up or down from their previous encounter.

### ANALYTICAL_FUNCTIONS-I05: Latest encounter per patient

Show only each patient's most recent encounter.

### ANALYTICAL_FUNCTIONS-I06: First visit date on every row

Show each encounter together with the patient's first-ever visit date.

### ANALYTICAL_FUNCTIONS-I07: Percent of patient total

For each encounter, show what percent its charge is of the patient's total charge.

### ANALYTICAL_FUNCTIONS-I08: Compare to the average

Show each encounter's charge and how far it is above or below the average charge for its encounter type.

### ANALYTICAL_FUNCTIONS-I09: 3-visit moving average

Show a moving average of charge over the current and previous 2 encounters, in date order.

### ANALYTICAL_FUNCTIONS-I10: Percentile rank

Show each medication's unit cost and its percentile rank (0 = cheapest, 1 = most expensive).


## Advanced

### ANALYTICAL_FUNCTIONS-A01: Top 2 encounters per doctor

For each doctor, show their 2 highest-charge encounters. If charges tie, keep all tied rows.

### ANALYTICAL_FUNCTIONS-A02: Delete duplicates, keep one

Interview classic: patients often get the same medication again (refills). Keep only each patient's FIRST prescription for each medication and delete the repeats. (Runs in a rolled-back transaction here.)

### ANALYTICAL_FUNCTIONS-A03: Gaps and islands: busy-day streaks

Find streaks of consecutive calendar days on which the clinic had at least one encounter. Show each streak's start, end and length, longest first.

### ANALYTICAL_FUNCTIONS-A04: Patients whose charge rose every visit

Find patients with at least 2 visits whose charge went up on every visit after the first.

### ANALYTICAL_FUNCTIONS-A05: Month-over-month growth %

Show each month's total charge, the previous month's total and the growth percentage.

### ANALYTICAL_FUNCTIONS-A06: Cumulative share (Pareto)

Rank patients by total charge and show the cumulative percent of all charges. Which patients make up the first 20% of revenue?

### ANALYTICAL_FUNCTIONS-A07: Second visit per patient

For each patient with at least 2 visits, show their second visit's date and charge.

### ANALYTICAL_FUNCTIONS-A08: Last value done right

Show each encounter with the patient's most recent charge on every row.

### ANALYTICAL_FUNCTIONS-A09: Monthly rank of doctors

For each month, rank doctors by their total charge that month and show only the top doctor (ties included).

### ANALYTICAL_FUNCTIONS-A10: Return visits within N days

Find encounters that happened within @Days days of the same patient's previous encounter (a readmission-style check). Use @Days = 145. Show patient, previous date, current date and gap.

---

# Topic 16: CTE (WITH Clause)

Common Table Expressions name a query step so the next step can use it. They make long queries readable, can be referenced more than once, and can be recursive for hierarchies and calendars.

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
