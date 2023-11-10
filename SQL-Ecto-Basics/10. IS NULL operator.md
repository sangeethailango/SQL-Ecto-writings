To fetch records which is having no value or null value for a column `IS NULL` is used.  `IS NULL` is used in `WHERE` command.

Example:

``` SQL
SELECT * FROM employees WHERE phone_number IS NULL;
```

The above code will fetch `employees` whose `phone_number` is null or if there is no value inserted.

Result:

![[Screenshot from 2023-11-03 15-29-43.png]]

On the above example, you can see that for all the 6 rows, there is not value inserted in `phone_number` column.

# Ecto query for `IS NULL`

In Ecto you can do it by using `is_nil/1` function in.

Example:

``` Ecto
SqlEcto.Hr.Employee |> where([c], is_nil(c.phone_number)) |> SqlEcto.Repo.all()
```

The above code will search in the `SqlEcto.Hr.Employee` struct, where `phone_number` is given as nil. 

![[Screenshot from 2023-11-03 15-48-26.png]]

Here i am limiting the records to 2, because i don't need every records to come. You can see in the above example that the both structs are having `nil` as a value for `phone_number`.
