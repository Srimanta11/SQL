## LeetCode SQL Solutions

1. [Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)
```SQL
SELECT Person.FirstName, Person.LastName, Address.City, Address.State 
from Person LEFT JOIN Address on Person.PersonId = Address.PersonId;
```

2. [Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)
```SQL
SELECT max(Salary) as SecondHighestSalary 
FROM Employee
WHERE Salary < (SELECT max(Salary) FROM Employee)
```

3. [Nth Highest Salary](https://leetcode.com/problems/nth-highest-salary/)
```SQL
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
DECLARE M INT;
SET M=N-1;
  RETURN (
       SELECT DISTINCT Salary FROM Employee ORDER BY Salary DESC LIMIT M, 1
  );
END
```


4. [Employees Earning More Than Their Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/)
```SQL
select name as Employee
from Employee as e1 
where salary > (select salary from Employee as e2 where e2.id = e1.managerId )
```

5. [Duplicate Emails](https://leetcode.com/problems/duplicate-emails/)
```SQL
select email
from Person
group by email
having count(email) > 1
```

6. [Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/)
```SQL
select name as Customers 
from Customers where id NOT in (select customerId from Orders)
```

7. [Department Highest Salary](https://leetcode.com/problems/department-highest-salary/)
```SQL
SELECT d.name AS Department, e.name AS Employee, e.salary AS Salary
FROM Employee e, Department d
WHERE e.departmentId = d.id
AND (e.departmentId, e.salary) in 
(SELECT DepartmentId, max(Salary) as max FROM Employee GROUP BY DepartmentId)
```

8. [Department Top Three Salaries](https://leetcode.com/problems/department-top-three-salaries/)
```SQL
SELECT  d.Name AS Department, e.Name AS Employee , e.Salary 
FROM Employee AS e, Employee as e1, Department AS d
WHERE e.DepartmentId = d.Id
AND e1.DepartmentId = e.DepartmentId
AND e1.Salary >= e.Salary 
GROUP BY e.Id
HAVING COUNT(DISTINCT e1.Salary) <= 3;
```

9. [Delete Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/)
```SQL
DELETE p1
FROM Person p1, Person p2
WHERE p1.Email = p2.Email AND
p1.Id > p2.Id
```

10. [Rising Temperature](https://leetcode.com/problems/rising-temperature/)
```SQL
SELECT wt1.Id 
FROM Weather wt1, Weather wt2
WHERE wt1.Temperature > wt2.Temperature AND 
TO_DAYS(wt1.recordDate)-TO_DAYS(wt2.recordDate)=1;
```

11. [Trips and Users](https://leetcode.com/problems/trips-and-users/)
```SQL
select t.Request_at Day,
       ROUND((count(IF(t.status!='completed',TRUE,null))/count(*)),2) as 'Cancellation Rate'
from Trips t where 
t.Client_Id in (Select Users_Id from Users where Banned='No') 
and t.Driver_Id in (Select Users_Id from Users where Banned='No')
and t.Request_at between '2013-10-01' and '2013-10-03'
group by t.Request_at;
```

12. [Find Customer Referee](https://leetcode.com/problems/find-customer-referee/)
```SQL
select name from customer where referee_id <> 2 OR referee_id IS NULL
```

13. [Customer Placing the Largest Number of Orders](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/)
```SQL
select customer_number from orders
group by customer_number
order by count(order_number) desc limit 1;
```

14. [Big Countries](https://leetcode.com/problems/big-countries/)
```SQL
select name, population, area from world 
where area >= 3000000 or population >= 25000000 
```

15. [Sales Person](https://leetcode.com/problems/sales-person/)
```SQL
SELECT name from salesperson
where sales_id not in 
(
    select sales_id from orders where com_id in 
	(select com_id from company where name='RED')
)
```

16. [Tree Node](https://leetcode.com/problems/tree-node/)
```SQL
SELECT id, 
IF (p_id IS NULL, "Root",
	IF (id IN (SELECT p_id FROM Tree), "Inner", "Leaf") 
) AS type
FROM Tree
```

17. [Swap Salary](https://leetcode.com/problems/swap-salary/)
```SQL
UPDATE salary SET sex = IF(sex = 'm', 'f', 'm')
```

18. [Actors and Directors Who Cooperated At Least Three Times](https://leetcode.com/problems/actors-and-directors-who-cooperated-at-least-three-times/)
```SQL
select actor_id, director_id
from ActorDirector
group by actor_id, director_id 
having count(timestamp) > 2
```

19. [Sales Analysis III](https://leetcode.com/problems/sales-analysis-iii/)
```SQL
SELECT s.product_id, product_name
FROM Sales s
LEFT JOIN Product p
ON s.product_id = p.product_id
GROUP BY s.product_id
HAVING MIN(sale_date) >= CAST('2019-01-01' AS DATE) AND
       MAX(sale_date) <= CAST('2019-03-31' AS DATE)
```

20. [Game Play Analysis I](https://leetcode.com/problems/game-play-analysis-i/)
```SQL
select player_id, min(event_date) as first_login
from activity 
group by player_id
```

. []()
```SQL
```



