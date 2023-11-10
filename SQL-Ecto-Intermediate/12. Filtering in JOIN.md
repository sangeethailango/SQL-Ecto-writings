You can use `WHERE`, `AND` in `JOIN` to filter your table. If you want your table to return certain rows that have certain values in either of the table or both tables you can use `WHERE`, `AND`. 

### `WHERE`

Example:

`countries` table

![[Pasted image 20231109095918.png]]

`regions` table

![[Pasted image 20231109100017.png]]

Let's join these two tables, But only rows whose `region_id` is 2.

``` SQL
SELECT * FROM countries LEFT JOIN regions ON countries.region_id = regions.region_id WHERE countries.region_id = 2;
```


Result:

![[Pasted image 20231109102251.png]]

`WHERE` condition applies to the table before the table got joined. The table will return once all the rows satisfy the `WHERE` condition. 

In the above example, you can see that the two tables whose `region_id` is 2 is got returned. Other rows didn't returned. Or if you want either one of the table to return every rows and other to return rows that only satisfy the condition use `AND`.      

### `AND`

So in `AND`, The table will return first and then the condition in `AND` will get applied.

Example:

``` SQL
SELECT * FROM countries LEFT JOIN regions ON countries.region_id = regions.region_id AND countries.region_id = 2;
```

Result:

![[Pasted image 20231109102527.png]]

Here you can see that every rows from `counries` returned. But only rows that have `region_id` = 2 got returned from regions. If you every rows from `regions` should come but rows that satisfy the condition should return from `countries` you have to do `RIGHT JOIN`

![[Pasted image 20231109102812.png]]


# Ecto query to filter in `JOIN`

`WHERE/3`

``` Ecto
SqlEcto.Hr.Country|> join(:left, [p], r in SqlEcto.Hr.Region, on: p.region_id==r.region_id ) |> where([p], p.region_id==2 ) |> select([p, r], [p ,r] ) |>  SqlEcto.
Repo.all()
```

`join(:left, [p], r in SqlEcto.Hr.Region, on: p.region_id==r.region_id )` -> We are doing left join here. joining rows whose `region_id` are same.   
`where([p], p.region_id==2 )` -> only rows whose `region_id` is 2. You can also use other comparison operators here, such as !=, <, >. 

Result:

![[Pasted image 20231109104918.png]]

The image is to long, so i just pasted only 2 lists. Here you can see that all lists `region_id` is 2.


`AND`

Example:

``` Ecto
SqlEcto.Hr.Country|> join(:left, [p], r in SqlEcto.Hr.Region, on: p.region_id==r.region_id and p.region_id==2 ) |> select([p, r], [p ,r] ) |>  SqlEcto.Repo.all()  
```

The above query will return every structs from `SqlEcto.Hr.Country`. But only those satisfy the `AND` condition

Result:

![[Pasted image 20231109105607.png]]

Here you can see that those `region_id` 2 got `SqlEcto.Hr.Region` others got `nil`.


