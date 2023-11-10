In this tutorial, you will learn about SQL queries and their equivalent Ecto queries. Both are used to interact with the database. 

### SQL

SQL stands for Structured Query Language. It is a language to interact with the database. 

### Ecto

Ecto is a elixir library which is a wrapper around the database in elixir.  Ecto has 4 main components. `Ecto.schema`, `Ecto.Repo`, `Ecto.Query`, `Ecto.Changeset`. These 4 are used to do things in Database. `Ecto.Repo` is used to create, delete, update, to do queries in database. `Ecto.Query` used to do queries from the `Ecto.Repo`. 

Every SQL query has it's own Ecto query and vice versa. Let's see some of the queries with their description.

#### **Database**

I took this database from https://www.sqltutorial.org/sql-sample-database/ this link.

I named my database as **sql_ecto_repo**. It has 7 tables. 

This database manages the HR data of a small business.

1. The `employees` table stores the data of employees.
2. The `jobs` table stores the job data including job title and salary range.
3. The `departments` table stores department data.
4. The `dependents` table stores the employee’s dependents.
5. The `locations` table stores the location of the departments of the company.
6. The `countries` table stores the data of countries where the company is doing business.
7. The `regions` table stores the data of regions such as Asia, Europe, America, and the Middle East and Africa. The countries are grouped into regions.

The following diagram explains the tables in the sql_ecto_repo database.

![[Screenshot from 2023-10-31 15-05-55.png]]


Number of records in each tables:

- employees      -     40
- dependents    -     30
- departments   -     11
- jobs                 -     11
- locations         -      7
- countries         -      25
- regions            -      4 

Now let's jump into the queries.


###  **Schema**

You can go through the below GitHub repo to see the schema structure. 
https://github.com/sangeethailango/SQL-Ecto-learning/tree/main/lib/sql_ecto/hr

