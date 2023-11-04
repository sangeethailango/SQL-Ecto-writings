To limit the number records from being fetched, `LIMIT` command is used. 
### Example:

In the below example, The inserted records in the `countries` table are 25. 

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/91f2ca32-31bd-45cd-a0df-8ca319cb3840)

Now let's set the limit to it.

``` SQL
 SELECT * FROM countries limit 10;
```

Result:

![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/f7249fe7-ce93-4de6-8486-2e2550940dd6)

we are limiting the records to 10.


# Ecto query for  `LIMIT`

#### `limit/2` function

You can limit the records using `limit/2` function from `Ecto.Query`.

Example: 

``` Ecto
 SqlEcto.Hr.Country |> limit(2) |> SqlEcto.Repo.all() 
```

Result:
![image](https://github.com/sangeethailango/SQL-Ecto-writings/assets/78719077/d6dbe4c5-938e-4683-a155-2b6183c7ab91)



