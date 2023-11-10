To get only unique value from any columns in a table, `DISTINCT` is used. Using `DISTINCT` keyword, you can see all the available values that present in a particular table. 

Example:

`locations` table

![[Pasted image 20231108164532.png]]

 you can find what are all the `country_id` that present in the `locations` table. If you use distinct keyword for any column, The duplicates in that column won't get returned.  The above `locations` table have 3 `coutry_id` as `US`. But if you put `DISTINCT`  you will only get one `US`. Even if you have 10 `street_address` that have same `country_id` , `DISTINCT` will only return one. 

``` SQL
SELECT DISTINCT country_id FROM locations;
```

The above query will return all the `country_id`'s in `locations` table.

Result:

![[Pasted image 20231108165547.png]]

We have 4 `country_id` in `locations` table.

# Ecto query for `DISTINCT`

#### `distinct/3`

In Ecto, You can get all unique values in a field by using `distinct/3` function. You can see what are all the `country_id` are present in `SqlEcto.Hr.Location` by doing,

``` Ecto
SqlEcto.Hr.Location |> select([l], [l.country_id]) |> distinct(true) |> SqlEcto.Repo.all()
```

The above query will return all the unique values from `country_id` field from `SqlEcto.Hr.Location`


Result:

![[Pasted image 20231108172108.png]]

So we have totally 4 `country_id` present in `SqlEcto.Hr.Location`.