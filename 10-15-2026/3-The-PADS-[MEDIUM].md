# The PADS

- Link: https://www.hackerrank.com/challenges/the-pads
- Difficulty: Medium

## Intuition
The first query appends the first letter of each occupation to the person's name and sorts the results alphabetically by name. The second groups rows by occupation, counts each group, and formats the required sentence. Sorting by count and then occupation handles ties in the count alphabetically.

## Solution
```sql
SELECT CONCAT(
    name, '(', SUBSTRING(occupation, 1, 1), ')'
    ) AS newColumn 
FROM occupations 
ORDER BY NAME ASC;

SELECT CONCAT(
    'There are a total of ', COUNT(occupation),' ', LOWER(occupation), 's.'
    ) FROM occupations 
GROUP BY occupation 
ORDER BY COUNT(occupation) ASC;
```
