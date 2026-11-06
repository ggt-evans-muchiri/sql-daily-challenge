# Alibaba Compressed Mean

- Link: https://datalemur.com/questions/alibaba-compressed-mean
- Difficulty: Easy

## Intuition
Calculate the weighted average number of items per order by multiplying each item's count by how often that order occurred, summing those values, and dividing by the total number of order occurrences. Round the result to one decimal place.

## Solution
```sql
SELECT 
ROUND(
  CAST(
    (SUM(order_occurrences * item_count) /
    SUM(order_occurrences)) AS NUMERIC
  ), 1) mean
FROM items_per_order;
```