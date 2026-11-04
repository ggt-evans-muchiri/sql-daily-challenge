# Final Account Balance

- Link: https://datalemur.com/questions/final-account-balance
- Difficulty: Easy

## Intuition
For each account, calculate the total deposits and subtract the total withdrawals to get its final balance. The correlated subqueries restrict each sum to the current account and transaction type.

## Solution
```sql
SELECT account_id,
  (
    SELECT SUM(amount) 
    FROM transactions
    WHERE transaction_type = 'Deposit' 
    AND account_id = t1.account_id
  ) -
  (
    SELECT SUM(amount) 
    FROM transactions
    WHERE transaction_type = 'Withdrawal' 
    AND account_id = t1.account_id
  ) final_balance
FROM transactions t1
GROUP BY account_id;

```