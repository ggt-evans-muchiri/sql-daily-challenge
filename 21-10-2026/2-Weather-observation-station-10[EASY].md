# Weather Observation Station 10

- Link: https://www.hackerrank.com/challenges/weather-observation-station-10
- Difficulty: Easy

## Intuition
We need the distinct city names that do not end with a vowel. Each `NOT LIKE '%vowel'` condition excludes names ending with that vowel. Combining the conditions with `AND` ensures the name ends with none of the five vowels, and `DISTINCT` removes duplicates.

## Solution
```sql
SELECT DISTINCT city 
FROM station
WHERE city NOT LIKE '%a'
AND city NOT LIKE '%e'
AND city NOT LIKE '%i'
AND city NOT LIKE '%o'
AND city NOT LIKE '%u';
```
