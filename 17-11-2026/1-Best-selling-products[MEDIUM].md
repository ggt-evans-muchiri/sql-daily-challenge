# Best Selling Products

- Link: https://datalemur.com/questions/best-selling-products
- Difficulty: Medium

## Intuition
Rank products within each category by sales quantity, using rating to break ties. Select the top-ranked product from each category.

## Solution
```sql
WITH product_sales_cte AS (
  SELECT *,
  ROW_NUMBER() OVER(
    PARTITION BY p.category_name 
    ORDER BY ps.sales_quantity DESC, ps.rating DESC
  ) ranked
  FROM products p
  JOIN product_sales ps USING(product_id)
)

SELECT category_name, product_name
FROM product_sales_cte
WHERE ranked = 1
ORDER BY category_name, product_name;
```
