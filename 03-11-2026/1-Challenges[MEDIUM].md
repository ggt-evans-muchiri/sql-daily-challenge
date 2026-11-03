# Challenges

- Link: https://www.hackerrank.com/challenges/challenges
- Difficulty: Medium

## Intuition
I first count the challenges created by each hacker, grouping by hacker ID and name so each hacker has one row with their total. Then I use window functions to compare those totals without collapsing the rows: `COUNT(*) OVER (PARTITION BY challenges_created)` tells me how many hackers share each count, and `MAX(challenges_created) OVER ()` gives the overall highest count on every row. This lets me keep hackers with a unique count or the maximum count, then sort by count descending and hacker ID ascending.

## Solution
```sql
WITH collective AS (
    SELECT h.hacker_id, h.name, COUNT(*) AS challenges_created
    FROM hackers h
    JOIN challenges c USING (hacker_id)
    GROUP BY h.hacker_id, h.name
),
ranked AS (
    SELECT hacker_id, name, challenges_created,
        COUNT(*) OVER (PARTITION BY challenges_created) AS frequency,
        MAX(challenges_created) OVER () AS max_challenges
    FROM collective
)

SELECT hacker_id, name, challenges_created
FROM ranked
WHERE frequency = 1 OR challenges_created = max_challenges
ORDER BY challenges_created DESC, hacker_id ASC;
```