# Second Highest Salary

- Link: https://datalemur.com/questions/sql-second-highest-salary
- Difficulty: Medium

## Intuition
Remove duplicate salaries, rank the remaining distinct values from highest to lowest, and select the salary in second place.

## Solution
```sql
SELECT salary second_highest_salary
FROM (
  SELECT DISTINCT salary,
   ROW_NUMBER() OVER(ORDER BY salary DESC) position
  FROM employee
) ranked
WHERE position = 2;
```