
To order records alphabetically `ORDER BY` is used. `DESC` helps in descending order and `ASC` helps in ascending order. You can order by one column and more than one column.

####  `ASC`

Example:

``` SQL
 SELECT * FROM employees ORDER BY last_name ASC;
```

We are ordering `employees` with `last_name` ordered in ascending way.

Result:


![[Screenshot from 2023-11-04 11-53-29.png]]

You can see that from the above example, that `last_name` is order in ascending order. starting from A.

#### `DESC`

Example:

``` SQL
SELECT * FROM employees ORDER BY last_name DESC;
```

`DESC` will order in descending way.

![[Screenshot from 2023-11-04 11-58-04.png]]

`last_name` is in descending order. Starting from W.


# Ecto query for `ORDER BY`

`order_by/3`

`order_by/3` function is used to order the records alphabetically.

Example:

#### `ASC`


``` Ecto
SqlEcto.Hr.Employee |> order_by(asc: :last_name) |> SqlEcto.Repo.all()
```

Result:

![[Screenshot from 2023-11-04 12-06-31.png]]

you can see that `last_name` is started from Whalen and descending to Vollman.

##### `ASC`

``` Ecto
SqlEcto.Hr.Employee |> order_by(asc: :last_name) |> SqlEcto.Repo.all()
```

Result:
![[Screenshot from 2023-11-04 12-07-57.png]]

you can see that `last_name` is started from Austin and Ascending to Baida.