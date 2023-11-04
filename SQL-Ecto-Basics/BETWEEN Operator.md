To a check for a range, `BETWEEN` is used in `WHERE`. It will check if the records are having values between the mentioned range for a column. it is used with `AND` command. 

Example:

``` SQL
SELECT * FROM employees WHERE job_id BETWEEN 5 AND 9;
```

The above code, will check for `employees` whose `job_id` is between the range 5 to 9. It will match for exact values.

``` SQL
SELECT * FROM employees WHERE job_id >=  5 AND job_id <= 9;
```

Both code will give the same results.

Result:

![[Screenshot from 2023-11-04 10-44-25.png]]

You can see that the above record's `job_id` is between 5 to 9.

# Ecto query for `BETWEEN`

There is no specific `between`function for Ecto. But you can filter your records from particular range to range using `fragement/1` https://hexdocs.pm/ecto/Ecto.Query.API.html#fragment/1 function or using comparison operator.

