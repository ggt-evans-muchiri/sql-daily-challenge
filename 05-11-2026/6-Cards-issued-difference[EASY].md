# Cards Issued Difference

- Link: https://datalemur.com/questions/cards-issued-difference
- Difficulty: Easy

## Intuition
Group monthly card issuance records by card, then subtract each card's lowest monthly issuance from its highest to find the difference. Sort the results by that difference from largest to smallest.

## Solution
```sql
SELECT card_name, 
  MAX(issued_amount) - MIN(issued_amount) difference
FROM monthly_cards_issued
GROUP BY card_name
ORDER BY difference DESC;
```