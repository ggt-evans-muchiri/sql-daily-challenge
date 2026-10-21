# Select All

- Link: https://www.hackerrank.com/challenges/weather-observation-station-8
- Difficulty: Easy

## Intuition
We need city names that both start and end with a vowel. The first group of `LIKE 'a%'` patterns checks that the first character is one of the vowels, and the second group of `LIKE '%a'` patterns checks the last character. `OR` allows any of the five vowels at each end, while `AND` requires both checks to match. `LOWER` makes the comparisons case-insensitive, and `DISTINCT` removes duplicate city names.

## Solution
```sql
SELECT DISTINCT city 
FROM station
WHERE (LOWER(city) LIKE 'a%' 
OR LOWER(city) LIKE 'e%'
OR LOWER(city) LIKE 'i%'
OR LOWER(city) LIKE 'o%'
OR LOWER(city) LIKE 'u%')
AND (LOWER(city) LIKE '%a'
OR LOWER(city) LIKE '%e'
OR LOWER(city) LIKE '%i'
OR LOWER(city) LIKE '%o'
OR LOWER(city) LIKE '%u');
```
