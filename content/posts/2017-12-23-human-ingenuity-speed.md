---
title: Human Ingenuity and Speed
author: Chris
date: '2017-12-23'
slug: human-ingenuity-and-speed
categories:
tags: ['astronomy','R']
---



```r
library(tidyverse)
```


Data Building 

The first thing we need to understand is where we have come and where we are going. There is alot that has been done in the past couple years but we still have more. 


```r
type <- c("Sound","Light","Human Travel")
units <- c("mps","mps","mps")
speed <- c(343,299792458,11082.569)
source <- c("","","")
speed_data <- data.frame(type,units, speed,source)
```



```r
spd <- speed_data$speed
spd %*% (t(spd)) 
```



--TODO: The following

```r
299792458/11082.57
```


# Human History of Speed 
Speed hasn't been a 

