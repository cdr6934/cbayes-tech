---
title: Phillips Hue in R
author: 'Chris Ried'
date: '2018-08-07'
slug: phillips-hue-in-r
tags: ['iot','r','hue']
---


The following function can be used to find and display the internal IP address needed to retrieve the IP address from Hue Bridge. You will need to generate an API key i.e. a "userkey" as I called it below. 
```
getIP <- function()
{
  url <- paste0("https://www.meethue.com/api/nupnp")
  res <- httpGET(url)
  resJson <- fromJSON(res)
  res <- resJson[["internalipaddress"]]
  res
}

```

In order to know what light you should change the state on, one can run the following to retrieve the available lights connected on the network. 

```
getLights <- function(ip, userName)
{
  ip <- getIP()
  url <- paste0("http://",ip,"/api/",userName,"/lights/")
  #content <- paste0('{"on":',state,'}')
  res <- httpGET(url)
  res
}

getLights(getIP(),userName)
```
In order to change the state of a particular light; the following function can be called. Make sure to have a light designated for it to be manipulated. 

```
userName <- "" 
light <- "1" 

changeBrightness <- function(ip, userName, light,brightness)
{
  ip <- getIP()
  url <- paste0("http://",ip,"/api/",userName,"/lights/",as.character(light),"/state")
  content <- paste0('{"bri":',as.string(brightness),'}')
  res <- httpPUT(url,content)
  res
}
```

Now to further play with that light, you can change the light brightness (1-254) on a sine wave or whatever function you might decide to use. 

```
# change the brightness based on sin wave 
t = seq(0,60,0.3)
y <- sin(t)
plot(y)
vals <- as.integer(rescale(y,range(1,254)))
for(i in vals){changeBrightness(ip,userName,light,i)}


```