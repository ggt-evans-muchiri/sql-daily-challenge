# Weather Observation Station 5

- Link: https://www.hackerrank.com/challenges/weather-observation-station-5
- Difficulty: Easy

## Intuition
Find the city with the fewest characters and the city with the most. Sort by `LENGTH(city)` to find each extreme, and use `city` as the next sort key so ties choose the alphabetically first name. The two limited queries are combined with `UNION ALL` to keep both results, then sorted so the shortest city appears first.

## Solution
```sql
SELECT city, city_length
FROM (
	(SELECT city, LENGTH(city) AS city_length, 1 AS result_order
	 FROM station
	 ORDER BY LENGTH(city), city
	 LIMIT 1)
	UNION ALL
	(SELECT city, LENGTH(city) AS city_length, 2 AS result_order
	 FROM station
	 ORDER BY LENGTH(city) DESC, city
	 LIMIT 1)
) AS city_extremes
ORDER BY result_order;
```
