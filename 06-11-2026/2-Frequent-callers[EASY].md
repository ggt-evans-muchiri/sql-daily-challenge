# Frequent Callers

- Link: https://datalemur.com/questions/frequent-callers
- Difficulty: Easy

## Intuition
Count calls for each policy holder, then count how many holders made at least three calls.

## Solution
```sql
SELECT COUNT(holder_count) 
FROM(
  SELECT COUNT(policy_holder_id) holder_count
  FROM callers
  GROUP BY policy_holder_id
  HAVING COUNT(policy_holder_id) >= 3
) total_count;
```