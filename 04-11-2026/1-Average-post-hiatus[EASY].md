# Average Post Hiatus

- Link: https://datalemur.com/questions/sql-average-post-hiatus-1
- Difficulty: Easy

## Intuition
Filtering to 2021 and grouping by user gives each user's earliest and latest post dates. Their difference is the user's post hiatus. The `HAVING` clause keeps users with more than one post, since a single post has no interval to compare.

## Solution
```sql
SELECT 
    user_id, 
    DATEDIFF(MAX(DATE(post_date)), MIN(DATE(post_date))) AS days_between
FROM posts
WHERE YEAR(post_date) = 2021
GROUP BY user_id
HAVING COUNT(post_id) > 1;
```