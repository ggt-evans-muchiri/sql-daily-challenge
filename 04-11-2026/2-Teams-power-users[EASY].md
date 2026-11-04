# Teams Power Users

- Link: https://datalemur.com/questions/teams-power-users
- Difficulty: Easy

## Intuition
Filtering messages to August 2022 and grouping by sender gives each sender's message count. Sorting by that count in descending order puts the most active senders first, and `LIMIT 2` returns the top two.

## Solution
```sql
SELECT sender_id, COUNT(message_id) message_count
FROM messages
WHERE sent_date > '07/31/2022' AND sent_date < '09/01/2022'
GROUP BY sender_id
ORDER BY message_count DESC LIMIT 2;
```