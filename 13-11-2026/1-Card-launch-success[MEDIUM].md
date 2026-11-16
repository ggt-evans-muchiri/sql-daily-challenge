# Card Launch Success

- Link: https://datalemur.com/questions/card-launch-success
- Difficulty: Medium

## Intuition
Rank each card's monthly records from earliest to latest, then select the first record for each card. This gives the number of cards issued during its launch month.

## Solution
```sql
WITH ranked_cards_cte AS (
    SELECT *,
           ROW_NUMBER() OVER (
               PARTITION BY card_name
               ORDER BY issue_year, issue_month
           ) AS ranked
    FROM monthly_cards_issued
)
SELECT card_name, issued_amount
FROM ranked_cards_cte
WHERE ranked = 1
ORDER BY issued_amount DESC;
```
