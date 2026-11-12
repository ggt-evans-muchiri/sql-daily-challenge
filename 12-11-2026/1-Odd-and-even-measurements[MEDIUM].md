# Odd and Even Measurements

- Link: https://datalemur.com/questions/odd-even-measurements
- Difficulty: Medium

## Intuition
The odd/even position is based on the sequence of measurements within each day, not the measurement value itself. `ROW_NUMBER()` creates that sequence by ordering each day's measurements by `measurement_time`; partitioning by the date resets the numbering at the start of every day.

Once each row has a position, the remainder from dividing `rn` by 2 identifies its group: odd positions have a remainder of 1, and even positions have a remainder of 0. Conditional `SUM`s add each measurement to the corresponding total, and grouping by `measurement_day` returns one row per day.

## Solution
```sql
WITH numbered AS (
    SELECT
        DATE(measurement_time) AS measurement_day,
        measurement_value,
        ROW_NUMBER() OVER (
            PARTITION BY DATE(measurement_time)
            ORDER BY measurement_time
        ) AS rn
    FROM measurements
)
SELECT
    measurement_day,
    SUM(CASE WHEN rn % 2 = 1 THEN measurement_value ELSE 0 END) AS odd_sum,
    SUM(CASE WHEN rn % 2 = 0 THEN measurement_value ELSE 0 END) AS even_sum
FROM numbered
GROUP BY measurement_day
ORDER BY measurement_day;
```
