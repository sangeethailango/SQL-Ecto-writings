
To count the total number of non-null values for particular a column `COUNT` is used. You can also count the whole table.

Example:

![[Pasted image 20231106141136.png]]

The above is the `jobs` table. The following syntax is used to get the total number of rows this table.

``` SQL
SELECT COUNT(*) FROM jobs;
```

\*  is refer the whole table.

Result:

![[Pasted image 20231106141739.png]]

Now, let's count non-null `max_salary` rows.

``` SQL
SELECT COUNT(max_salary) FROM jobs;
```

Result:

![[Pasted image 20231106141938.png]]

You can clearly see that, when we counted the whole table using `*` the result is 20, but when i count only `max_salary` rows, the result is 19.  it's because one record is having null value in the `max_salary` column. 

# Ecto query for `COUNT`

#### `count/0`

To get the total number inserted structs for a schema `count/0` is used.

Example:

``` Ecto
SqlEcto.Hr.Job |> select([c], count()) |> SqlEcto.Repo.all() 
```

Result:

![[Pasted image 20231106142528.png]]

The total number of structs for `SqlEcto.Hr.Job` is 20 as you can see in above example.

#### `count/1`

If you wanted to calculate total number of non-null values for a particular field in a schema
use `count/1`.

Example:

``` Ecto
SqlEcto.Hr.Job |> select([c], count(c.max_salary)) |> SqlEcto.Repo.all()
```

`count(c.max_salary)` ->  We are calculating `max_salary` here for `SqlEcto.Hr.Job`.  

Result:

![[Pasted image 20231106143013.png]]

The total number of `max_salary` field that has non-null value is 19.

