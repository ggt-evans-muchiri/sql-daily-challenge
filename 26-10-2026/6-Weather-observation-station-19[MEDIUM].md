# Weather Observation Station 19

- Link: https://www.hackerrank.com/challenges/weather-observation-station-19/
- Difficulty: Medium

## Intuition
Euclidean distance is the square root of the sum of the squared differences in latitude and longitude. The maximum-minus-minimum ranges give the coordinate differences; round the resulting distance to four decimal places.

## Solution
```sql
SELECT 
    ROUND(
        SQRT(
            POWER(MAX(LAT_N)-MIN(LAT_N),2)+ 
            POWER(MAX(LONG_W)-MIN(LONG_W),2))
        ,4) 
FROM STATION;
```
