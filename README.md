# Leetcode SQL

1. Combine Two Tables
```
SELECT p.firstName, p.lastName, a.city, a.state
FROM Person p
left join Address a
on p.PersonId = a.PersonId;
```
2. 
