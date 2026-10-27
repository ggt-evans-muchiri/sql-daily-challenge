# Weather Observation Station 14

- Link: https://www.hackerrank.com/challenges/weather-observation-station-14/
- Difficulty: Easy

## Intuition
Find the greatest latitude below the upper bound and round it to four decimal places.

## Solution
```sql
SELECT ROUND(MAX(LAT_N), 4)
FROM station
WHERE LAT_N < 137.2345;
```
