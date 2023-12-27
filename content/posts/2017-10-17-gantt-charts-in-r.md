---
title: Gantt Charts in R
author: C Ried
date: '2017-10-17'
slug: gantt-charts-in-r
categories:
tags: ['r']
---

# In Progress



## Using timevis 
```r
library(timevis)

data <- data.frame(
  id      = 1:4,
  content = c("Item one"  , "Item two"  ,"Ranged item", "Item four"),
  start   = c("2016-01-10", "2016-01-11", "2016-01-20", "2016-02-14 15:00:00"),
  end     = c(NA          ,           NA, "2016-02-04", NA)
)

timevis(data)
```


## Using DiagrammerR
```r

library(tidyr)
library(dplyr)
library(DiagrammeR)

mermaid("
gantt
dateFormat  YYYY-MM-DD
title A Very Nice Gantt Diagram

section Basic Tasks
This is completed             :done,          first_1,    2014-01-06, 2014-01-08
This is active                :active,        first_2,    2014-01-09, 3d
Do this later                 :               first_3,    after first_2, 5d
Do this after that            :               first_4,    after first_3, 5d

section Important Things
Completed, critical task      :crit, done,    import_1,   2014-01-06,24h
Also done, also critical      :crit, done,    import_2,   after import_1, 2d
Doing this important task now :crit, active,  import_3,   after import_2, 3d
Next critical task            :crit,          import_4,   after import_3, 5d

section The Extras
First extras                  :active,        extras_1,   after import_4,  3d
Second helping                :               extras_2,   after extras_1, 20h
More of the extras            :               extras_3,   after extras_1, 48h
")
```


## Using Plotly 
If you wanted to use a more 
```r
library(plotly)

df <- read.csv("https://cdn.rawgit.com/plotly/datasets/master/GanttChart-updated.csv", stringsAsFactors = F)

df$Start  <- as.Date(df$Start, format = "%m/%d/%Y")
client    <- "Sample Client"
cols      <- RColorBrewer::brewer.pal(length(unique(df$Resource)), name = "Set3")
df$color  <- factor(df$Resource, labels = cols)

p <- plot_ly()
for(i in 1:(nrow(df) - 1)){
  p <- add_trace(p,
                 x = c(df$Start[i], df$Start[i] + df$Duration[i]), 
                 y = c(i, i), 
                 mode = "lines",
                 line = list(color = df$color[i], width = 20),
                 showlegend = F,
                 hoverinfo = "text",
                 text = paste("Task: ", df$Task[i], "<br>",
                              "Duration: ", df$Duration[i], "days<br>",
                              "Resource: ", df$Resource[i]),
                 evaluate = T
  )
}

```

```r
p
```

