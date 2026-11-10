# Amerimed Healthcare SQL: Introduction: Database Concepts

The theory interviewers ask before any query: tables, keys, relationships, normalization, ACID, OLTP vs OLAP and how SQL Server runs a query. Some answers are explanations only; others prove the idea with a query on the Amerimed data.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
