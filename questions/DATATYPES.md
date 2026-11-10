# Amerimed Healthcare SQL: Data Types & Conversion

Choosing the right type and converting safely: int family, decimal vs float, char/varchar/nvarchar, date and time types, bit, CAST, CONVERT, TRY_CAST, rounding and implicit conversion.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
