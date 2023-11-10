To check either one of the condition in `WHERE`, `OR` is used. In `OR` either one can be true or both. it is used in `where`.

Example:

``` SQL
SELECT * FROM employees WHERE phone_number IS NULL OR first_name ILIKE 'A%';
```

Here we have two conditions. 

- `phone_number is null`
- `first_name ILIKE 'A%'`

The above code will return those records which satisfy either one of the above condition. It works same as `AND` but `OR` is checking for either one of the condition to be true.

Result:

![[Screenshot from 2023-11-03 16-28-18.png]]

The first 3 records satisfy ` first_name ILIKE 'A%'` this condition. The next 6 rows satisfy `phone_number is null` condition.  So each records satisfy either of the condition.

# Ecto query for  `OR`

`or/2` function

In Ecto you can check for the records which satisfy either one of the condition by using `or/2` function.

Example:

``` Ecto.Query
SqlEcto.Hr.Employee |> where([c], is_nil(c.phone_number) or ilike(c.email, "bruce.ernst@sqltutorial.org")) |> SqlEcto.Repo.all()
```

Here we have checking for two functions.

- `is_nil(c.phone_number)` 
- `ilike(c.email, "bruce.ernst@sqltutorial.org"))`

Result:

![[Screenshot from 2023-11-03 16-45-55.png]]

In the above example, The first struct's email is  `bruce.ernst@sqltutorial.org` So it satisfying the `ilike(c.email, "bruce.ernst@sqltutorial.org"))` condition.
The second struct `phone_number` is nil so it is satisfying the `is_nil(c.phone_number)`  condition.