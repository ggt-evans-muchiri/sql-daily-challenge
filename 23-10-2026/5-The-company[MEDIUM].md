# The Company

- Link: https://www.hackerrank.com/challenges/the-company
- Difficulty: Medium

## Intuition
We need to count the number of distinct lead managers, senior managers, managers, and employees for each company, grouped by company code and founder.

## Solution
```sql
SELECT e.company_code, c.founder,
    COUNT(DISTINCT lm.lead_manager_code),
    COUNT(DISTINCT sm.senior_manager_code),
    COUNT(DISTINCT m.manager_code),
    COUNT(DISTINCT e.employee_code)
FROM employee e
JOIN company c ON c.company_code = e.company_code
JOIN lead_manager lm ON c.company_code = lm.company_code
JOIN senior_manager sm ON c.company_code = sm.company_code
JOIN manager m ON c.company_code = m.company_code
GROUP BY e.company_code, c.founder
ORDER BY e.company_code ASC;
```
