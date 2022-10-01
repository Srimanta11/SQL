This function, dense_rank(), will rank every row in a partition with no gaps. In essence, the ranks are given in a sequential order.
```SQL
SELECT student_name, total_marks, dense_rank() 
OVER ( order by total_marks desc ) 
AS 'dense_rank' FROM school_result;

```

Within a partition with gaps, function rank() will rank each row. In this case, ranks are given out in a random order.
```SQL
SELECT student_name, total_marks, rank() 
OVER ( order by total_marks desc ) 
AS 'rank' FROM school_result;
```
