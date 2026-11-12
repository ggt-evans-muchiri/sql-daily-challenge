# Top 2 Products by Sales

- Link: https://datalemur.com/questions/sql-highest-grossing
- Difficulty: Medium

## Intuition
First sum each product's spend in 2022, grouped by category and product. Then rank products within each category by total spend and return the top two.

## Solution
```sql
WITH product_totals AS (
    SELECT category,
           product,
           SUM(spend) AS total_spend
    FROM product_spend
    WHERE transaction_date >= '2022-01-01'
      AND transaction_date < '2023-01-01'
    GROUP BY category, product
),
ranked_products AS (
    SELECT *,
           ROW_NUMBER() OVER(
               PARTITION BY category
               ORDER BY total_spend DESC
           ) AS ranked
    FROM product_totals
)
SELECT category,
       product,
       total_spend
FROM ranked_products
WHERE ranked <= 2;
```