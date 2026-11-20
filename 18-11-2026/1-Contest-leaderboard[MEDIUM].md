# Contest Leaderboard

- Link: https://www.hackerrank.com/challenges/contest-leaderboard
- Difficulty: Medium

## Intuition
For each hacker and challenge, keep only their highest submission score. Then sum those per-challenge scores for each hacker, exclude hackers with a total score of zero, and sort by total score descending with hacker ID ascending to break ties.

## Solution
```sql
WITH cte AS (
    SELECT
        h.hacker_id AS id,
        h.name AS name,
        s.challenge_id AS hacker_challenge_id,
        MAX(s.score) AS max_score
    FROM Hackers AS h
    JOIN Submissions AS s
        ON s.hacker_id = h.hacker_id
    GROUP BY h.hacker_id, h.name, s.challenge_id
),
cte2 AS (
    SELECT id, name, SUM(max_score) AS total_score
    FROM cte
    GROUP BY id, name
)

SELECT id, name, total_score
FROM cte2
WHERE total_score > 0
ORDER BY total_score DESC, id;
```
