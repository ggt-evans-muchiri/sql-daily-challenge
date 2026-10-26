# What Type of Triangle

- Link: https://www.hackerrank.com/challenges/what-type-of-triangle
- Difficulty: Easy

## Intuition
First check the triangle inequality: the sum of any two sides must be greater than the third, otherwise the sides cannot form a triangle. For a valid triangle, check for three equal sides, then two equal sides; any remaining valid triangle is scalene.

## Solution
```sql
SELECT
    CASE
        WHEN A + B <= C OR B + C <= A OR C + A <= B
            THEN 'Not A Triangle'
        WHEN A = B AND B = C
            THEN 'Equilateral'
        WHEN A = B OR B = C OR C = A
            THEN 'Isosceles'
        ELSE 'Scalene'
    END
FROM triangles;
```
