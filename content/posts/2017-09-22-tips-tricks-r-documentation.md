---
title: Tips on Creating Effective and Functional Documentation in R 
author: Chris R. 
date: '2017-09-22'
slug: tips-creating-functional-documention
categories:
tags: ['r','documentation','packages','roxygen']

---

 Just like any skill, there is a learning curve involved in creating effective communication. This involves the code written and the documentation of its usage. Writing functional code is a intricate thing to accomplish as a newbie. It takes time to know what is efficient and how to communicate it as such. Now, writing functional documentation is more complicated as there is a delicate balance between not reguritate what the code says, and giving usable pointers to the users on how a particular function was intended to be used. It also, keeps you in line as the coder practices by actively thinking about that balance. Thus you help yourself keeping it modular and simple. So here are a few tips on how to writing effective documentation. 


### 1. Keep It Simple Stupid (KISS)
* Simplicity always wins over an overly complicated explanation. If you can't explain something in simple terms, try to break it down into smaller steps so that it can be communicated to your audience. 

### 2. Define how the function works
* Describing a function in one sentence can be difficult, however it gives the user of your code the ability to scan your functions and determine with ease which function they need to use for their project. If it takes more than a  sentence to explain what the function is; there is a good chance it is a bloated function. Try to break your function down into smaller parts for improved readability and easier bug tracking. 

* Don't write pseudo code comments; let the code read itself. If it can't be read,  that should indicate there is an easier way to write it.

### 3. Determine the parameter types
* Document the class / type of data that is being passed into the function and name it in such a way that gives the reader a clear understanding of its function. This will help you when writing unit tests for these functions in the future. That way you will know what should work and run as a positive test and what shouldn't. 

### 4. Describe what the function should return 
* Again, you'd think it would be simple to remember. But, againn it should be a way to describe the type / class of data that is going to be returned. If you don't know what the function should return; it is neigh impossible to know how you should use it's result. 

### 5. Dream up an implementation of the function
* Now that you have defined the ins / outs of the function. Why not create a reproducible example of your function. This will give the your user the ability to see how it works and what they expect from a tried and true function. 


All of these are suggestions and  will vary from company to preference to individual. But the bottom line is, you will need a way to communicate your creation so that anyone can pick up what you have written and use it to further extend one's own analysis or packages. Otherwise you will end up in the ghost town of a github repo that has never seen the light of day. Or have someone rewrite the same thing you have written. 

## Now how do we implement this in R?

Down here we find an implementaiton of these rules that have been pulled from the roxygen2 package. Above every function that is coded, you should have the following added. This will give you the ability to properly understand what and why you have written. 

```r
#' Add together two numbers
#'
#' @param x A number
#' @param y A number
#' @return The sum of \code{x} and \code{y}
#' @examples
#' add(1, 1)
#' add(10, 1)
```


#### References 
* [ROxygen2 Vignette](https://cran.r-project.org/web/packages/roxygen2/vignettes/rd.html)
* [Rd Conversion](https://cran.r-project.org/web/packages/roxygen2/vignettes/rd.html)