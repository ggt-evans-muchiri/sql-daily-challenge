# Well Paid Employees

- Link: https://datalemur.com/questions/sql-well-paid-employees
- Difficulty: Easy

## Intuition
A self-join matches each employee with their manager through the manager ID. Comparing their salaries filters the results to employees who earn more than their manager.

## Solution
```sql
SELECT e1.employee_id, e1.name employee_name
FROM employee e1
JOIN employee e2 ON e1.manager_id = e2.employee_id
WHERE e1.salary > e2.salary;
```