# Sign Up Confirmation Rate

- Link: https://datalemur.com/questions/signup-confirmation-rate
- Difficulty: Medium

## Intuition
Left join text actions to emails, then calculate the share of distinct users with a confirmed signup among all distinct users. Round the rate to two decimal places.

## Solution
```sql
WITH count_cte AS (
  SELECT * 
  FROM emails e
  LEFT JOIN texts t USING(email_id)
)

SELECT 
  ROUND(
      CAST((
        SELECT COUNT(DISTINCT user_id) 
        FROM count_cte WHERE signup_action = 'Confirmed'
        ) AS DECIMAL
      )/
      CAST((
        SELECT COUNT(DISTINCT user_id) 
        FROM count_cte) AS DECIMAL
      ), 2
  );
```