# Non-Profitable Drugs

- Link: https://datalemur.com/questions/non-profitable-drugs
- Difficulty: Easy

## Intuition
Filter for drugs whose cost of goods sold exceeds their total sales, then group those losses by manufacturer. Count the affected drugs, sum the loss amounts, and sort manufacturers from the largest total loss to the smallest.

## Solution
```sql
SELECT manufacturer, 
  COUNT(drug) drug_count, 
  ABS(SUM(total_sales - cogs)) AS total_loss
FROM pharmacy_sales
WHERE (total_sales  - cogs) < 0
GROUP BY manufacturer
ORDER BY total_loss DESC;
```