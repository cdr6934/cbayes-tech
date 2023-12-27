---
title: Formatting Currencies in R
author: Chris Ried
date: '2018-08-21'
tags: ['R', 'currency']
---

Here are a few  ways to format numbers in R for presentations. A few of theme can be accomplished using the _paste_ function in R. I've found that there are a few different methods to do this.


### Using the scales package 

Using the _scales_ packages from Hadley, there is a great function with various options including passing a vector. 


```r
	library(scales)
	dollar_format()(c(-100, 0.23, 1.456565, 2e3))
```

### Formatting currency with separator 

Following is a simple function one can build and place in their utility function that will give formatted currency. 

```r
myNum = 1234.12 
toCurrency <- function(money)
{
	paste("$",format(money, big.mark=","),sep="")
}
toCurrency(myNum)
```