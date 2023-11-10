To fetch records by checking for multiple values in `WHERE` , `IN` command is used.
In `WHERE`, **Comparison operators** such as =, >= allows you to only compare with one value but `IN` allows us to check for multiple values.

For example:

``` SQL
SELECT * FROM employees WHERE job_id IN (9, 5, 6);
```

The above code will fetch `employees` records whose `job_id` is either 9 or 5 or 6.

Result:

![[Screenshot from 2023-11-04 09-59-13.png]]

You can see in the above table, that all records have `job_id` as either 9 or 5 or 6. To check records with multiple values `IN` is used. `IN` allows us to check strings also.

# Ecto query for `IN`

`in/2` is used to fetch records by checking multiple values in `where/3`.

Example:

``` Ecto
SqlEcto.Hr.Employee |> where([c], c.job_id in [9, 6, 5]) |> SqlEcto.Repo.all()
```

The above code will fetch `SqlEcto.Hr.Employee` whose `job_id` is 9 or 6 or 5.

Result:
![[Screenshot from 2023-11-04 10-26-12.png]]

You can see in the above example, that both 3 structs contains `job_id` as either 9 or 6 or 5.