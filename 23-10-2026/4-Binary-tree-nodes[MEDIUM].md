# Binary Tree Nodes

- Link: https://www.hackerrank.com/challenges/binary-search-tree-1
- Difficulty: Medium

## Intuition
Each node in the BST needs to be labeled as a root, inner node, or leaf based on whether it has a parent and whether it has children.

## Solution
```sql
SELECT N,
    CASE
        WHEN P IS NULL THEN 'Root'
        WHEN N IN (SELECT P FROM BST WHERE P IS NOT NULL) THEN 'Inner'
        ELSE 'Leaf'
    END
FROM BST
ORDER BY N;
```
