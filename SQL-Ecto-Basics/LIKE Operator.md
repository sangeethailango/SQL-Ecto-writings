
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

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/e96695e2-a49e-48ea-a496-33daf53bda3e)

``` SQL
SELECT * FROM employees WHERE first_name ILIKE 'a%';
```

Result:

![Uploading image.png…]()


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

![Uploading image.png…]()
