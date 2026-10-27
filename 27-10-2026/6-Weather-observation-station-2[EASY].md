# Weather Observation Station 2

- Link: https://www.hackerrank.com/challenges/weather-observation-station-2/
- Difficulty: Easy

## Intuition
Sum the latitude and longitude values separately and round each total to two decimal places.

## Solution
```sql
SELECT ROUND(SUM(LAT_N), 2), ROUND(SUM(LONG_W), 2)
FROM station;
```
