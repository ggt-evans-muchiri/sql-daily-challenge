# Weather Observation Station 20

- Link: https://www.hackerrank.com/challenges/weather-observation-station-20/
- Difficulty: Medium

## Intuition
Sort the latitudes and assign each row a position. For this odd-sized dataset, the median is the latitude at position CEIL(row count / 2); round that value to four decimal places.

## Solution
```sql
SELECT ROUND(LAT_N, 4)
FROM (
    SELECT LAT_N,
           ROW_NUMBER() OVER (ORDER BY LAT_N) AS rn
    FROM station
) x
WHERE rn = (
    SELECT CEIL(COUNT(*) / 2)
    FROM station
);
```