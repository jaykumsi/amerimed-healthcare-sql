# Amerimed Healthcare SQL: Date Functions

Work with dates and times: GETDATE, YEAR/MONTH/DAY, DATEPART, DATENAME, DATEADD, DATEDIFF, EOMONTH, DATEFROMPARTS, DATETRUNC-style grouping, CONVERT and time zones.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
