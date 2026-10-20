# Top Competitors

- Link: https://www.hackerrank.com/challenges/top-competitors
- Difficulty: Medium

## Intuition
Join each submission to its challenge and that challenge's difficulty level. A submission earns a full score when its score equals the difficulty's maximum score. Group by hacker and count distinct challenges, since multiple full-score submissions for one challenge should count only once. Keep hackers with more than one such challenge, then sort by that count descending and hacker ID ascending.

## Solution
```sql
SELECT h.hacker_id, h.name
FROM Hackers h
JOIN Submissions s
    ON s.hacker_id = h.hacker_id
JOIN Challenges c
    ON c.challenge_id = s.challenge_id
JOIN Difficulty d
    ON d.difficulty_level = c.difficulty_level
WHERE s.score = d.score
GROUP BY h.hacker_id, h.name
HAVING COUNT(DISTINCT c.challenge_id) > 1
ORDER BY COUNT(DISTINCT c.challenge_id) DESC, h.hacker_id ASC;
```
