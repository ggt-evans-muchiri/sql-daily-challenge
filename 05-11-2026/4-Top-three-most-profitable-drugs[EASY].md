# Top 3 Most Profitable Drugs

- Link: https://datalemur.com/questions/top-profitable-drugs
- Difficulty: Easy

## Intuition
Calculate each drug's profit by subtracting its cost of goods sold from total sales, then sort by profit in descending order and return the top three.

## Solution
```sql
SELECT drug,
  (total_sales - cogs) total_profit
FROM pharmacy_sales
ORDER BY total_profit DESC
LIMIT 3;
```