# Tesla Unfinished Parts

- Link: https://datalemur.com/questions/tesla-unfinished-parts
- Difficulty: Easy

## Intuition
An unfinished part has no finish date, so filter for rows where `finish_date` is NULL and return the part and assembly step.

## Solution
```sql
SELECT part, assembly_step
FROM parts_assembly 
WHERE finish_date IS NULL;
```