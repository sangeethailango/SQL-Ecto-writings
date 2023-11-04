SELECT and FROM 

To view a table, or any columns from a table, `SELECT` and `FROM` are used.  As it name suggest it will `select` a_column `from` a_table. It has to be in that order only. This is the common query in all the SQL queries. 

### **Example**

 ![[Screenshot from 2023-10-31 16-32-07.png]]

The above table is the `countries` table. Let's select only `country_name` column from it.

```SQL
SELECT country_name FROM countries;
```

On the above query, `country_name` is the column name from the table called `countries`. The above line will give the below result.

Result:

![[Screenshot from 2023-10-31 16-37-13.png]]

if you wanted to select more than one column from a table, you can use `,` between the column names. let's select `country_id` and `country_name` from `countries`.

``` SQL
SELECT country_id, country_name FROM countries;
```

Result:

![[Screenshot from 2023-11-02 11-57-39.png]]


if you wanted to select every column from a table use `*` symbol. 

``` SQL
SELECT * FROM countries;
```

**Formatting convention**

SQL accept capitalized and not capitalized letters for their queries. SQL will accept both `SELECT` and `select`. But it is best to practice to use capitalized letter as it is easily readable.

# Ecto query for `SELECT`


Ecto has 4 main components. you can visit [https://hexdocs.pm/ecto/Ecto.html](https://hexdocs.pm/ecto/Ecto.html)   Let's see the equivalent Ecto queries to fetch all the inserted records from a schema and any particular fields from a schema. 

##### 1. Using `Repo.all/1` 

### **Syntax**

``` Ecto
  Repo.all(Schema_name)
```

### **Example:**

``` Elixir
defmodule SqlEcto.Hr.Country do
	use Ecto.Schema
	import Ecto.Changeset
	
	@primary_key {:country_id, :string, autogenerate: false}
	schema "countries" do
	
	field :country_name, :string
	field :region_id, :integer
	
	end
	
	def changeset(countries, _params) do
	countries
	|> validate_required(:region_id)
	|> validate_length(:country_id, max: 2)
	|> validate_length(:country_name, max: 40)
	end
end
```

The above is the Country schema. Let's fetch all the records inserted in this schema using iex shell. 

``` iex
iex(10)> SqlEcto.Repo.all(SqlEcto.Hr.Country)
```

Explanation:

In Ecto.Repo, there is a function called Repo.all/1. It will fetch all the records from the given schema. In the above example,  `SqlEcto.Repo` is the project's Repo name. `SqlEcto.Hr.Country` is the schema module name. If you put the above command you will get a list of structs.

Result:

![[Screenshot from 2023-11-02 13-45-54.png]]

##### 2.  Using `select/3`

In Ecto.Query, there is a function called `select/3`. `select/3` is used to select particular fields from a schema. you can also select the whole schema. you have to give a structure of how you want your data to be appeared. For example, list, tuple or map, etc...

Example:

``` Ecto
SqlEcto.Hr.Country |> select([c], [c.country_name, c.region_id]) |> SqlEcto.Repo.all()
```

Result:

![[Screenshot from 2023-11-03 09-15-31.png]]

Explanation:

On the above example, we are selecting `country_name` and `region_id` from `SqlEcto.Hr.Country` schema. 

`select([c], [c.country_name, c.region_id])` ->

- `c` is the reference variable for the schema `SqlEcto.Hr.Country`.  `c` is used in the whole expression to refer the schema. `c` = `SqlEcto.Hr.Country`
- `[c.country_name, c.region_id]` [] list is the data structure. You can also use tuple, keyword list, struct. `country_name`, `region_id` are the fields.
- `Repo.all/1` will fetch the selected fields from the Database.

You can also select the whole struct. Instead of selecting particular fields like `c.country_name` and `c.region_id`, give the reference variable `c`. 

``` Ecto 
SqlEcto.Hr.Country |> select([c], c) |> SqlEcto.Repo.all() 
```



