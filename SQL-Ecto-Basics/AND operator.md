To check for two conditions in one query in `WHERE`,  `AND` is used. In `AND` both the condition should return true.  

Example:

``` SQL
SELECT * FROM employees WHERE phone_number is null and first_name ILIKE 'J%';
```

Here we have two conditions. 

- `phone_number is null`
- `first_name ILIKE 'J%'`

We are using the `AND` operator in between the two conditions. So it will look for `employees` whose `phone_number` is nil and `first_name` starts from J or j.  And will return only records which satisfy both sides the condition.

![[Pasted image 20231104154938.png]]

You can use as many `AND` statements you want.

# Ecto query for `AND`

In Ecto, You can check for two condition with the `and/2` function

Example:

``` Ecto
SqlEcto.Hr.Employee |> where([c], is_nil(c.phone_number) and ilike(c.first_name, "J%")) |> limit(2) |> SqlEcto.Repo.all()
```

Here we have checking for two functions.

-  `is_nil(c.phone_number)` 
- `ilike(c.first_name, "J%"))`

Also we are limiting our records to 2. 

Result:

![[Screenshot from 2023-11-03 16-19-41.png]]

The above is result whose `phone_number` is nil and `first_name` starts with J or j