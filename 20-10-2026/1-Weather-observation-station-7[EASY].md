# Select All

- Link: https://www.hackerrank.com/challenges/weather-observation-station-7
- Difficulty: Easy

## Intuition
We want each city name that ends in a vowel. The `LIKE '%a'` pattern matches names ending in `a` (`%` stands for any preceding characters); the other `OR` conditions check for the remaining vowels. `DISTINCT` removes duplicate city names from the results.

## Solution
```sql
SELECT DISTINCT city FROM station 
WHERE city LIKE '%a' 
OR city LIKE '%e'
OR city LIKE '%i'
OR city LIKE '%o'
OR city LIKE '%u';

```
