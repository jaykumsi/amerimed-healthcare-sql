# Amerimed Healthcare SQL: Operators & Filtering

Comparison, logical, arithmetic and pattern operators: =, <>, >, BETWEEN, IN, LIKE, IS NULL, AND, OR, NOT, % and operator precedence.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

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
