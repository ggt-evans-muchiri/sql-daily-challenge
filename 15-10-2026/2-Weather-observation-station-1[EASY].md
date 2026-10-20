# Japanese Cities Attributes

- Link: https://www.hackerrank.com/challenges/weather-observation-station-1
- Difficulty: Easy

## Intuition
We need to return all columns for cities in Japan, so we filter the city table using a WHERE clause with countrycode = 'JPN'. This selects every record that matches the Japan country code.

## Solution
```sql
SELECT city,
       state
  FROM station;
```
