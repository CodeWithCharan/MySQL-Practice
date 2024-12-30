# SQL Joins

The `Joins` folder contains examples and exercises that demonstrate the usage of SQL joins to combine rows from two or more tables based on related columns. Below are the details of the contents.

---

## File: [basic_joins.txt](basic_joins.txt)
This file contains beginner-level SQL join exercises to understand fundamental join operations. 

### Problems
1. **Sum of City Populations in Asia**
   - Tables: `CITY`, `COUNTRY`
   - **Query**:
     ```sql
     SELECT SUM(CITY.POPULATION)
     FROM CITY
     INNER JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
     WHERE COUNTRY.CONTINENT = 'Asia';
     ```

2. **Names of Cities in Africa**
   - Tables: `CITY`, `COUNTRY`
   - **Query**:
     ```sql
     SELECT CITY.NAME
     FROM CITY
     INNER JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
     WHERE COUNTRY.CONTINENT = 'Africa';
     ```

3. **Average City Populations by Continent**
   - Tables: `CITY`, `COUNTRY`
   - **Query**:
     ```sql
     SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
     FROM CITY
     INNER JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
     GROUP BY COUNTRY.CONTINENT;
     ```

---

## File: [leetcode-joins.txt](leetcode-joins.txt)
This file contains SQL join problems from LeetCode, providing real-world scenarios and challenges.

### Problems
1. **Combine Two Tables** (LeetCode Problem 175)
   - Tables: `Person`, `Address`
   - **Example**:
     - **Input**:
       ```
       Person:
       +----------+----------+-----------+
       | personId | lastName | firstName |
       +----------+----------+-----------+
       | 1        | Wang     | Allen     |
       | 2        | Alice    | Bob       |
       +----------+----------+-----------+

       Address:
       +-----------+----------+---------------+------------+
       | addressId | personId | city          | state      |
       +-----------+----------+---------------+------------+
       | 1         | 2        | New York City | New York   |
       | 2         | 3        | Leetcode      | California |
       +-----------+----------+---------------+------------+
       ```
     - **Output**:
       ```
       +-----------+----------+---------------+----------+
       | firstName | lastName | city          | state    |
       +-----------+----------+---------------+----------+
       | Allen     | Wang     | Null          | Null     |
       | Bob       | Alice    | New York City | New York |
       +-----------+----------+---------------+----------+
       ```
   - **Query**:
     ```sql
     SELECT P.firstName, P.lastName, A.city, A.state
     FROM Person P
     LEFT JOIN Address A ON P.personId = A.personId;
     ```

2. **Employees Earning More Than Their Managers** (LeetCode Problem 181)
   - Tables: `Employee`
   - **Example**:
     - **Input**:
       ```
       Employee:
       +----+-------+--------+-----------+
       | id | name  | salary | managerId |
       +----+-------+--------+-----------+
       | 1  | Joe   | 70000  | 3         |
       | 2  | Henry | 80000  | 4         |
       | 3  | Sam   | 60000  | Null      |
       | 4  | Max   | 90000  | Null      |
       +----+-------+--------+-----------+
       ```
     - **Output**:
       ```
       +----------+
       | Employee |
       +----------+
       | Joe      |
       +----------+
       ```
   - **Query**:
     ```sql
     SELECT E1.name AS Employee
     FROM Employee E1
     LEFT JOIN Employee E2 ON E1.managerId = E2.id
     WHERE E1.salary > E2.salary;
     ```