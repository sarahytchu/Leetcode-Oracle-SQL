# Leetcode Oracle SQL

1. [Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)
<br> Left Join
```
SELECT p.firstName, p.lastName, a.city, a.state
FROM Person p
left join Address a
on p.PersonId = a.PersonId;
```

2. [Employee Earning More Than Their Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/)
<br> Self-Join
```
SELECT E.name AS Employee
FROM Employee E
WHERE E.managerId IS NOT NULL AND E.salary >
(SELECT M.salary
FROM Employee M
WHERE M.id=E.managerId);
```

3. 
