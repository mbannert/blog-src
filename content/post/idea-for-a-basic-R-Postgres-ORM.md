+++
Categories = ["R ORM","rstats","postgreSQL","ORM for data science"]
date = "2017-12-19T11:11:05+01:00"
title = "Map R objects to PostgreSQL - a premature ORM draft for R and PG"
Tags = ["SQL","Postgres"]
Description = "Map R objects to PostgreSQL relations."
+++

Lately some of the rstats developer community's heavyweights have been busy to get  **RPostgres**, a DBI compliant R - PostgreSQL interface, to CRAN ready status. This remarkable effort and resulting github bustle, has motivated me as a long time R and PostgreSQL user to scratch some of my own much simpler, DB related itches: How about transforming R objects to PostgreSQL relations generically? 

How about some kind of Object Relational Mapping for R objects? Yep, I know the database should lead the way, not some quirky non-type safe language. But, ... maybe ORM is just too be big (or too exploited) of a word. Let's say: How about some SQL code generator written in R. Why?

Assume you have a data.frame (or data_frame as @Hadley would say.). 
Assume you decide to store it somewhere more persistent than in memory. 
Assume you want to share it with others, some of whom are not R users. 
Assume you want build a REST based web interface to access to the data.

You'd still tweak the data.frame before making it create tables.
Wouldn't it be great to magically have a create table statement like so: 

```
library(dplyr)
create_table_sql <- function(df,
                         tbl_name,
                         schema,
                         pk = NULL){
  # some examples mapping, of course we could
  # add more types here                       	
  sql_dplyr_map <- data_frame(
    dplyr_type = c("chr","int","lgl","list"),
    pg_type = c("text","integer","boolean","json")
  )
  type_v <- df %>% 
    lapply(type_sum)
  
  type_df <- data_frame(col_names = names(type_v),
                        dplyr_type = unlist(type_v)) %>% 
    inner_join(sql_dplyr_map)

  cols <- paste(type_df$col_names,
                type_df$pg_type,
                collapse=", ")  
  
  if(is.null(pk)) pk <- type_df$col_names[1]
  
  sql <- sprintf("CREATE TABLE %s.%s (%s,
                 PRIMARY KEY (%s));",
                 schema, tbl_name, cols,
                 pk)
  sql
}

```

And then simply call it like this to obtain the sql statement to be passed to the database?

```
create_table_sql(starwars,"starwars","movies")

```


Personally I've been using a less general, time series specific mapping 
for quite some time. Over time I've improved performance and r/w processes 
got more complex than just `SELECT` or `INSERT`. `UPSERT` kind of operations as well as '\copy' can do much more but require much more coding. So maybe, just maybe I could extend the above idea to a function factory creating 
statements for bulk `INSERT` and/or `UPSERT`. Hmmm... what do you think?


















