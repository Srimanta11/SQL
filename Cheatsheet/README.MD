
## Querying data from a table

- Query data in columns c1, c2 from a table

```SQL
  SELECT c1, c2 FROM t;
```

- Query all rows and columns from a table

```SQL
  SELECT * FROM t;
```

- Query data and filter rows with a condition

```SQL
  SELECT c1, c2 FROM t
  WHERE condition;
```

- Query distinct rows from a table

```SQL
  SELECT DISTINCT c1 FROM t
  WHERE condition;
```

- Sort the result set in ascending or descending order

```SQL
  SELECT c1, c2 FROM t
  ORDER BY c1 ASC [DESC];
```

- Skip offset of rows and return the next n rows


```SQL
  SELECT c1, c2 FROM t
  ORDER BY c1 
  LIMIT n OFFSET offset;

```

- Group rows using an aggregate function

```SQL
  SELECT c1, aggregate(c2)
  FROM t
  GROUP BY c1;
```

- Filter groups using HAVING clause

```SQL
  SELECT c1, aggregate(c2)
  FROM t
  GROUP BY c1
  HAVING condition;
```

- Querying from multiple tables 
  - Inner join t1 and t2
  ```SQL
  SELECT c1, c2 
  FROM t1
  INNER JOIN t2 ON condition;
  ```

  - Left join t1 and t1
  ```SQL
  SELECT c1, c2 
  FROM t1
  LEFT JOIN t2 ON condition;
  ```

  - Right join t1 and t2
  ```SQL
  SELECT c1, c2 
  FROM t1
  RIGHT JOIN t2 ON condition;
  ```
  - Perform full outer join
  ```SQL
  SELECT c1, c2 
  FROM t1
  FULL OUTER JOIN t2 ON condition;
  ```

- Produce a Cartesian product of rows in tables
```SQL
  SELECT c1, c2 
  FROM t1
  CROSS JOIN t2;
```

- Another way to perform cross join
```SQL
  SELECT c1, c2 
  FROM t1, t2;
```

- Join t1 to itself using INNER JOIN clause
```SQL
  SELECT c1, c2
  FROM t1 A
  INNER JOIN t1 B ON condition;
```

- Using SQL Operators
  - Combine rows from two queries
  ```SQL
  SELECT c1, c2 FROM t1
  UNION [ALL]
  SELECT c1, c2 FROM t2;
  ```

  - Return the intersection of two queries

  ```SQL
  SELECT c1, c2 FROM t1
  INTERSECT
  SELECT c1, c2 FROM t2;
  ```
- Subtract a result set from another result set

SELECT c1, c2 FROM t1
MINUS
SELECT c1, c2 FROM t2;
Code language: SQL (Structured Query Language) (sql)

Query rows using pattern matching %, _

SELECT c1, c2 FROM t1
WHERE c1 [NOT] LIKE pattern;
Code language: SQL (Structured Query Language) (sql)

Query rows in a list

SELECT c1, c2 FROM t
WHERE c1 [NOT] IN value_list;
Code language: SQL (Structured Query Language) (sql)

Query rows between two values

SELECT c1, c2 FROM t
WHERE  c1 BETWEEN low AND high;
Code language: SQL (Structured Query Language) (sql)

Check if values in a table is NULL or not

SELECT c1, c2 FROM t
WHERE  c1 IS [NOT] NULL;
Code language: SQL (Structured Query Language) (sql)

Managing tables

Create a new table with three columns

CREATE TABLE t (
     id INT PRIMARY KEY,
     name VARCHAR NOT NULL,
     price INT DEFAULT 0
);
Code language: SQL (Structured Query Language) (sql)

Delete the table from the database

DROP TABLE t ;
Code language: SQL (Structured Query Language) (sql)

Add a new column to the table

ALTER TABLE t ADD column;
Code language: SQL (Structured Query Language) (sql)

Drop column c from the table

ALTER TABLE t DROP COLUMN c ;
Code language: SQL (Structured Query Language) (sql)

Add a constraint

ALTER TABLE t ADD constraint;
Code language: SQL (Structured Query Language) (sql)

Drop a constraint

ALTER TABLE t DROP constraint;
Code language: SQL (Structured Query Language) (sql)

