
`LIKE` operator is used to match string values in `WHERE`. You can fetch records which contains some particular string characters.   

Example:

``` SQL
SELECT * FROM employees WHERE first_name LIKE 'A%';
```

The above query will fetch `employees` whose `first_name` starts with the letter **A** followed by any other character or numbers. 

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/1c31b503-3df0-45a2-b2cc-1dcd8dbb0870)

##### `ILIKE`

`LIKE` is case sensitive. Meaning If you put `like A%` it will only give those records whose `first_name` starts with **A** not the small letter **a**, to avoid this use `ilike`

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/14b70969-bcc8-4511-8431-e386601591dd)

``` SQL
SELECT * FROM employees WHERE first_name ILIKE 'a%';
```

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/57f6cb02-3d5b-458c-91d6-ee9b7d5fd3ac)


# Ecto query for `like`

##### `like/2` function


In Ecto you can do it with the `like/2` function from `Ecto.Query`.

Example:

``` Ecto
SqlEcto.Hr.Employee |> where([c], like(c.first_name, "A%")) |> SqlEcto.Repo.all()
```

On the above code, `like(c.first_name, "A&")` will search for `employees` whose `first_name` starts with A followed by any characters or numbers.  

`ILIKE/2`

``` Ecto
SqlEcto.Hr.Employee |> where([c], ilike(c.first_name, "a%")) |> SqlEcto.Repo.all()
```

The above code will search for employees whose `first_name` starts with a and A. 

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/dca7830b-e083-473e-b83f-d82cee933ded)
