# Weather Observation Station 15

- Link: https://www.hackerrank.com/challenges/weather-observation-station-15/
- Difficulty: Easy

## Intuition
Use the greatest latitude below the upper bound to identify the matching station, then round its longitude to four decimal places.

## Solution
```sql
SELECT ROUND(LONG_W, 4)
FROM station
WHERE LAT_N = (
    SELECT MAX(LAT_N) 
    FROM station 
    WHERE LAT_N <  137.2345
);
```
