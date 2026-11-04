# Average Review Ratings

- Link: https://datalemur.com/questions/sql-avg-review-ratings
- Difficulty: Easy

## Intuition
Grouping reviews by product and submission month makes it possible to average the star ratings for each product-month pair. Rounding to two decimal places gives a concise monthly rating, and ordering by month and product keeps the results easy to scan.

## Solution
```sql
SELECT 
  EXTRACT(MONTH from submit_date) mnth, 
  product_id product,
  ROUND(AVG(stars),2) avg_stars
FROM reviews
GROUP BY product_id, mnth
ORDER BY mnth, product;
```