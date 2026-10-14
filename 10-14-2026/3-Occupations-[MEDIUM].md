# Occupations

- Link: https://www.hackerrank.com/challenges/occupations/problem
- Difficulty: Medium

## Intuition
The query first sorts the names in each occupation and assigns a row number to each one. This is done with `ROW_NUMBER()`, and `OVER()`, this tells SQL to evaluate the ranking within a window of rows.

`PARTITION BY occupation` resets the ranking for each profession, so Doctors are counted separately from Professors, Singers, and Actors. After that, a `CASE` expression turns each row into the correct column based on the occupation name.

`MAX(...)` is used because each row position should contain only one name from a given profession, while empty cells remain null. `GROUP BY rowNumber` combines rows with the same rank, and `ORDER BY rowNumber` ensures the final result is displayed from the first position to the last.

## Resources
- [SQL Window Functions | Advanced SQL | ThoughtSpot](https://www.thoughtspot.com/sql-tutorial/sql-window-functions) - BLOG
- [Window Functions in SQL - GeeksforGeeks](https://www.geeksforgeeks.org/sql/window-functions-in-sql/) - BLOG
- [SQL Window Functions | Clearly Explained | PARTITION BY, ORDER BY, ROW_NUMBER, RANK, DENSE_RANK](https://www.youtube.com/watch?v=rIcB4zMYMas&t=3s) - VIDEO

## Solution
```sql
SELECT
  MAX(CASE WHEN occupation = 'Doctor' THEN name END) AS doctor,
  MAX(CASE WHEN occupation = 'Professor' THEN name END) AS professor,
  MAX(CASE WHEN occupation = 'Singer' THEN name END) AS singer,
  MAX(CASE WHEN occupation = 'Actor' THEN name END) AS actor
FROM (
  SELECT
    name,
    occupation,
    ROW_NUMBER() OVER (PARTITION BY occupation ORDER BY name) AS rowNumber
  FROM occupations
) AS ranked_occupations
GROUP BY rowNumber
ORDER BY rowNumber;
```
