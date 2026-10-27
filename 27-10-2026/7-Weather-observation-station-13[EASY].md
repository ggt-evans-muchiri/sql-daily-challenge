# Weather Observation Station 13

- Link: https://www.hackerrank.com/challenges/weather-observation-station-13
- Difficulty: Easy

## Intuition
Sum latitudes that fall strictly between the specified bounds and round the result to four decimal places.

## Solution
```sql
SELECT ROUND(SUM(LAT_N), 4)
FROM station
WHERE LAT_N > 38.7880 AND LAT_N < 137.2345;
```
