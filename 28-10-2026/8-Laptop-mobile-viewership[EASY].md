# Laptop vs. Mobile Viewership

- Link: https://datalemur.com/questions/laptop-mobile-viewership
- Difficulty: Easy

## Intuition
Count laptop views in the main query and count phone and tablet views in a scalar subquery to return both totals on one row.

## Solution
```sql
SELECT COUNT(*) AS laptop_views,
       (
           SELECT COUNT(*)
           FROM viewership
           WHERE device_type IN ('phone', 'tablet')
       ) AS mobile_views
FROM viewership
WHERE device_type = 'laptop';
```