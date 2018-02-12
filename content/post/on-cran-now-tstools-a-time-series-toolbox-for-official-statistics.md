+++
Categories = ["R for economists","rstats","economic data visualization"]
date = "2018-02-12T11:09:05+01:00"
title = "On CRAN now: tstools - An R Toolbox for Time Series in Official Statistics and Macroeconomics"
Tags = ["rstats for economists","2 Y-axes","statistics","rstats","establishment statistics"]
Description = "tstools is an R toolbox for plotting time series in establishment statistics and macroeconomics. Conveniently use 2 y-axes, stacked bar charts with positive and negative contribution, highlight windows, ... "
+++


Shouldn't creating a **neat** time series chart **/w legend** be a matter of *tsplot(my_data)*? Don't you feel plotting a chart with 2 y-axes should be possible without getting hammered by community support for comming up with a desire that is 'fundamentally flawed' and 'utterly disgusting'? <!--more-->

I mean like

```
data(KOF)
tsplot(list("KOF Barometer" = KOF$kofbarometer),
            tsr = list("Reference" = KOF$reference))
```

![Stacked](/images/baro_w_reference.png)

Despite all the hype and traction, awesomeness and accessibility that the tidyverse, R Studio or shiny (to name only a few pieces of the ecosystem) brought to the R language, creating some of official statistics' most popular time series visualizations is too quirky a task for many newly intrigued. To me, R as a language and as a community has to face the fact that people who do not distinguish between Star Wars and Star Trek, start to use R.

Speaking of legends, I mean y'all should definitely know who Han Solo was, but I admit I understand your frustration with not getting a legend at the bottom of your plot by default. Or with the need to think about math beyond the 5th Grade in order to position your grids. Or with not just being able to have bar charts with negative contributions out-the-gates-quick. That frustration is the reason why we created tstools. 

Let me show a few use cases from the field of macroeconomics here, but I hope the package might be useful to other fields, too. 

### 1. Growth contributions to Swiss GDP (stacked bar chart)

```
# this only about loading example data
data("CHGDP")
# adjustments to the theme
tt <- init_tsplot_theme()
tt$sum_as_line <- T
tt$sum_line_color <- "#E1E1E1"
tt$bar_fill_color <- color_blind()

# the actual plot is single line of code ! 
tsplot(CHGDP,left_as_bar = T,theme = tt)

```  

![Stacked](/images/stacked_bar_gdp.png)


### 2. Grouped Bar Charts

Let's have detailed look at some smaller sectors and display bars next to 
each other, so smaller contributions can be compared more easily.

```
tsplot(CHGDP[c(2,3,4)],
	   left_as_bar = T,
       group_bar_chart = T,
       theme = tt)

```



![Grouped](/images/grouped_bar_chart_gdp.png)




### 3. Highlight a Time Window

Let's highlight the last two years (default). This option can be used 
to highlight a crisis, a boom or simply a forecast horizon. 

```
tt$highlight_window <- T
tt$sum_as_line <- F

tsplot(CHGDP[c(2,3,4)],
	   left_as_bar = T,
       group_bar_chart = T,
       theme = tt)

```

![highlight](/images/highlight_window.png)


As you can see, it's essentially the same call to *tsplot* and the same input time series. Just by tweaking the defaults a bit we can easily draw some of the macroeconomics' most popular time series plots. The easiest way to get started is to download the package from CRAN and follow the *vignette* for some introductory examples. 

```
install.packages("tstools")
vignette("tstools")

```

This is *tstools'* first public release. So questions, feedback and feature requests are more than welcome! I hope to highlight many new features here in the future.

