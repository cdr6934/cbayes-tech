---
title: Timeseries Analysis Using R and Advantager
author: C Ried
date: '2017-11-11'
slug: timeseries-analysis-using-r-and-advantager
categories:
tags: ['R', 'documentation']
---


### Threw error due to the API 

In the past, the best way to get stock prices was to use either Google Finance or Yahoo Finance data streams. These have since become difficult to keep up to date and thus another outlet to get this information is AlphaVantager. Following is a simple R implementation to get up to date data. You will be able to thus use this to find the information. 

```r
library(alphavantager)
library(tidyverse)
source("~/Keys.R")
```

Above we provide two different libraries that will give us the functionality we need.

```r

#symbol <- "BTC"
#av_api_key(advantagerKey)
#data <- av_get(symbol = symbol,market = "CNY", av_fun ="DIGITAL_CURRENCY_DAILY") 
#write.csv(data, "btc_data.csv")
```

In order to make this more useful, we will parameterize these functions in order to make data exploration easier to use when looking at multiple stocks. 

```r
#head(data)
```


Here we look at the daily open price of the stock for the past 5 years. 

```r
#g <- data %>%
#  filter(timestamp >= '2017-1-1') %>% 
#  ggplot() + 
#  geom_line(aes(timestamp, open..cny. ))+  
#  labs(title = paste("Daily Open Pricing (",symbol,")"), 
#       y = "Open Price (BTC)", x = "Daily")
#g
```

#References 
* [API Key Access](https://www.alphavantage.co/support/#)