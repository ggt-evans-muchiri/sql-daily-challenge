# Histogram of Tweets

- Link: https://datalemur.com/questions/sql-histogram-tweets
- Difficulty: Easy

## Intuition
Count each user's tweets from 2022 to get their tweet-count bucket, then count how many users fall into each bucket.

## Solution
```sql
SELECT tweet_bucket, COUNT(user_id)
FROM (
  SELECT COUNT(tweet_id) tweet_bucket, user_id
  FROM tweets
  WHERE tweet_date LIKE '%2022%'
  GROUP BY user_id
) tweet_count 
GROUP BY tweet_bucket;
```