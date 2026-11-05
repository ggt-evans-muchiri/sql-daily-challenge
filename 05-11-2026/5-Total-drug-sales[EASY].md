# Total Drug Sales

- Link: https://datalemur.com/questions/total-drugs-sales
- Difficulty: Easy

## Intuition
Group drug sales by manufacturer, sum each manufacturer's sales, and sort the totals from highest to lowest. Convert each total to millions and format it as a dollar amount.

## Solution
```sql
SELECT manufacturer,
  CONCAT('$', ROUND(SUM(total_sales)/1000000), ' million') sale_mil
FROM pharmacy_sales
GROUP BY manufacturer
ORDER BY SUM(total_sales) DESC;
```