Rename a table from t1 to t2

ALTER TABLE t1 RENAME TO t2;
Code language: SQL (Structured Query Language) (sql)

Rename column c1 to c2

ALTER TABLE t1 RENAME c1 TO c2 ;
Code language: SQL (Structured Query Language) (sql)

Remove all data in a table

TRUNCATE TABLE t;
Code language: SQL (Structured Query Language) (sql)

Using SQL constraints

Set c1 and c2 as a primary key

CREATE TABLE t(
    c1 INT, c2 INT, c3 VARCHAR,
    PRIMARY KEY (c1,c2)
);
Code language: SQL (Structured Query Language) (sql)

Set c2 column as a foreign key

CREATE TABLE t1(
    c1 INT PRIMARY KEY,  
    c2 INT,
    FOREIGN KEY (c2) REFERENCES t2(c2)
);
Code language: SQL (Structured Query Language) (sql)

Make the values in c1 and c2 unique

CREATE TABLE t(
    c1 INT, c1 INT,
    UNIQUE(c2,c3)
);
Code language: SQL (Structured Query Language) (sql)

Ensure c1 > 0 and values in c1 >= c2

CREATE TABLE t(
  c1 INT, c2 INT,
  CHECK(c1> 0 AND c1 >= c2)
);
Code language: SQL (Structured Query Language) (sql)

Set values in c2 column not NULL

CREATE TABLE t(
     c1 INT PRIMARY KEY,
     c2 VARCHAR NOT NULL
);
Code language: SQL (Structured Query Language) (sql)

Modifying Data

Insert one row into a table

INSERT INTO t(column_list)
VALUES(value_list);
Code language: SQL (Structured Query Language) (sql)

Insert multiple rows into a table

INSERT INTO t(column_list)
VALUES (value_list), 
       (value_list), …;
Code language: SQL (Structured Query Language) (sql)

Insert rows from t2 into t1

INSERT INTO t1(column_list)
SELECT column_list
FROM t2;
Code language: SQL (Structured Query Language) (sql)

Update new value in the column c1 for all rows

UPDATE t
SET c1 = new_value;
Code language: SQL (Structured Query Language) (sql)

Update values in the column c1, c2 that match the condition

UPDATE t
SET c1 = new_value, 
        c2 = new_value
WHERE condition;
Code language: SQL (Structured Query Language) (sql)

Delete all data in a table

DELETE FROM t;
Code language: SQL (Structured Query Language) (sql)

Delete subset of rows in a table

DELETE FROM t
WHERE condition;
Code language: SQL (Structured Query Language) (sql)

Managing Views

Create a new view that consists  of c1 and c2

CREATE VIEW v(c1,c2) 
AS
SELECT c1, c2
FROM t;
Code language: SQL (Structured Query Language) (sql)

Create a new view with check option

CREATE VIEW v(c1,c2) 
AS
SELECT c1, c2
FROM t;
WITH [CASCADED | LOCAL] CHECK OPTION;
Code language: SQL (Structured Query Language) (sql)

Create a recursive view

CREATE RECURSIVE VIEW v 
AS
select-statement -- anchor part
UNION [ALL]
select-statement; -- recursive part
Code language: SQL (Structured Query Language) (sql)

Create a temporary view

CREATE TEMPORARY VIEW v 
AS
SELECT c1, c2
FROM t;
Code language: SQL (Structured Query Language) (sql)

Delete a view

DROP VIEW view_name;
Code language: SQL (Structured Query Language) (sql)

Managing indexes

Create an index on c1 and c2 of the t table

CREATE INDEX idx_name 
ON t(c1,c2);
Code language: SQL (Structured Query Language) (sql)

Create a unique index on c3, c4 of the t table

CREATE UNIQUE INDEX idx_name
ON t(c3,c4)
Code language: SQL (Structured Query Language) (sql)

- Drop an index
- 
```SQL
DROP INDEX idx_name;
```

- Managing triggers
  - Create or modify a trigger

  ```SQL
  CREATE OR MODIFY TRIGGER trigger_name
  WHEN EVENT
  ON table_name TRIGGER_TYPE
  EXECUTE stored_procedure;
  ```
