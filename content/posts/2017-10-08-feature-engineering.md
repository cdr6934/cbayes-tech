---
title: Tips on Feature Engineering
author: C Ried
date: '2017-10-08'
categories:
tags: ['r','feature engineering','statistics']
---

## Tips on Feature Engineering
* to fit how classifiers work; giving a geometry problem to a tree, oversized dimension to a kNN and interval data to an SVM are not a good ideas
* remove as much nonlinearities as possible; expecting that some classifier will do Fourier analysis inside is rather naive (even if, it will waste a lot of complexity there)
* make features generic to all objects so that some sampling in the chain won't knock them out
* check previous works -- often transformation used for visualisation or testing similar types of data is already tuned to uncover interesting aspects
* avoid unstable, optimizing transformations like PCA which may lead to overfitting
* experiment a lot