To find out how many columns have same values, to know the count, `GROUP BY` command is used. Group by has to be used, using aggregate functions such as `count`, `sum`, `max`, `min`, `avg`. 

Example:

![[Pasted image 20231106164959.png]]

if you wanted to know how many records have same value in `salary`, you can use group by.

``` SQL
SELECT salary, COUNT(salary) FROM employees GROUP BY salary;
```

Explanation:

- we are selecting `salary` to be appeared in the table. 
- we are counting the `salary` how many values are in the salary table.
- we are grouping the records by salary. Meaning all records whose value in `salary` will get grouped.
-  `salary` will get grouped, the `count(salary)` will count the grouped column. like if 3 columns were grouped together the `count(salary)` will count it as 3.

You have to print the columns which you are trying to group by. For example, if your trying to group by salary, you have to print that. if you try to print column which doesn't have any same values you will get an error. 

![[Pasted image 20231106170049.png]]

You can see in the above example, that i am grouping by `salary` with counting the `job_id` column. which means it will group the `salary` and count the grouped salary's `job_id`. But error is coming because i am trying to print the `job_id` which is a count. 
You apply aggregate function for any column. But for printing, The column which you put after `group by` and the column which got printed has to be the same column. 

![[Pasted image 20231106174858.png]]

You can see in the above example, after changing the query to

``` SQL
SELECT salary, COUNT(job_id) FROM employees GROUP BY salary;
```

It is working, so the column which you try to print has to be the column which you try to do `group by`. You can `count` any column. `count` will just count the column, so that we can have a count of how many column is got grouped by.


# Ecto query for `GROUP BY`

##### `group_by/3`





























