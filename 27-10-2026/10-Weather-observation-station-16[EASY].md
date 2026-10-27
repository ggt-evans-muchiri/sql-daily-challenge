# Weather Observation Station 16

- Link: https://www.hackerrank.com/challenges/weather-observation-station-16/
- Difficulty: Easy

## Intuition
Find the smallest latitude greater than the lower bound and round it to four decimal places.

## Solution
```sql
SELECT ROUND(MIN(LAT_N), 4)
FROM station
WHERE LAT_N > 38.7780;
```
