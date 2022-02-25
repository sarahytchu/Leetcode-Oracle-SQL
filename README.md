# Leetcode SQL Exercises

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

9. [Find Customer Referee](https://leetcode.com/problems/find-customer-referee/)
```
SELECT name
FROM Customer 
WHERE referee_id <> 2 OR referee_id IS NULL;
```

10. [Customer Placing the Largest Number of Orders](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/)
```
SELECT customer_number
FROM Orders
GROUP BY customer_number
ORDER BY COUNT(*) DESC
LIMIT 1;
```

11. [Big Countries](https://leetcode.com/problems/big-countries/submissions/)
```
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;
```

12. [Classes More Than 5 Students](https://leetcode.com/problems/classes-more-than-5-students/)
```
SELECT class
FROM Courses
GROUP BY class
HAVING COUNT(*) >= 5;
```

13.[Friend Requests I: Overall Acceptance Rate](https://leetcode.com/problems/friend-requests-i-overall-acceptance-rate/)
```
SELECT
ROUND (
IFNULL(
(SELECT COUNT(DISTINCT requester_id, accepter_id) FROM RequestAccepted)
/
(SELECT COUNT(DISTINCT sender_id, send_to_id) FROM FriendRequest),
0)
, 2) AS accept_rate;
```

14.[Customers Who Bought All Products](https://leetcode.com/problems/customers-who-bought-all-products/)
```
SELECT customer_id
FROM Customer 
GROUP BY customer_id
HAVING COUNT(DISTINCT product_key) = (
SELECT COUNT(DISTINCT product_key)
FROM Product );
```

15.[Managers with At Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)
```
SELECT name
FROM Employee
WHERE id IN
(SELECT managerId
FROM Employee
GROUP BY managerId
HAVING COUNT(*) >= 5);
```
