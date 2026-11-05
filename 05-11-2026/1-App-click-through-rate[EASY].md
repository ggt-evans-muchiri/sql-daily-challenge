# App Click-through Rate (CTR)

- Link: https://datalemur.com/questions/click-through-rate
- Difficulty: Easy

## Intuition
Filter events to 2022 and group them by app. For each app, divide clicks by impressions and multiply by 100 to calculate the click-through rate; round the percentage to two decimal places.

## Solution
```sql
SELECT
    app_id,
    ROUND(
        100.0 * SUM(CASE WHEN event_type = 'click' THEN 1 ELSE 0 END)
        / SUM(CASE WHEN event_type = 'impression' THEN 1 ELSE 0 END),
        2
    ) AS ctr
FROM events
WHERE timestamp >= '2022-01-01'
  AND timestamp < '2023-01-01'
GROUP BY app_id;
```