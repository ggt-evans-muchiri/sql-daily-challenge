# Final Account Balance

- Link: https://datalemur.com/questions/final-account-balance
- Difficulty: Easy

## Intuition
Group transactions by account, then use conditional aggregation to sum deposits and withdrawals separately. Subtracting the withdrawal total from the deposit total gives each account's final balance.

## Solution
```sql
-- SELECT account_id,
--   (
--     SELECT SUM(amount) 
--     FROM transactions
--     WHERE transaction_type = 'Deposit' 
--     AND account_id = t1.account_id
--   ) -
--   (
--     SELECT SUM(amount) 
--     FROM transactions
--     WHERE transaction_type = 'Withdrawal' 
--     AND account_id = t1.account_id
--   ) final_balance
-- FROM transactions t1
-- GROUP BY account_id;

SELECT
    account_id,
    SUM(CASE WHEN transaction_type = 'Deposit' THEN amount ELSE 0 END)
    -
    SUM(CASE WHEN transaction_type = 'Withdrawal' THEN amount ELSE 0 END)
    AS final_balance
FROM transactions
GROUP BY account_id;

```