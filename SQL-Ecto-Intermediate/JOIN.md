To join multiple tables based on particular column `JOIN/INNER JOIN` is used. We can join tables using  the same column that the tables have. There is four types of `JOIN`. 

`INNER JOIN`
`RIGHT JOIN`
`LEFT JOIN`
`FULL OUTER JOIN`

`INNER JOIN` is the default `JOIN`. so `JOIN` and `INNER JOIN` are same. 


For example:

Example:
#####  `employees` table

![[Pasted image 20231107104248.png]]

##### `jobs` table

![[Pasted image 20231107104406.png]]

The `employees` and the `jobs` table have a common column called `job_id`. We can join these two tables and create one big table using this `job_id` column.  this `JOIN/INNER JOIN` will only return rows that matches the condition written using `ON`.

Syntax:

``` SQL
SELECT * FROM employees JOIN jobs ON employees.job_id = jobs.job_id;
```

Explanation:

`JOIN/INNER JOIN`, `ON` are used together. 

- `JOIN/INNER JOIN` is used to write what tables were going to be joined. Here we defined `employees` and `jobs` are going to be joined. 
- `ON` used to tell what columns in the tables were same. In what column these tables are related to each other. Here `employees` and `jobs` column related to each other by the column `job_id`.
- So the above line means, join `employees` and `jobs` tables which is related to each other by the column `job_id`.
- We are selecting every columns from the both tables to be appeared.

Result:

![[Pasted image 20231107110005.png]]

In the above table you can see that both `employees` and `jobs` are joined together with all the columns appeared. all columns are here because we select * every columns from both tables.

Example to select only some columns that needs to be appeared

``` SQL
SELECT employees.first_name, employees.last_name, employees.phone_number, jobs.min_salary FROM employees JOIN jobs ON employees.job_id = jobs.job_id;
```

On the above example, we are select only `first_name`  from `employees` `last_name` from `employees` , `phone_number` from `employees`, `min_salary` from `jobs`. 

Result:

![[Pasted image 20231107110508.png]]


# Ecto query for `JOIN` 

`join/5` is used to do all joins.

Official document for `join/5` function:  https://hexdocs.pm/ecto/Ecto.Query.html#join/5

It will accept 4 arguments. 

in expression,

1. A schema
2. `join` type. :inner, :right, :left, :full,...
3. A variable to refer to the already mentioned schema
4. A variable to refer to second schema
5.  `on` to refer to column name that matches both the table

Example:

```Ecto

```


