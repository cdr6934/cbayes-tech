---
title: Simulate Doctor Visit Resource Planning Using Simmer
author: Chris Ried
date: '2018-08-07'
slug: simulate-resource-planning-using-simmer
categories:
tags: ['R','simmer']
---
Here I've tried to come up with a simple layout on how we might simulate doctor's visits. 

Following code tries to resource plan certain doctor visits based on the vignette that was provided with the simmer package. 


```r
library(simmer)
set.seed(42)
env <- simmer("SuperDuperSim")
env

patient <- trajectory("patients' path") %>%
  ## add an intake activity 
  seize("nurse", 1) %>%
  timeout(function() rnorm(1, 15)) %>%
  release("nurse", 1) %>%
  ## add a consultation activity
  seize("doctor", 1) %>%
  timeout(function() rnorm(1, 20)) %>%
  release("doctor", 1) %>%
  ## add a planning activity
  seize("administration", 1) %>%
  timeout(function() rnorm(1, 5)) %>%
  release("administration", 1)


env %>%
  add_resource("nurse", 1) %>%
  add_resource("doctor", 2) %>%
  add_resource("administration", 1) %>%
  add_generator("patient", patient, function() rnorm(1, 10, 2))


env %>% 
  run(80) %>% 
  now()

env %>% peek(3)

env %>%
  stepn() %>% # 1 step
  print() %>%
  stepn(3)    # 3 steps


envs <- lapply(1:100, function(i) {
  simmer("SuperDuperSim") %>%
    add_resource("nurse", 1) %>%
    add_resource("doctor", 2) %>%
    add_resource("administration", 1) %>%
    add_generator("patient", patient, function() rnorm(1, 10, 2)) %>%
    run(80)
})


envs %>% 
  get_mon_resources() %>%
  head()

envs %>% 
  get_mon_arrivals() %>%
  head()
```

