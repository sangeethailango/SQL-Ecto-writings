
`FULL OUTER JOIN` will return unmatched and matched values from both side tables. 

Example:

###### `job_history` 

![[Pasted image 20231107162852.png]]

##### `regions` 

![[Pasted image 20231107162952.png]]

You can see that one record is matching for both tables and one records is not matching for both tables.

``` SQL
SELECT * FROM regions FULL OUTER JOIN job_history ON regions.region_id = job_history.region_id;
```

Result:

![[Pasted image 20231107163139.png]]

You can see that all columns got returned.