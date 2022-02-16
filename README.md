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
5. [Delete Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/)

```
DELETE p1 from Person p1
INNER JOIN Person p2
WHERE p1.id > p2.id AND p1.email = p2.email;
```
<br>
*Note:* In MySQL because no option for Oracle

6. [Rising Temperature](https://leetcode.com/problems/rising-temperature/)
```
SELECT b.id
FROM Weather a JOIN Weather b ON
a.recordDate = b.recordDate-1
WHERE b.temperature > a.temperature;
```

7. [Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)
```
SELECT MAX(salary) as SecondHighestSalary
FROM Employee
WHERE salary NOT IN (SELECT MAX(salary) FROM Employee);
```

8. [Employee Bonus](https://leetcode.com/problems/employee-bonus/)
```SELECT e.name, b.bonus
FROM Employee e
FULL OUTER JOIN Bonus b ON e.empId = b.empId
WHERE b.bonus < 1000 OR b.bonus IS NULL;
```

9. 

