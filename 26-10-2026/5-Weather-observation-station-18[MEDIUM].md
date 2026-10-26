# Weather Observation Station 18

- Link: https://www.hackerrank.com/challenges/weather-observation-station-18/
- Difficulty: Medium

## Intuition
Manhattan distance is the sum of the absolute differences between the latitude and longitude coordinates. The maximum-minus-minimum range gives each absolute difference, and rounding the sum to four decimal places produces the required result.

## Solution
```sql
SELECT
    ROUND(
        MAX(LAT_N) - MIN(LAT_N) + 
        MAX(LONG_W) - MIN(LONG_W)
    ,4)
FROM STATION;
```
