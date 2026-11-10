# Amerimed Healthcare SQL: DDL: Create, Alter, Drop

Data Definition Language builds and changes database objects: CREATE / ALTER / DROP / TRUNCATE for tables, plus views, indexes and computed columns. Every answer here runs inside a transaction that is rolled back, so nothing is changed permanently.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
