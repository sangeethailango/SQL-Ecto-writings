
`LEFT JOIN` will return all rows from left and only matching rows from right. 

Example:

`countries` table

![[Pasted image 20231107155511.png]]

`regions` table

![[Pasted image 20231107155541.png]]

We have `countries` and `regions` table. Let's do `LEFT JOIN` for it.

``` SQL
SELECT * FROM countries LEFT JOIN regions ON countries.region_id = regions.region_id;
```

`LEFT JOIN` will return all rows from `countries` table but only some rows from `regions` table where in the table `regions`,  `region_id`  column is matching to `region_id` column `countries`.


Result:

![[Pasted image 20231107155706.png]]

`regions` have 7 rows and `countries` have 25 rows. Last 3 records in the `regions` didn't match with any rows in the `countries` table. As `LEFT JOIN` will return only matching values from the right side table, these unmatched values in `regions` table didn't come when doing `LEFT JOIN` in the above example.
