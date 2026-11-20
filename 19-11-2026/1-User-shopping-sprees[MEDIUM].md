# User Shopping Sprees

- Link: https://datalemur.com/questions/amazon-shopping-spree
- Difficulty: Medium

## Intuition
Match each transaction to transactions by the same user on the next two calendar days. Selecting distinct user IDs returns users with at least one three-day shopping spree, even if they have multiple qualifying date ranges.

## Solution
```sql
SELECT DISTINCT t1.user_id
FROM transactions AS t1
JOIN transactions AS t2
    ON t2.user_id = t1.user_id
    AND DATE(t2.transaction_date) = DATE(t1.transaction_date) + 1
JOIN transactions AS t3
    ON t3.user_id = t1.user_id
    AND DATE(t3.transaction_date) = DATE(t1.transaction_date) + 2
ORDER BY t1.user_id;
```
