# Duplicate Job Listings

- Link: https://datalemur.com/questions/duplicate-job-listings
- Difficulty: Easy

## Intuition
A window function counts listings for each company and job title while retaining each listing's row. Filtering for counts greater than one identifies duplicate listings; counting the distinct company IDs returns the number of companies with at least one duplicate.

## Solution
```sql
WITH counted AS (
  SELECT company_id, title,
  COUNT(company_id) OVER(PARTITION BY company_id, title) AS amount
  FROM job_listings
)

SELECT COUNT(DISTINCT company_id) duplicate_companies
FROM counted
WHERE AMOUNT > 1;
```