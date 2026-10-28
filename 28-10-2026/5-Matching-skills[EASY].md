# Matching Skills

- Link: https://datalemur.com/questions/matching-skills
- Difficulty: Easy

## Intuition
Group candidates by ID, then keep only those who have all three required skills. DISTINCT prevents duplicate skill rows from affecting the count.

## Solution
```sql
SELECT candidate_id
FROM candidates
WHERE skill IN('Python', 'Tableau', 'PostgreSQL')
GROUP BY candidate_id
HAVING COUNT(DISTINCT skill) = 3
ORDER BY candidate_id;
```