# IBM DB2 Product Analytics

- Link: https://datalemur.com/questions/sql-ibm-db2-product-analytics
- Difficulty: Easy

## Intuition
Count each employee's queries during the third quarter of 2023, including employees with no queries, then group employees by their query count and count employees in each group.

## Solution
```sql
SELECT unique_queries, COUNT(employee_id) employee_count
FROM (
  SELECT e.employee_id, COUNT(q.query_id) unique_queries
  FROM employees e
  LEFT JOIN queries q ON e.employee_id = q.employee_id
  AND q.query_starttime >= '2023-07-01T00:00:00Z'
  AND q.query_starttime < '2023-10-01T00:00:00Z'
  GROUP BY e.employee_id
) t
GROUP BY unique_queries
ORDER BY unique_queries;
```