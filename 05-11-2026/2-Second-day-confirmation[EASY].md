# Second Day Confirmation

- Link: https://datalemur.com/questions/second-day-confirmation
- Difficulty: Easy

## Intuition
Join emails to texts using the email ID, then group the records by user. Keep users with multiple actions whose earliest and latest action dates are exactly one day apart.

## Solution
```sql
SELECT e.user_id
FROM emails e
JOIN texts t ON e.email_id = t.email_id
GROUP BY e.user_id
HAVING COUNT(action_date) > 1 
AND DATEDIFF(MAX(action_date), MIN(action_date)) = 1;
```