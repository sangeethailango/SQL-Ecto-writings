To limit the number records from being fetched, `LIMIT` command is used. 
### Example:

In the below example, The inserted records in the `countries` table are 25. 

![[Screenshot from 2023-10-31 16-37-13.png]]

Now let's set the limit to it.

``` SQL
 SELECT * FROM countries limit 10;
```

Result:

![[Screenshot from 2023-11-03 09-52-38.png]]

we are limiting the records to 10.


# Ecto query for  `LIMIT`

#### `limit/2` function

You can limit the records using `limit/2` function from `Ecto.Query`.

Example: 

``` Ecto
 SqlEcto.Hr.Country |> limit(2) |> SqlEcto.Repo.all() 
```

Result:
![[Screenshot from 2023-11-03 15-42-56-1.png]]



