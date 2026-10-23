# More Than 75 Marks

- Link: https://www.hackerrank.com/challenges/more-than-75-marks
- Difficulty: Easy

## Intuition
We need to display the names of students whose marks are greater than 75. To sort the output in a way that matches the challenge, we sort by the last three characters of the name and then by the student ID.

## Solution
```sql
SELECT name
FROM students
WHERE marks > 75
ORDER BY SUBSTRING(name, -3) ASC, id ASC;
```
