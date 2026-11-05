# Third Transaction

- Link: https://datalemur.com/questions/sql-third-transaction
- Difficulty: Medium

## Intuition
Assign each transaction a row number within its user's rows and keep row number three. Because the window has no `ORDER BY`, the query does not guarantee which transaction is considered third.

## Solution
```sql
SELECT user_id, spend, transaction_date
FROM 
  (
    SELECT user_id, spend, transaction_date,
    ROW_NUMBER() OVER(PARTITION BY user_id) rowNumber
    FROM transactions
  ) ranked
WHERE rowNumber = 3;
```