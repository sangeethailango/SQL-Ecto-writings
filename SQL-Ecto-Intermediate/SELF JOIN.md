`SELF JOIN` let's you join the same table based on the queries. 

Syntax:

``` SQL
select column_1, column 2 from table_1, table_2 where condition;
```

`column_1`, `column_2` are columns from the same table but selecting twice. 
`table_1`, `table_2` are same tables but selected twice.

So the tables would be two but both will be the same table. By the condition that you are writing in `where` the records will return. 

Example:

![[Pasted image 20231108205230.png]]

This is the `locations` table. You can see that lot of records have same `country_id` such as `US`, `UK`. So Let's do query to find what are all the `street_address` are from what `country_id`.

``` SQL
SELECT A.street_address AS street_address_1, B.street_address AS street_address_2, A.country_id FROM locations A, locations B WHERE A.street_address <> B.street_address AND A.country_id = B.country_id;
```

Here, i am fetching `street_address_1`, `street_address_2` from `locations_1`, `locations_2`. In `where` condition, i am saying `street_address` should not match each other and `country_id` should be same. So it will look for `street_address` whose `country_id` are same and will return.

Result:

![[Pasted image 20231108212727.png]]

