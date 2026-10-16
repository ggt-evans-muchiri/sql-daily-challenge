# The Report

- Link: https://www.hackerrank.com/challenges/the-report
- Difficulty: Medium

## Intuition
Each student needs a grade, but the grade is defined by a marks interval rather than an exact value. The range join matches a student's `Marks` to the grade whose `Min_Mark` through `Max_Mark` contains it. Keep every matched student row; for grades below 8, replace only the displayed name with `NULL` so the student still appears. Sort by grade descending, then by the displayed `Name`: visible names order alphabetically, while the `NULL` names for lower grades tie and are ordered by marks ascending.

## Solution
```sql
SELECT
    CASE WHEN g.Grade < 8 THEN NULL ELSE s.Name END AS Name,
    g.Grade,
    s.Marks
FROM Students s
JOIN Grades g
    ON s.Marks BETWEEN g.Min_Mark AND g.Max_Mark
ORDER BY g.Grade DESC, Name ASC, s.Marks ASC;
```
