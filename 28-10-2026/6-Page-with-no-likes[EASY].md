# Page With No Likes

- Link: https://datalemur.com/questions/sql-page-with-no-likes
- Difficulty: Easy

## Intuition
Return pages that have no matching row in the likes table, and sort the page IDs in ascending order.

## Solution
```sql
SELECT page_id
FROM pages
WHERE page_id NOT IN (SELECT page_id FROM page_likes)
ORDER BY page_id ASC;
```