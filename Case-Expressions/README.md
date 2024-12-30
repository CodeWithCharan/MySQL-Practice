# Case Expressions in SQL

The `CASE` expression in SQL allows for conditional logic in queries, similar to `if-then-else` statements. It evaluates conditions in order and returns a result when the first condition is met. If no conditions are met, it returns the value in the `ELSE` clause. If no `ELSE` is provided and no conditions are met, `NULL` is returned.

### Syntax
```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

### Content Overview
This folder contains beginner, intermediate, and advanced SQL problems to practice using `CASE` expressions. Below are brief descriptions and example queries for each level.

---

## Beginner Level Problems
1. **Classify students as "Pass" or "Fail" based on their scores**:
   - **Condition**: Score >= 50 is "Pass"; otherwise, "Fail".
   - **Example Table**:
     ```
     +--------+-------+
     | Name   | Score |
     +--------+-------+
     | Alice  | 45    |
     | Bob    | 78    |
     | Carol  | 65    |
     | Dave   | 30    |
     +--------+-------+
     ```
   - **Example Query**:
     ```sql
     SELECT Name, Score,
         CASE
             WHEN Score >= 50 THEN "Pass"
             ELSE "Fail"
         END AS Status
     FROM Students;
     ```

2. **Classify employees into salary ranges**:
   - **Ranges**: "Low" (<3000), "Medium" (3000-7000), "High" (>7000).
   - **Example Table**:
     ```
     +--------+--------+
     | Name   | Salary |
     +--------+--------+
     | John   | 2500   |
     | Sarah  | 5000   |
     | Mike   | 8000   |
     +--------+--------+
     ```
   - **Example Query**:
     ```sql
     SELECT Name, Salary,
         CASE
             WHEN Salary >= 3000 AND Salary <= 7000 THEN "Medium"
             WHEN Salary > 7000 THEN "High"
             ELSE "Low"
         END AS Category
     FROM Employees;
     ```

---

## Intermediate Level Problems
Assign grades based on scores with the following criteria:
- **A**: Score >= 90
- **B**: Score 80-89
- **C**: Score 70-79
- **D**: Below 70

- **Example Table**:
  ```
  +--------+-------+
  | Name   | Score |
  +--------+-------+
  | Alice  | 95    |
  | Bob    | 83    |
  | Carol  | 72    |
  | Dave   | 60    |
  +--------+-------+
  ```
- **Example Query**:
  ```sql
  SELECT Name, Score,
      CASE
          WHEN Score >= 90 THEN "A"
          WHEN Score >= 80 AND Score <= 89 THEN "B"
          WHEN Score >= 70 AND Score <= 79 THEN "C"
          ELSE "D"
      END AS Grade
  FROM Grades;
  ```

---

## Advanced Level Problems
Create labels for employees based on both salary and department:
- **"High Earner - IT"**: Salary > 7000 and Department = "IT".
- **"High Earner - Non-IT"**: Salary > 7000 and Department != "IT".
- **"Regular Earner"**: All other cases.

- **Example Table**:
  ```
  +--------+--------+-------------+
  | Name   | Salary | Department  |
  +--------+--------+-------------+
  | Alice  | 9000   | IT          |
  | Bob    | 8000   | HR          |
  | Carol  | 5000   | IT          |
  +--------+--------+-------------+
  ```
- **Example Query**:
  ```sql
  SELECT Name, Salary, Department,
      CASE
          WHEN Salary > 7000 AND Department = "IT" THEN "High Earner - IT"
          WHEN Salary > 7000 AND Department != "IT" THEN "High Earner - Non-IT"
          ELSE "Regular Earner"
      END AS Label
  FROM EmployeeDetails;
  ```