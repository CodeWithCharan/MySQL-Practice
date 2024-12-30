# REGEXP in SQL

This folder contains examples and queries demonstrating the use of Regular Expressions (REGEXP) in SQL. These commands focus on filtering data based on patterns in text columns, such as names or other string values.

---

## File Description

### 1. [regexp_commands.txt](regexp_commands.txt)
Contains practical examples of using REGEXP in SQL queries to manipulate and filter data based on string patterns. Below is a summary of the commands:

---

### Examples of REGEXP Queries:

1. **Cities Starting with Vowels**
   - Query the list of `CITY` names starting with vowels (`a, e, i, o, u`), ignoring case sensitivity.
   ```sql
   SELECT DISTINCT CITY FROM STATION
   WHERE CITY REGEXP '^[aeiouAEIOU]'
   ```

2. **Cities Ending with Vowels**
   - Query the list of `CITY` names ending with vowels (`a, e, i, o, u`), ignoring case sensitivity.
   ```sql
   SELECT DISTINCT CITY FROM STATION
   WHERE CITY REGEXP '[aeiouAEIOU]$'
   ```

3. **Cities Not Starting with Vowels**
   - Query the list of `CITY` names not starting with vowels.
   ```sql
   SELECT DISTINCT CITY FROM STATION
   WHERE CITY REGEXP '^[^aeiouAEIOU]'
   ```

4. **Cities Not Ending with Vowels**
   - Query the list of `CITY` names not ending with vowels.
   ```sql
   SELECT DISTINCT CITY FROM STATION
   WHERE CITY REGEXP '[^aeiouAEIOU]$'
   ```

---

### Additional REGEXP Use Cases:
You can expand the use of REGEXP to include more advanced patterns, such as:
- **Match Specific Lengths**: Query cities with names exactly 5 characters long.
  ```sql
  SELECT DISTINCT CITY FROM STATION
  WHERE CITY REGEXP '^.{5}$'
  ```

- **Find Words Containing Specific Characters**: Query cities with names containing the substring "abc".
  ```sql
  SELECT DISTINCT CITY FROM STATION
  WHERE CITY REGEXP 'abc'
  ```

- **Exclude Specific Patterns**: Query cities whose names do not contain any digits.
  ```sql
  SELECT DISTINCT CITY FROM STATION
  WHERE CITY NOT REGEXP '[0-9]'
  ```

- **Find Cities Starting and Ending with the Same Letter**: Query cities that start and end with the same letter.
  ```sql
  SELECT DISTINCT CITY FROM STATION
  WHERE CITY REGEXP '^(.).*\1$'
  ```