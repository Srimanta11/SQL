# Subdomains Wise Questions

## Basic Select
- [Revising the Select Query I](https://www.hackerrank.com/challenges/revising-the-select-query/problem)
```SQL
    select * from CITY where COUNTRYCODE = 'USA' AND POPULATION > 100000;
```

- [Revising the Select Query II](https://www.hackerrank.com/challenges/revising-the-select-query-2)
```SQL
    select NAME from CITY where COUNTRYCODE = 'USA' AND POPULATION > 120000;
```

- [Select All](https://www.hackerrank.com/challenges/select-all-sql)
```SQL
    select * from CITY;
```

- [Select By ID](https://www.hackerrank.com/challenges/select-by-id)
```SQL
    select * from CITY where ID = 1661;
```

- [Japanese Cities' Attributes](https://www.hackerrank.com/challenges/japanese-cities-attributes)
```SQL
    select * from CITY where COUNTRYCODE = 'JPN';
```

- [Japanese Cities' Names](https://www.hackerrank.com/challenges/japanese-cities-name)
```SQL
    select NAME from CITY where COUNTRYCODE = 'JPN';
```

- [Weather Observation Station 1](https://www.hackerrank.com/challenges/weather-observation-station-1)
```SQL
    select CITY, STATE from STATION;
```

- [Weather Observation Station 3](https://www.hackerrank.com/challenges/weather-observation-station-3)
```SQL
    select distinct(CITY) from STATION where MOD(ID,2) = 0;
```

- [Weather Observation Station 4](https://www.hackerrank.com/challenges/weather-observation-station-4)
```SQL
    select COUNT(CITY) - COUNT(DISTINCT(CITY)) from STATION;
```

- [Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5)
```SQL
    select city, length(city) from station
    order by length(city),city asc
    limit 1;
    select city, length(city) from station
    order by length(city) desc
    limit 1;
```

- [Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6)
```SQL
    select distinct city from station 
    where left(city,1) in ('a','e','i','o','u')
```

- [Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7)
```SQL
    select distinct CITY from STATION where (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%u' OR CITY LIKE '%o');
```

- [Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8)
```SQL
    select distinct city from station 
    where left(city,1) in ('a','e','i','o','u') 
    and right(city, 1) in ('a','e','i','o','u')
```

- [Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9)
```SQL
    select distinct city from station 
    where left(city,1) NOT in ('a','e','i','o','u')
```

- [Weather Observation Station 10](https://www.hackerrank.com/challenges/weather-observation-station-10)
```SQL
    select distinct city from station where right(city, 1) NOT in ('a','e','i','o','u');
```

- [Weather Observation Station 11](https://www.hackerrank.com/challenges/weather-observation-station-11)
```SQL
    select distinct CITY from STATION where left(CITY,1) NOT IN ('a','e','i','o','u') OR right(CITY,1) NOT IN ('a','e','i','o','u');
```

- [Weather Observation Station 12](https://www.hackerrank.com/challenges/weather-observation-station-12)
```SQL
    select distinct CITY from STATION where left(CITY,1) NOT IN ('a','e','i','o','u') AND right(CITY,1) NOT IN ('a','e','i','o','u');
```

- [Higher Than 75 Marks](https://www.hackerrank.com/challenges/more-than-75-marks)
```SQL
    select name from students where marks > 75 order by substr(name,length(name)-2, 3), id;
```

- [Employee Names](https://www.hackerrank.com/challenges/name-of-employees)
```SQL
    select name from employee order by name asc;
```

- [Employee Salaries](https://www.hackerrank.com/challenges/salary-of-employees)
```SQL
    select name from employee where salary > 2000 AND months < 10 order by employee_id;
```

## Advanced Select
- [Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle)
```SQL
    SELECT CASE WHEN A + B > C AND A+C>B AND B+C>A THEN CASE WHEN A = B AND B = C THEN 'Equilateral' WHEN A = B OR B = C OR A = C THEN 'Isosceles' WHEN A != B OR B != C OR A != C THEN 'Scalene' END ELSE 'Not A Triangle' END FROM TRIANGLES;
```

- [The PADS](https://www.hackerrank.com/challenges/the-pads)
```SQL
    select concat(name,'(',substr(occupation,1,1),')') from occupations order by name;
    select concat('There are a total of ',count(*),' ',lower(occupation),'s.') from occupations group by occupation order by count(*), occupation;
```

- [Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1)
```SQL
    SELECT case
        when P IS NULL THEN CONCAT(N, ' Root')
        when N IN (SELECT DISTINCT P FROM BST) THEN CONCAT(N, ' Inner')
        ELSE CONCAT(N, ' Leaf')
        END
    FROM BST
    ORDER BY N ASC
```

## Aggregation
- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

## Basic Join
- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

## Advanced Join
- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

- []()
```SQL
```

## Alternative Queries
- [Draw The Triangle 1](https://www.hackerrank.com/challenges/draw-the-triangle-1)
```SQL
    DECLARE @i INT = 20
    WHILE (@i > 0) 
    BEGIN
    PRINT REPLICATE('* ', @i) 
    SET @i = @i - 1
    END
```

- [Draw The Triangle 2](https://www.hackerrank.com/challenges/draw-the-triangle-2)
```SQL
    DECLARE @i INT = 1
    WHILE (@i < 21) 
    BEGIN
    PRINT REPLICATE('* ', @i) 
    SET @i = @i + 1
    END
```

- [Print Prime Numbers](https://www.hackerrank.com/challenges/print-prime-numbers)
```SQL
    SELECT GROUP_CONCAT(NUMB SEPARATOR '&')
    FROM (
        SELECT @num:=@num+1 as NUMB FROM
        information_schema.tables t1,
        information_schema.tables t2,
        (SELECT @num:=1) tmp
    ) tempNum
    WHERE NUMB<=1000 AND NOT EXISTS(
        SELECT * FROM (
            SELECT @nu:=@nu+1 as NUMA FROM
                information_schema.tables t1,
                information_schema.tables t2,
                (SELECT @nu:=1) tmp1
                LIMIT 1000
            ) tatata
        WHERE FLOOR(NUMB/NUMA)=(NUMB/NUMA) AND NUMA<NUMB AND NUMA>1
    )

```
