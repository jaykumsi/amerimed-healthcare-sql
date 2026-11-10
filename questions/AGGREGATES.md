# Amerimed Healthcare SQL: Aggregates: GROUP BY & HAVING

Summarise many rows into totals: COUNT, SUM, AVG, MIN, MAX, GROUP BY, HAVING, ROLLUP and GROUPING SETS. These questions come up in almost every SQL interview.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
