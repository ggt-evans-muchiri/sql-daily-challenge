# Weather Observation Station 12

- Link: https://www.hackerrank.com/challenges/weather-observation-station-12
- Difficulty: Easy

## Intuition
We need distinct city names that neither start nor end with a vowel. The first group of `NOT LIKE` conditions rules out a vowel at the beginning; the second rules one out at the end. Combining both groups with `AND` ensures each returned city meets both requirements.

## Solution
```sql
SELECT DISTINCT city
FROM station
WHERE LOWER(city) NOT LIKE 'a%'
AND LOWER(city) NOT LIKE 'e%'
AND LOWER(city) NOT LIKE 'i%'
AND LOWER(city) NOT LIKE 'o%'
AND LOWER(city) NOT LIKE 'u%'
AND LOWER(city) NOT LIKE '%a'
AND LOWER(city) NOT LIKE '%e'
AND LOWER(city) NOT LIKE '%i'
AND LOWER(city) NOT LIKE '%o'
AND LOWER(city) NOT LIKE '%u';
```
