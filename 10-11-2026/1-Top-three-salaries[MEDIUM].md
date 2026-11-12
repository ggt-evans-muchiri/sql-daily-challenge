# Top 3 Salaries

- Link: https://datalemur.com/questions/sql-top-three-salaries
- Difficulty: Medium

## Intuition
For each department, sort employees by salary in descending order and assign a rank. Then keep only employees whose rank is 3 or less, and display the department name alongside the employee details. This captures the highest-paid employees in each department while preserving ties by using `DENSE_RANK()`.

## Solution
```sql
WITH ranked_employee_cte AS (
  SELECT *, 
  DENSE_RANK() OVER(PARTITION BY department_id ORDER BY salary DESC) ranked
  FROM employee
)

SELECT d.department_name, re.name, re.salary
FROM ranked_employee_cte re
JOIN department d ON re.department_id = d.department_id
WHERE ranked <= 3
ORDER BY department_name ASC, salary DESC, name ASC;
```