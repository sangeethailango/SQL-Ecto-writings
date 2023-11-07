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


# Ecto query for `LEFT JOIN`
##### `join/5`

`join/5` function is used to do left join in `Ecto`. To know more about `join/5` function, visit my [[JOIN]] page.

###### `:left` option

Example:

``` Ecto
SqlEcto.Hr.Region |> join(:left, [r], c in SqlEcto.Hr.Country, on: r.region_id == c.region_id) |> select([r, c], [r,c])   |> SqlEcto.Repo.all() 
```

Explanation:

So the above query will return all records from `SqlEcto.Hr.Region` as it is on the left side of the `on:`.  And only matching records from  `SqlEcto.Hr.Country` as it is on the right side of `on:`.

`|> join(:left, [r], c in SqlEcto.Hr.Country, on: r.region_id == c.region_id) `

- It is accepting `SqlEcto.Hr.Region` schema as first argument. 
- `[r]` is the reference variable for `SqlEcto.Hr.Region` schema.
- `c in SqlEcto.Hr.Country` another schema and reference variable.
- `on: r.region_id == c.region_id)` condition.

Result:

``` iex
[
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 2,
      region_name: "Americas"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "AR",
      country_name: "Argentina",
      region_id: 2
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "AU",
      country_name: "Australia",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "BE",
      country_name: "Belgium",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 2,
      region_name: "Americas"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "BR",
      country_name: "Brazil",
      region_id: 2
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 2,
      region_name: "Americas"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "CA",
      country_name: "Canada",
      region_id: 2
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "CH",
      country_name: "Switzerland",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "CN",
      country_name: "China",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "DE",
      country_name: "Germany",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "DK",
      country_name: "Denmark",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "EG",
      country_name: "Egypt",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "FR",
      country_name: "France",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "HK",
      country_name: "HongKong",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "IL",
      country_name: "Israel",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "IN",
      country_name: "India",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "IT",
      country_name: "Italy",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "JP",
      country_name: "Japan",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "KW",
      country_name: "Kuwait",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 2,
      region_name: "Americas"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "MX",
      country_name: "Mexico",
      region_id: 2
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "NG",
      country_name: "Nigeria",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "NL",
      country_name: "Netherlands",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 3,
      region_name: "Asia"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "SG",
      country_name: "Singapore",
      region_id: 3
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 1,
      region_name: "Europe"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "UK",
      country_name: "United Kingdom",
      region_id: 1
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 2,
      region_name: "Americas"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "US",
      country_name: "United States of America",
      region_id: 2
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "ZM",
      country_name: "Zambia",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 4,
      region_name: "Middle East and Africa"
    },
    %SqlEcto.Hr.Country{
      __meta__: #Ecto.Schema.Metadata<:loaded, "countries">,
      country_id: "ZW",
      country_name: "Zimbabwe",
      region_id: 4
    }
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 5,
      region_name: "India"
    },
    nil
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 6,
      region_name: "China"
    },
    nil
  ],
  [
    %SqlEcto.Hr.Region{
      __meta__: #Ecto.Schema.Metadata<:loaded, "regions">,
      region_id: 7,
      region_name: "Korean"
    },
    nil
  ]
]
```

In the above result, you can see that all records in `SqlEcto.Hr.Region` are returned even though some doesn't have a matching  `SqlEcto.Hr.Country` records which got returned as nil value for `SqlEcto.Hr.Country`.

 