# Japanese Cities Attributes

- Link: https://www.hackerrank.com/challenges/japanese-cities-names
- Difficulty: Easy

## Intuition
We need to return just the name columns for cities in Japan, so we filter the city table using a WHERE clause with countrycode = 'JPN'. This selects every record that matches the Japan country code.

## Solution
```sql
SELECT name
  FROM city
 WHERE countrycode = 'JPN';
```
