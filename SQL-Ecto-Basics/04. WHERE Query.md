To select records which is having a particular values `WHERE` command is used. Used to filter records.

Example:

The below is the `locations` table.

![[Screenshot from 2023-11-03 10-31-22.png]]

Let's select only those records whose `country_id` is `US`.

``` SQL
SELECT * FROM locations WHERE country_id = 'US';
```

Following by `WHERE`,  `country_id` is the the column name which has to be equal to the value 'US'. `SELECT` `FROM` `WHERE` has to be in this order only.

Result:

![[Screenshot from 2023-11-03 10-43-35.png]]

###### **Note:**

In SQL, anything inside ' ' single quote are treated as string.
For example

1. 'name' - is also string
2. 1. '123'  -is string
 
  Anything inside " " are treated as column name. if you put any words inside " ", SQL will take that as a column name and will search for it.

![[Screenshot from 2023-11-03 10-47-04.png]]

As you see In the above example, it says column "US" does not exist. SQL consider "US" as a column name. 


# Ecto query for `where` 

#### `where/3` function

In Ecto.Query `where/3` is used to fetch records based on the particular value.

Example:

``` Ecto
SqlEcto.Hr.Location |> where([c], c.country_id == "US") |> SqlEcto.Repo.all()
```

Result:

 ![[Screenshot from 2023-11-03 11-12-50.png]]

`where([c], c.country_id == "US")` -> Fetching `SqlEcto.Hr.Location` struct only those which `country_id` is equal to "US".  