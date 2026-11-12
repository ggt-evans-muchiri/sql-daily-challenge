# Uncategorized Calls Percentage

- Link: https://datalemur.com/questions/uncategorized-calls-percentage
- Difficulty: Easy

## Intuition
Count all rows in the `callers` table, then count how many rows have a missing or null `call_category`. Divide the uncategorized count by the total count and multiply by 100 to get the percentage. Round to one decimal place.

## Solution
```sql
SELECT ROUND(
  100.00 * (
    CAST((
      SELECT COUNT(*)
      FROM callers
      WHERE call_category = 'n/a'
         OR call_category IS NULL
    ) AS DECIMAL) /
    CAST((
      SELECT COUNT(*)
      FROM callers
    ) AS DECIMAL)
  ),
  1
) AS uncategorized_call_pct;
```
