---
title: Time and Difficulty
author: Chris Ried
date: '2018-08-07'
slug: time-and-difficulty
tags: ['R','difficulty']
---

Sometimes, seeing data in a 3 dimensional space gives us better visibility to the rest of the world. You will see that we have taken a hypothetical experiment and tried to rate different ideas by their complexity and likelihood to succeed.  

```r

#Libraries to import
library(tidyverse)
library(plotly)


# Intellectual matrix 
idea <- c("Build a spaceship","Create a new social platform",
          "Build a birdhouse","Collect 10000 friends",
          "Clip toenails","Build a spaceship","Create a new social platform",
          "Build a birdhouse","Collect 10000 friends","Build a spaceship","Create a new social platform",
          "Build a birdhouse","Collect 10000 friends","Build a spaceship","Create a new social platform",
          "Build a birdhouse","Collect 10000 friends")
time <- c(5,5,2,3,1,5,5,2,3,5,5,2,3,1,5,5,2)
difficulty <- c(5,4,2,3,1,5,4,2,3,5,5,2,3,1,5,5,2)
favorability <- c(2,5,2,1,3,4,1,2,1,2,5,2,1,3,3,1,2)

#Creates the dataframe
dataset <- data.frame(Idea = idea, Time = time, Difficulty = difficulty, Favorable = favorability)


# Creates the 3 dimension intellectual plot
p <- plot_ly(dataset, x = ~Time, y = ~Difficulty, z = ~Favorable, color = ~Idea) %>%
  add_markers() %>%
  layout(title = "Intellectual Matrix", scene = list(xaxis = list(title = 'Length to Complete'),
                                                     yaxis = list(title = 'Difficulty'),
                                                     zaxis = list(title = 'Likability')))

p
```
