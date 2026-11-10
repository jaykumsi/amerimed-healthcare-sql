# Amerimed Healthcare SQL: String Functions

Clean, split, search and format text: LEN, UPPER, LOWER, TRIM, LEFT, RIGHT, SUBSTRING, CHARINDEX, REPLACE, CONCAT, FORMAT, STRING_AGG and STRING_SPLIT.

10 Beginner · 10 Intermediate · 10 Advanced. Use the large practice dataset (data_setup.sql).

## Beginner

### STRING_FUNCTIONS-B01: Length of text

Show each medication name and how many characters it has.

### STRING_FUNCTIONS-B02: Upper and lower case

Show each doctor's name in UPPER case and in lower case.

### STRING_FUNCTIONS-B03: First characters

Show the first 3 characters of each medication code.

### STRING_FUNCTIONS-B04: Last characters

Show the last 5 characters (the number part) of each patient number.

### STRING_FUNCTIONS-B05: Middle characters

From each encounter reference (HEA-YYYYMMDD-NNNNN), extract the 8-digit date part.

### STRING_FUNCTIONS-B06: Join text with CONCAT

Show each patient as 'Name - Region'.

### STRING_FUNCTIONS-B07: Replace text

Show doctor names without the 'Dr. ' title.

### STRING_FUNCTIONS-B08: Trim spaces

Remove spaces from both ends of the text '   Amerimed Clinic   '.

### STRING_FUNCTIONS-B09: Find a character's position

For each patient name, find the position of the space between first and last name.

### STRING_FUNCTIONS-B10: Reverse text

Show each medication code written backwards.


## Intermediate

### STRING_FUNCTIONS-I01: Split first and last name

Split each patient's name into FirstName and LastName.

### STRING_FUNCTIONS-I02: Initials

Show each patient's initials, e.g. 'Olivia Bennett' → 'O.B.'.

### STRING_FUNCTIONS-I03: Number from a code

Turn the numeric part of each medication code (MED-00012) into an integer.

### STRING_FUNCTIONS-I04: Pad with zeros

Show each PatientID as a 6-digit code with leading zeros, e.g. 7 → 000007.

### STRING_FUNCTIONS-I05: Medication strength

Extract the strength (e.g. '500mg') from each medication name. The strength is the second word.

### STRING_FUNCTIONS-I06: Count a character

Count how many spaces are in each medication name.

### STRING_FUNCTIONS-I07: Format a date as text

Show each encounter date as 'Mon DD, YYYY' text, e.g. 'Jan 01, 2024'.

### STRING_FUNCTIONS-I08: Case-insensitive search

Find medications that contain 'ACID' regardless of case, and show the position where it starts.

### STRING_FUNCTIONS-I09: STRING_AGG

For each doctor, list their patients' names in one comma-separated cell.

### STRING_FUNCTIONS-I10: Proper case a word

Turn 'NORTH', 'south' and 'eAST' into 'North', 'South', 'East'.


## Advanced

### STRING_FUNCTIONS-A01: Last word of a name

Return the last word of each medication name (e.g. 'tablet'), using REVERSE.

### STRING_FUNCTIONS-A02: Validate a code format

Find medication codes that are not 'MED-' followed by exactly 5 digits.

### STRING_FUNCTIONS-A03: Split a string into rows

Split the text 'Fever, Cough, Headache' into one row per symptom, with the extra spaces removed.

### STRING_FUNCTIONS-A04: Mask sensitive data

Show patient numbers masked except the last 3 characters, e.g. PT-0000001 → *******001.

### STRING_FUNCTIONS-A05: Most common last name

Which patient last names are the most common? Show the top 5 with counts.

### STRING_FUNCTIONS-A06: Drug family summary

Group medications by family (the first word of the name) and show the number of strengths and the price range as 'min - max'.

### STRING_FUNCTIONS-A07: Find names with repeated letters

Find patient first names that contain the same letter twice in a row (like 'Emma').

### STRING_FUNCTIONS-A08: Build a JSON-like label

For patient 1, build a single text value like {"id":1,"name":"Olivia Bennett","visits":3}.

### STRING_FUNCTIONS-A09: TRANSLATE several characters

Make encounter references 'safe' by turning both '-' and digits 0-4 into '_' in one call (just for demonstration). Show the first 5.

### STRING_FUNCTIONS-A10: Compare text ignoring spaces and case

Check whether ' dr. olivia CHEN ' matches any doctor's name when spaces at the ends and case are ignored.
