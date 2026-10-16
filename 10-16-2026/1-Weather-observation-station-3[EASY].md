# Weather Observation Station 3

- Link: https://www.hackerrank.com/challenges/weather-observation-station-3
- Difficulty: Easy

## Intuition
Think of this as two steps: keep only station rows with an even `ID`, then return the city names from those rows. The modulo test `id % 2 = 0` checks whether division by 2 leaves no remainder. `DISTINCT` removes repeated city names from the result; it does not change which rows pass the even-ID filter. Filter the rows first, then deduplicate the projected city values.

## Solution
```sql
SELECT DISTINCT city
FROM station
WHERE id % 2 = 0;

```
