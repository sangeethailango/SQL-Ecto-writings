To exclude some values from the records, `NOT` is used. 

Example:

``` SQL
SELECT * FROM employees WHERE job_id = 5 AND NOT salary < 9000 ;
```

The above query will fetch `employes` whose `job_id` is 5 but salary is not < 9000.
So all `job_id = 5` ,  `employees` with more than 9000 will get listed. 

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/29b561cf-c535-4e70-a2a9-45ac8bf7a6e5)
You can see in the above example that we have only 2 `employees` with `job_id` 5 and more than 9000 salary.

Using not and <, < is no use.

``` SQL
SELECT * FROM employees WHERE NOT salary > 9000 ;
```

instead of writing it like the above, you could write as

``` SQL
SELECT * FROM employees WHERE salary < 9000 ;
```


# Ecto query for `NOT`

`not/1` function

In Ecto, `not/1` is used to exclude values inside `where/3`.

Example:

``` Ecto
SqlEcto.Hr.Employee |> where([c], c.job_id == 5 and not(c.salary<9000) ) |> SqlEcto.Repo.all()
```

the above code will fetch `SqlEcto.Hr.Employee` whose `job_id` is 5 and salary is not  < 9000.

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/6a93dd22-56db-4fee-91b5-6b8579199478)
