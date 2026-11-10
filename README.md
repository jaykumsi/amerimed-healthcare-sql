# Amerimed Healthcare SQL Assignments

**Tinitiate AI Academy** · Instructor: Jayathirth Kumsiravinder

Practise SQL Server on a realistic hospital database, from your first `SELECT` to the queries asked in interviews.

- **16 topics × 30 questions = 480 questions**
- Each topic has **10 Beginner, 10 Intermediate and 10 Advanced** questions
- Each question shows the **expected result**, so you can check your own work

## Start here

| What | File |
|---|---|
| Interactive assignment page (search, level filter, self-checks, progress) | [`index.html`](index.html): download it and open it in your browser |
| All questions in one document | [`STUDENT_ASSIGNMENTS.md`](STUDENT_ASSIGNMENTS.md) |
| Questions by topic | [`questions/`](questions/) |
| Practice data | [`data_setup.sql`](data_setup.sql) |

## Set up your practice database

1. In SQL Server Management Studio, create a new database (for example `AmerimedPractice`) and select it.
2. Open [`data_setup.sql`](data_setup.sql) and run it once. It creates the `healthcare` schema and loads:

   | Table | Rows | Key columns |
   |---|---:|---|
   | healthcare.Patients | 100 | PatientID, PatientName, PatientNumber, Region |
   | healthcare.Doctors | 50 | DoctorID, DoctorName, LicenseNumber, Specialty |
   | healthcare.Medications | 50 | MedicationID, MedicationName, MedicationCode, UnitCost |
   | healthcare.Encounters | 240 | EncounterID, PatientID, DoctorID, EncounterType (A office, B follow-up, C telehealth), Status (Open, Closed, Pending), Charge, EncounterDate, ParentEncounterID |
   | healthcare.Prescriptions | 164 | PrescriptionID, EncounterID, MedicationID, PrescriptionReference, Quantity |

3. For DDL, Constraints and DML questions, wrap your work in `BEGIN TRAN ... ROLLBACK TRAN` so the data stays the same for the next question.

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

## How to submit

- Save one `.sql` file per topic, named `TOPIC_YourName.sql` (for example `JOINS_PriyaSharma.sql`).
- Put the question ID above each answer as a comment, e.g. `-- JOINS-B03`.
- Under each query, add a comment with the number of rows your query returned.
- For questions that ask you to explain something, write your answer as a comment.

A different query can still be correct. Your instructor checks that your rows and values match the expected result.

---

The data is fictional and for training only. Contact: contact@tinitiateai.com · [tinitiateai.com](https://tinitiateai.com)
