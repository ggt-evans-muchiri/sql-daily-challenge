# Time Spent on Snapchat

- Link: https://datalemur.com/questions/time-spent-snaps
- Difficulty: Medium

## Intuition
Join activities with users' age groups, then calculate each age group's percentage of time spent sending and opening snaps out of the total time spent on both activities. Round each percentage to two decimal places.

## Solution
```sql
SELECT age_bucket,
  ROUND(
    100.0 * (SUM(a.time_spent) FILTER (WHERE activity_type = 'send')/
    (SUM(a.time_spent) FILTER (WHERE activity_type = 'open') + 
    SUM(a.time_spent) FILTER (WHERE activity_type = 'send')))
  , 2) send_perc,
  ROUND(
    100.0 * (SUM(a.time_spent) FILTER (WHERE activity_type = 'open')/
    (SUM(a.time_spent) FILTER (WHERE activity_type = 'open') + 
    SUM(a.time_spent) FILTER (WHERE activity_type = 'send')))
  , 2) open_perc
FROM activities a
JOIN age_breakdown ag 
ON a.user_id = ag.user_id
GROUP BY ag.age_bucket; 
```