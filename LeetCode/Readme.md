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

. []()
```SQL
```
