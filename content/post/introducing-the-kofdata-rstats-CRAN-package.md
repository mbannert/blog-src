+++
Categories = ["R","rstats","postgreSQL","API"]
date = "2017-12-19T11:11:05+01:00"
title = "Swiss data in R - Introducing the kofdata API R package"
Tags = ["rstats","API","Swiss data","forward looking indicator"]
Description = "Swiss data in R - Introducing the kofdata API R package"
+++

In an effort to make public data public, at KOF, we have recently introduced a REST Interface
to conveniently automate data downloads. R users can now benefit in even more convenient fashion, 
because of the brand new 'kofdata' CRAN package. The package allows to download Swiss time series data and meta information
through simple R functions. 

Installing the package is a matter of:


```
install.packages("kofdata")
```

Once you installed the package, you can, e.g., get Switzerland's most popular macro economic *forward looking indicator*, the KOF Barometer, by: 

```
library(kofdata)
get_time_series("kofbarometer")
```

You can easily plot the resulting series using time series plotting methods such as *tsplot* from my [tstools](https://github.com/mbannert/tstools) or simply base R's plot

```
library(tstools)
tslist <- get_time_series("kofbarometer")
tsplot(tslist)

# base R alternative without additional plot packages
plot(tslist$kofbarometer)

```

![KOF Barometer](/images/kofbarometer.png)



Btw: *get_time_series* does accept vectors of keys. Let's compare the KOF Index of Globalization for Switzerland and Germany for example. 

```
globidx <- get_time_series(c("ch.kof.globidx.v2015.index.che",
                              "ch.kof.globidx.v2015.index.deu"))
tsplot(globidx)

```

![KOF Globidx](/images/kofbarometer.png)


And yes, there's a bit more to the package than just querying vectors of keys: 


- **start_key_explorer** starts the alpha version of our graphical, hierarchical Web GUI Key explorer.
- **list_available_sets** lists available, pre-defined sets of series
- **get_dataset** downloads a pre-defined set by its name
- **list_keys_in_set** lists all keys in a set
- **get_remaining_quota** returns user's remaining quota for volume restricted downloads
- **list_cached_files** returns file names of pre-cached files for a particular user
- **download_cached_file** downloads a specified pre-cached file
- **get_metadata** returns meta information for a given language and key. language defaults to 'en'.
- **translate_legacy_key** returns current identifier given legacy key
- **get_legacy_key** returns the legacy identifier given a current identifier
   




   









