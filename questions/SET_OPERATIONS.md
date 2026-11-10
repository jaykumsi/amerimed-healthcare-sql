# Amerimed Healthcare SQL: Set Operations

Stack or compare whole result sets with UNION, UNION ALL, INTERSECT and EXCEPT. Both queries must return the same number of columns with compatible types.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
