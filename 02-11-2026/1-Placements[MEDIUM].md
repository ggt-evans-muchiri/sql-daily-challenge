# Placements

- Link: https://www.hackerrank.com/challenges/placements
- Difficulty: Medium

## Intuition
Join each student to their friend and both students' salary records. Keep students whose friend earns more, then order the results by the friend's salary.

## Solution
```sql
SELECT s.name, p1.salary, p2.salary
FROM students s
JOIN friends f ON s.id = f.id
JOIN packages p1 ON s.id = p1.id
JOIN packages p2 ON f.friend_id = p2.id
WHERE p1.salary < p2.salary
ORDER BY p2.salary;
```