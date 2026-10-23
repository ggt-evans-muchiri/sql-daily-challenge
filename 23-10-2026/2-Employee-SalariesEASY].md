# Employee Salaries

- Link: https://www.hackerrank.com/challenges/salary-of-employees
- Difficulty: Easy

## Intuition
We need employees whose salary is greater than 2000 and who have been employed for fewer than 10 months. Sorting by employee ID keeps the result consistent with the challenge requirement.

## Solution
```sql
SELECT name
FROM employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id ASC;
```
