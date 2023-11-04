
To order records alphabetically `ORDER BY` is used. `DESC` helps in descending order and `ASC` helps in ascending order. You can order by one column and more than one column.

####  `ASC`

Example:

``` SQL
 SELECT * FROM employees ORDER BY last_name ASC;
```

We are ordering `employees` with `last_name` ordered in ascending way.

Result:


![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/df557a87-e9d0-4d02-b529-1d4196d47ebb)

You can see that from the above example, that `last_name` is order in ascending order. starting from A.

#### `DESC`

Example:

``` SQL
SELECT * FROM employees ORDER BY last_name DESC;
```

`DESC` will order in descending way.

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/a85c07bf-cf21-4de0-b244-bdb2f5885494)

`last_name` is in descending order. Starting from W.


# Ecto query for `ORDER BY`

`order_by/3`

`order_by/3` function is used to order the records alphabetically.

Example:

#### `DESC`


``` Ecto
SqlEcto.Hr.Employee |> order_by(asc: :last_name) |> SqlEcto.Repo.all()
```

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/6c3c5b66-3cbb-4155-8f50-679ac76224fd)

you can see that `last_name` is started from Whalen and descending to Vollman.

##### `ASC`

``` Ecto
SqlEcto.Hr.Employee |> order_by(asc: :last_name) |> SqlEcto.Repo.all()
```

Result:
![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/e4077fec-83c8-4a50-b800-1dea709bf228)

you can see that `last_name` is started from Austin and Ascending to Baida.
