
`RIGHT JOIN` will return all rows from right and only matching rows from left.

`countries` table

![[Pasted image 20231107155511.png]]

`regions` table

![[Pasted image 20231107155541.png]]


We have `countries` and `regions` table. Let's do `RIGHT JOIN` for it.

``` SQL
SELECT * FROM countries RIGHT JOIN regions ON countries.region_id = regions.region_id;
```

the above code returns all records form `regions` table but only records which matching the condition `ON` from the `countries` table.

Result:

![[Pasted image 20231107160949.png]]

You can see that all records from `regions` table got returned here even though the `region_name`,  `India` `China` `Korean`  didn't have matching values with `countries` table.   
