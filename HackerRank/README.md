# HackerRank SQL Solutions

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
- [Revising Aggregations - The Count Function](https://www.hackerrank.com/challenges/revising-aggregations-the-count-function)
```SQL
    select COUNT(ID) from CITY where POPULATION > 100000;
```

- [Revising Aggregations - The Sum Function](https://www.hackerrank.com/challenges/revising-aggregations-sum)
```SQL
    select SUM(POPULATION) from CITY where DISTRICT = 'California';
```

- [Revising Aggregations - Averages](https://www.hackerrank.com/challenges/revising-aggregations-the-average-function)
```SQL
    select AVG(POPULATION) from CITY where DISTRICT = 'California';
```

- [Average Population](https://www.hackerrank.com/challenges/average-population)
```SQL
    select FLOOR(AVG(POPULATION)) from CITY;
```

- [Japan Population](https://www.hackerrank.com/challenges/japan-population/problem)
```SQL
    select SUM(POPULATION) from CITY where countrycode='JPN';
```

- [Population Density Difference](https://www.hackerrank.com/challenges/population-density-difference/problem)
```SQL
    select max(population) - min(population) from CITY;
```

- [The Blunder](https://www.hackerrank.com/challenges/the-blunder/problem)
```SQL
    SELECT CEIL(AVG(Salary)-AVG(REPLACE(Salary,'0',''))) FROM EMPLOYEES;
```

- [Top Earners](https://www.hackerrank.com/challenges/earnings-of-employees/problem)
```SQL
    select months*salary as earn, count(*)from employee group by earn order by earn desc limit 1;
```

- [Weather Observation Station 2](https://www.hackerrank.com/challenges/weather-observation-station-2)
```SQL
    select round(sum(lat_n),2), round(sum(long_w),2) from station;
```

- [Weather Observation Station 13](https://www.hackerrank.com/challenges/weather-observation-station-13)
```SQL
    select round(sum(lat_n),4) from station where lat_n > 38.7880 AND lat_n < 137.2345;
```

- [Weather Observation Station 14](https://www.hackerrank.com/challenges/weather-observation-station-14)
```SQL
    select round(max(lat_n),4) from station where lat_n < 137.2345;
```

- [Weather Observation Station 15](https://www.hackerrank.com/challenges/weather-observation-station-15)
```SQL
    select round(long_w,4) from station where lat_n=(select max(lat_n) from station where lat_n < 137.2345);
```

- [Weather Observation Station 16](https://www.hackerrank.com/challenges/weather-observation-station-16)
```SQL
    select min(round(lat_n,4)) from station where lat_n > 38.7780;
```

- [Weather Observation Station 17](https://www.hackerrank.com/challenges/weather-observation-station-17)
```SQL
    select round(long_w,4) from station where lat_n=(select min(lat_n) from station where lat_n > 38.7780);
```

- [Weather Observation Station 18](https://www.hackerrank.com/challenges/weather-observation-station-18)
```SQL
    SELECT ROUND( MAX(lat_n)-MIN(lat_n) + MAX(long_w)-MIN(long_w), 4) FROM Station;
```

- [Weather Observation Station 19](https://www.hackerrank.com/challenges/weather-observation-station-19)
```SQL
    SELECT ROUND(
    SQRT(
        POWER((MAX(lat_n)-MIN(lat_n)), 2)
        + POWER((MAX(long_w)-MIN(long_w)), 2)
        ),
    4) FROM Station;
```

- [Weather Observation Station 20](https://www.hackerrank.com/challenges/weather-observation-station-20)
```SQL
    select round(s.lat_n, 4) from station s where (select count(lat_n) from station where s.lat_n > lat_n ) = (select count(lat_n) from station where s.lat_n < lat_n ); 
```

## Basic Join
- [Population Census](https://www.hackerrank.com/challenges/asian-population)
```SQL
    select sum(c.population) from city c, country d where c.countrycode = d.code AND d.continent ='Asia';
```

- [African Cities](https://www.hackerrank.com/challenges/african-cities)
```SQL
    select c.name from city c, country d where c.countrycode = d.code AND d.continent ='Africa';
```

- [Average Population of Each Continent](https://www.hackerrank.com/challenges/average-population-of-each-continent)
```SQL
    select d.continent, floor(avg(c.population)) from city c, country d where c.countrycode = d.code group by d.continent;
```

- [The Report](https://www.hackerrank.com/challenges/the-report)
```SQL
    select if(g.grade<8, 'NULL', s.name), g.grade, s.marks from students as s, grades as g where s.marks between g.min_mark and g.max_mark order by g.grade desc, s.name; 
```

- [Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard)
```SQL
    select h.hacker_id, name, sum(score) as total_score
    from
    hackers as h inner join
    (select hacker_id,  max(score) as score from submissions group by challenge_id, hacker_id) max_score
    on h.hacker_id=max_score.hacker_id
    group by h.hacker_id, name
    having total_score > 0
    order by total_score desc, h.hacker_id;
```

## Advanced Join
- [Interviews](https://www.hackerrank.com/challenges/interviews/problem)
```SQL
    select con.contest_id,
            con.hacker_id, 
            con.name, 
            sum(total_submissions), 
            sum(total_accepted_submissions), 
            sum(total_views), sum(total_unique_views)
    from contests con 
    join colleges col on con.contest_id = col.contest_id 
    join challenges cha on  col.college_id = cha.college_id 
    left join
    (select challenge_id, sum(total_views) as total_views, sum(total_unique_views) as total_unique_views
    from view_stats group by challenge_id) vs on cha.challenge_id = vs.challenge_id 
    left join
    (select challenge_id, sum(total_submissions) as total_submissions, sum(total_accepted_submissions) as total_accepted_submissions from submission_stats group by challenge_id) ss on cha.challenge_id = ss.challenge_id
        group by con.contest_id, con.hacker_id, con.name
        having sum(total_submissions)!=0 or 
                sum(total_accepted_submissions)!=0 or
                sum(total_views)!=0 or
                sum(total_unique_views)!=0
        order by contest_id;
```

- [15 Days of Learning SQL](https://www.hackerrank.com/challenges/15-days-of-learning-sql/problem)
```SQL
    select 
    submission_date ,

    ( SELECT COUNT(distinct hacker_id)  
    FROM Submissions s2  
    WHERE s2.submission_date = s1.submission_date AND    (SELECT COUNT(distinct s3.submission_date) FROM      Submissions s3 WHERE s3.hacker_id = s2.hacker_id AND s3.submission_date < s1.submission_date) = dateDIFF(s1.submission_date , '2016-03-01')) ,

    (select hacker_id  from submissions s2 where s2.submission_date = s1.submission_date 
    group by hacker_id order by count(submission_id) desc , hacker_id limit 1) as shit,
    (select name from hackers where hacker_id = shit)
    from 
    (select distinct submission_date from submissions) s1
    group by submission_date
```

- [SQL Project Planning](https://www.hackerrank.com/challenges/sql-projects/problem)
```SQL
    
    SET sql_mode = '';
    SELECT Start_Date, End_Date
    FROM 
        (SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) a,
        (SELECT End_Date FROM Projects WHERE End_Date NOT IN (SELECT Start_Date FROM Projects)) b 
    WHERE Start_Date < End_Date
    GROUP BY Start_Date 
    ORDER BY DATEDIFF(End_Date, Start_Date), Start_Date

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
