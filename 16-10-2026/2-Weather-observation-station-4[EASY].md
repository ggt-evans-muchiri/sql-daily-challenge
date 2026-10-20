# Weather Observation Station 4

- Link: https://www.hackerrank.com/challenges/weather-observation-station-4
- Difficulty: Easy

## Intuition
Count the city entries, then subtract the number of different city names. Each occurrence beyond a city's first occurrence contributes one to that difference. For example, `A, A, B, B, B` has 5 entries and 2 distinct names, so the result is 3 repeated entries. `COUNT(city)` counts non-`NULL` entries, while `COUNT(DISTINCT city)` counts each non-`NULL` name once.

## Solution
```sql
SELECT COUNT(city) - COUNT(DISTINCT city)
FROM station;
```
