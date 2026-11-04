# Top Three Cities by Completed Trades

- Link: https://datalemur.com/questions/completed-trades
- Difficulty: Easy

## Intuition
Joining users to their trades makes each trade's city available. Filtering to completed trades, grouping by city, and counting orders gives the completed-trade total per city. Sorting by that count and limiting the output returns the top three cities.

## Solution
```sql
SELECT u.city, COUNT(t.order_id) total_orders
FROM users u
JOIN trades t ON t.user_id = u.user_id
WHERE t.status = 'Completed'
GROUP BY u.city
ORDER BY total_orders DESC LIMIT 3;
```