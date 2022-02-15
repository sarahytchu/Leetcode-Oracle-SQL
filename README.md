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

3. [Duplicate Emails](https://leetcode.com/problems/duplicate-emails/)
```
SELECT email AS Email
FROM Person
GROUP BY email
HAVING COUNT(email)>1;
```

4. [Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/)
```
SELECT name AS Customers
FROM Customers
WHERE id NOT IN (
SELECT customerId
FROM Orders);
```
5. [Deleter Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/)
