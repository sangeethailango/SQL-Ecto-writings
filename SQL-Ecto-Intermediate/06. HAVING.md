To do aggregate functions such as `AVG`,`COUNT`, `MAX` in `group by`. `HAVING` is used. You cannot do aggregate functions in `WHERE`. 

Example:

``` SQL
SELECT region_id, COUNT(region_id) FROM countries GROUP BY region_id HAVING COUNT(region_id) > 3;
```

Here we are only returning `region_id` and count of the `region_id` only if the count is > 3.
Basically we are telling what grouped items should returned in the table. Here the count should be > 3.

Result:

![[Pasted image 20231109135608.png]]

You can see in the above example that, all the records count is > 3.

# Ecto query for `HAVING`

###### `having/3` 

`having/3` function let's you do aggregate functions in join. To filter the rows that are grouped.

``` Ecto
 SqlEcto.Hr.Country |> group_by([c], c.region_id)|> having([c], count(c.region_id)>3) |> select([c], %{"region_id" => c.region_id, "count" => count(c.region_id)})|> SqlEct
o.Repo.all()
```

`having([c], count(c.region_id)>3)`  -> `[c]` is the reference variable name. `count(c.region_id)>3` is the `count` function which used to tell that the count of the `region_id` should be greater than 3. we are telling to return only grouped rows that the count of the  `region_id` is greater than 3.

Result:

![[Pasted image 20231109141501.png]]



