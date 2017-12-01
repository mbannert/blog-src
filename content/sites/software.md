+++
date = "2017-05-05T11:09:05+01:00"
title = "Open Source Software Projects"
Tags = ["R Stats","Matthias Bannert","Open Source"]
Description = "Open Source Software for Data Driven Analytics."

+++

## Establishment statistics

Establishment statistics have been my main occupation for a while now. Just like most
things you keep doing for a while, establishment statistics has certain reocurring itches.
Instead of scratching over and over again, I started and maintain a couple of R packages
to make everyday life a little more comfy.

### timeseriesdb: The ts-to-Postgres-mapper
timeseriesdb is an R interface to manage and archive time series. It was designed
to store a large number of (macro)economic time series and enables users to
store extensive and flexible, multi-language meta information. The timeseriesdb package
maps data stored in a PostgreSQL database to R time series objects. It's available from the official CRAN repository, but (at least for now) I recommend to download the latest dev version from [github](https://github.com/mbannert/timeseriesdb), because I was not able to update CRAN for quite some time.

### datenservice.kof.ethz.ch REST API

datenservice is a read only REST API to facilitate access to the rich economic time series database provided of my employer, the KOF Swiss Economic Institute. Our main goal is to automate data pipelines.


### tstools: Charts with 2 Y-Axes and more...
tstools is a toolbox for people who work with time series. The package does not do a lot R can't do out-of-the-box, but it helps to do things a lot more conveniently. tstools' early releases are mostly focused on plotting and a bit of exporting, but other features will follow. Again, economists are my main customers. Their fondness for charts with 2 Y-Axes and other forms of presentation does not [fall in line with hacking savvy professions who contribute to R (read Hadley Wickham's post)](https://stackoverflow.com/questions/3099219/plot-with-2-y-axes-one-y-axis-on-the-left-and-another-y-axis-on-the-right/3101876#3101876). Though I mostly agree with Hadley Wickham on the issue itself, the part where I don't agree is the conclusion to not provide a tool for this. It's a demanded feature and other packages (but R) can do it. I've spent time to convince people to use open source software and I don't want to see people turning their backs simply because they can't draw their favorite plot.


## Online Marketing

In order to avoid the Ivory tower trap of academia, I try to contribute to open source software that is used in the commercial world. If I was download driven, I'd probably focus on the Radwords project entirely. It's by far the most popular of the projects I contribute to, even though it's one of the more simple projects. 

### Radwords
Radwords is a wrapper around Google's Adwords API. Connect to your Google Account using R and download data through R and process it right in R. RAdwords is joint work with my buddy @jburkhardt. It's on [CRAN](https://cran.r-project.org/web/packages/RAdwords/index.html). Development is on 
[@jburkhardt's github](https://cran.r-project.org/web/packages/RAdwords/index.html).



