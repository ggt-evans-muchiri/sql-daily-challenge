# Supercloud Customer

- Link: https://datalemur.com/questions/supercloud-customer
- Difficulty: Medium

## Intuition
Count the distinct product categories represented in each customer's contracts. Return customers whose category count matches the total number of distinct categories available in the products table.

## Solution
```sql
WITH supercloud_cust AS (
    SELECT
        customers.customer_id,
        COUNT(DISTINCT products.product_category) AS product_count
    FROM customer_contracts AS customers
    INNER JOIN products
        ON customers.product_id = products.product_id
    GROUP BY customers.customer_id
)

SELECT customer_id
FROM supercloud_cust
WHERE product_count = (
    SELECT COUNT(DISTINCT product_category)
    FROM products
);
```
