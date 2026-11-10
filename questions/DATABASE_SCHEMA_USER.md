# Amerimed Healthcare SQL: Database, Schema & Security

Databases, schemas, logins, users, roles and permissions: who can see and change Amerimed's patient data. Instance-level statements (CREATE DATABASE, CREATE LOGIN) are shown but not run here; everything else runs and is rolled back.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
