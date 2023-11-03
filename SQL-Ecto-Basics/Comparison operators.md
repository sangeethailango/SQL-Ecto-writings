In `SQL` and `Ecto`, comparison operators used to compare between values. You can filter results using comparison operators. 

##### Comparison operators

In `SQL` and `Ecto`, comparison operators are same. only equal to will vary. In `sql` = is used , in `Ecto` == is used

In `SQL` 

`=`           Equal to
`!=`          Not equal to
\<           Less than
\>           Greater than
\>=         Greater than or equal to
`<=`         Less than or equal to 

In `Ecto`

`==`           Equal to
`!=`          Not equal to
\<           Less than
\>           Greater than
\>=         Greater than or equal to
`<=`         Less than or equal to 


##### SQL

Example 1: 

we have `employees` table. Let's select those records whose salary is **less than** 6000 using `<` operator.

![[Screenshot from 2023-11-03 11-45-03.png]]

``` SQL
select * from employees where salary < 6000;
```

Result:

![[Screenshot from 2023-11-03 11-46-57.png]]

Example 2:

``` SQL
SELECT * FROM locations WHERE country_id = 'US';
```

As we saw in the `where` query, We are selecting locations whose country_id is **equal to** 'US', using `=` operator .

##### Ecto

``` Ecto
SqlEcto.Hr.Employee |> where([c], c.salary < 6000) |> SqlEcto.Repo.all()
```

We are fetching `SqlEcto.Hr.Employee` whose salary is **less than** 6000 using < operator.

```Ecto
SqlEcto.Hr.Location |> where([c], c.country_id == "US") |> SqlEcto.Repo.all()
```

will fetch `SqlEcto.Hr.Location` whose `country_id` is equal to `US` using == operators.

**Note:**

In `SQL`, equal to is `=`  operator
in `Ecto` is equal to is `==` operator

Other than **equal to**,  every comparison operators are same.