# International Call Percentage

- Link: https://datalemur.com/questions/international-call-percentage
- Difficulty: Medium

## Intuition
Join each call to the caller's and receiver's country. Count the calls where those countries differ, divide by the total number of calls, and round the percentage to one decimal place.

## Solution
```sql
SELECT ROUND(
    100.0 * SUM(
        CASE
            WHEN caller_info.country_id <> receiver_info.country_id THEN 1
            ELSE 0
        END
    ) / COUNT(*),
    1
) AS international_calls_pct
FROM phone_calls pc
JOIN phone_info caller_info
    ON pc.caller_id = caller_info.caller_id
JOIN phone_info receiver_info
    ON pc.receiver_id = receiver_info.caller_id;
```
