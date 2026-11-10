# Amerimed Healthcare SQL: Analytical (Window) Functions

Window functions compute across related rows without collapsing them: ROW_NUMBER, RANK, DENSE_RANK, NTILE, LAG, LEAD, running totals, moving averages and FIRST_VALUE. These are the most-asked advanced SQL interview topics.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
