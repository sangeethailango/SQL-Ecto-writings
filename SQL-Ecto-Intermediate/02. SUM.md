`SUM` is used to get the sum of any particular column in a table. `SUM` will give the addition value of any column in a table. It will only work on numerical values. 

Example:

![[Pasted image 20231106144113.png]]

The above is the `jobs` table. Let's find out the sum of the column `max_salary`.

``` SQL
SELECT SUM(max_salary) FROM jobs;
```

Result:

![[Pasted image 20231106144236.png]]

The total sum of column `max_salary` is 25,100,0

# Ecto query for `SUM`

`sum/1` is used to get the sum of a fields in a schema.  

Example:

``` Ecto
SqlEcto.Hr.Job |> select([c], sum(c.max_salary)) |> SqlEcto.Repo.all()  
```

The above will calculate the sum of `max_salary` field in `SqlEcto.Hr.Job`.

Result:

![[Pasted image 20231106144632.png]]

The sum of `max_salary` in `SqlEcto.Hr.Job` is 2,51,000.
