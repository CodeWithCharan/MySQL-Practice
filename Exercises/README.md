# SQL Exercises

This folder contains various SQL exercises categorized into multiple files. Each file contains queries solving different problems, showcasing the use of SQL to interact with and manipulate databases.

## Exercise Files

### [Exercise_1.txt](./Exercise_1.txt)

1. Print all movie titles and release years for Marvel Studios movies:
    ```sql
    SELECT title, release_year
    FROM movies
    WHERE studio="Marvel Studios"
    ```

2. Print all movies that have "Avengers" in their name:
    ```sql
    SELECT title
    FROM movies
    WHERE title LIKE "%Avengers%"
    ```

3. Print the year when the movie "The Godfather" was released:
    ```sql
    SELECT release_year
    FROM movies
    WHERE title="The Godfather"
    ```

4. Print all distinct movie studios in the Bollywood industry:
    ```sql
    SELECT DISTINCT studio
    FROM movies
    WHERE industry="Bollywood"
    ```

### [Exercise_2.txt](./Exercise_2.txt)

1. Print all movies in the order of their release year (latest first):
    ```sql
    SELECT *
    FROM movies
    ORDER BY release_year DESC
    ```

2. All movies released in the year 2022:
    ```sql
    SELECT *
    FROM movies
    WHERE release_year=2022
    ```

3. All movies released after 2020:
    ```sql
    SELECT *
    FROM movies
    WHERE release_year>2020
    ```

4. All movies after the year 2020 that have more than 8 rating:
    ```sql
    SELECT *
    FROM movies
    WHERE release_year>2020 AND imdb_rating>8.0
    ```

5. Select all movies that are by Marvel Studios and Hombale Films:
    ```sql
    SELECT *
    FROM movies
    WHERE studio IN("Marvel Studios", "Hombale Films")
    ```

6. Select all THOR movies by their release year:
    ```sql
    SELECT *
    FROM movies
    WHERE title LIKE "%Thor%"
    ORDER BY release_year
    ```

7. Select all movies that are not from Marvel Studios:
    ```sql
    SELECT *
    FROM movies
    WHERE studio!="Marvel Studios"
    ```

### [Exercise_3.txt](./Exercise_3.txt)

1. How many movies were released between 2015 and 2022:
    ```sql
    SELECT COUNT(*)
    FROM movies
    WHERE release_year BETWEEN 2015 AND 2022
    ```

2. Print the max and min movie release year:
    ```sql
    SELECT MAX(release_year) as max_year,
           MIN(release_year) as min_year
    FROM movies
    ```

3. Print a year and how many movies were released in that year, starting with the latest year:
    ```sql
    SELECT release_year, COUNT(*) as Count
    FROM movies
    GROUP BY release_year
    ORDER BY release_year DESC
    ```

### [Exercise_4.txt](./Exercise_4.txt)

1. Print profit percentage for all the movies:
    ```sql
    SELECT *, (revenue-budget) as profit,
           (revenue-budget)*100/budget as profit_per
    FROM financials
    ```

### [Exercise_5.txt](./Exercise_5.txt)

1. Show all the movies with their language names:
    ```sql
    SELECT m.title, l.name
    FROM movies m
    JOIN languages l
    USING (language_id)
    ```

2. Show all Telugu movie names (assuming you don't know the language id for Telugu):
    ```sql
    SELECT title, name
    FROM movies
    LEFT JOIN languages
    USING (language_id)
    HAVING name="Telugu"
    ```

3. Show the language and number of movies released in that language:
    ```sql
    SELECT DISTINCT name, COUNT(name) as Count
    FROM movies
    LEFT JOIN languages
    USING (language_id)
    GROUP BY name
    UNION
    SELECT DISTINCT name, COUNT(name) as Count
    FROM movies
    RIGHT JOIN languages
    USING (language_id)
    GROUP BY name
    ```

### [Exercise_6.txt](./Exercise_6.txt)

1. Extract and format data to display names in the format `<Name>(<FirstLetterOfOccupation>)`, sorted alphabetically by Name:
    ```sql
    SELECT CONCAT(Name, "(", SUBSTRING(Occupation, 1, 1), ")") as result
    FROM OCCUPATIONS
    ORDER BY Name
    ```

2. Aggregate and count total number of each occupation, sorted by Count ascending and alphabetically by Occupation:
    ```sql
    SELECT Occupation, COUNT(Occupation) as COUNTS
    FROM OCCUPATIONS
    GROUP BY Occupation
    ORDER BY COUNTS ASC, Occupation ASC
    ```

3. Combine and format to display:
   - Names with their occupations' first letters.
   - Total count of each occupation in the format `There are a total of [Count] [Occupation]s.`

    ```sql
    SELECT CONCAT(Name, "(", SUBSTRING(Occupation, 1, 1), ")") as result
    FROM OCCUPATIONS
    UNION ALL
    SELECT CONCAT("There are a total of ", COUNT(Occupation), " ", LOWER(Occupation), "s.") as result
    FROM OCCUPATIONS
    GROUP BY Occupation
    ORDER BY result ASC
    ```