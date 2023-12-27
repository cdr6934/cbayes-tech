---
title: 'Tracking Change Improvements in Retail'
author: Chris Ried
date: '2017-09-21'
slug: tracking-change-improvements-in-retail
categories:
tags: ['r']
---


In the ever changing world of retail; one always has to keep one step ahead of the competition and to engage with its customers. One of the best ways 

* Formulate a test
* Implement Test
* Evaluate results
* Adjust the test 
* Try again.  

These are all great ideas, but how do we truly watch tas things get better? 

```r
library(qcc)
library(xtable)
library(SixSigma)
library(qicharts)
```

## Cause and Effect Diagrams 
```r
cManpower <- c("Recepcionist", "Record. Operator",
"Storage operators")
cMaterials <- c("Supplier", "Transport agency",
"Packing")
cMachines <- c("Compressor type",
"Operation conditions",
"Machine adjustment")
cMethods <- c("Reception", "Transport method")
cMeasurements <- c("Recording method",
"Measurement appraisal")
cGroups <- c("Manpower", "Materials", "Machines",
"Methods", "Measurements")
cEffect <- "Too high density"

cause.and.effect(
cause = list(Manpower = cManpower,
Materials = cMaterials,
Machines = cMachines,
Methods = cMethods,
Measurements = cMeasurements),
effect = cEffect)
```

```r
ss.ceDiag(
effect = cEffect,
causes.gr <- cGroups,
causes = list(cManpower, cMaterials, cMachines,
cMethods, cMeasurements),
main = "Cause-and-effect diagram",
sub = "Pellets Density")
```



## Check Sheet
```r
data_checkSheet <- rbind(
data.frame(Group = "Manpower",
Cause = cManpower),
data.frame(Group = "Machines",
Cause = cMachines),
data.frame(Group = "Materials",
Cause = cMaterials),
data.frame(Group = "Methods",
Cause = cMethods),
data.frame(Group = "Measurements",
Cause = cMeasurements)
)

data_checkSheet$A_supplier <- NA
data_checkSheet$B_supplier <- NA
data_checkSheet$C_supplier <- NA
```



```r
data_checkSheet
```

## Control Charts

```r
pdensity <- c(10.6817, 10.6040, 10.5709, 10.7858,
10.7668, 10.8101, 10.6905, 10.6079,
10.5724, 10.7736, 11.0921, 11.1023,
11.0934, 10.8530, 10.6774, 10.6712,
10.6935, 10.5669, 10.8002, 10.7607,
10.5470, 10.5555, 10.5705, 10.7723)

myControlChart <- qcc(data = pdensity,
type = "xbar.one")
summary(myControlChart)
```

## Histogram 

```r
hist(pdensity)
par(bg = "gray95")
hist(pdensity,
main = "Histogram of pellets density - Sample #25",
sub = "Data from ceramic process",
xlab = expression("Density (g"/"cm"^3*")"),
col = "steelblue",
border = "white",
lwd = 2,
las = 1,
bg = "gray")
```

```r
library(ggplot2)
ggplot(data = data.frame(pdensity),
aes(x = pdensity)) +
geom_histogram(fill = "seagreen",
colour = "lightgoldenrodyellow",
binwidth = 0.2) +
labs(title = "Histogram",
x = expression("Density ("*g/cm^3*")"),
y = "Frequency")
```
## Pareto Chart 
```r
data_checkSheet$A_supplier <- c(2, 0, 0, 2, 1, 7, 1,
3, 6, 0, 1, 2, 0)
data_checkSheet$B_supplier <- c(0, 0, 1, 1, 2, 1, 12,
1, 2, 1, 0, 0, 1)
data_checkSheet$C_supplier <- c(0, 1, 0, 6, 0, 2, 2,
4, 3, 0, 1, 0, 2)
data_checkSheet$Total <- data_checkSheet$A_supplier +
data_checkSheet$B_supplier +
data_checkSheet$C_supplier

data_checkSheet
```

```r
data_pareto <- data_checkSheet[order(
data_checkSheet$Total,
decreasing = TRUE), ]
par(mar = c(8, 4, 4, 2) + 0.1)
barplot(height = data_pareto$Total,
names.arg = data_pareto$Cause,
las = 2,
main = "Pareto chart for total causes")
```

```r
data_pareto2 <- data_pareto$Total
names(data_pareto2) <- data_pareto$Cause
pareto.chart(data = data_pareto2,
main = "Out-of-control causes")
```

```r
library(qualityTools)
paretoChart(x = data_pareto2,
main = "Out-of-control causes")
```

```r
spreadvector <- rep(names(data_pareto2),times = data_pareto2)
paretochart(spreadvector)

x <- rep(LETTERS[1:9], c(256, 128, 64, 32, 16, 8, 4, 2, 1))
paretochart(x)
```
## Scatterplot
```r
set.seed(1234)
ptemp <- - 140 + 15*pdensity + rnorm(24)

plot(pdensity ~ ptemp,
col = "gray40",
pch = 20,
main = "Pellets density vs. temperature",
xlab = "Temperature (Celsius)",
ylab = expression("Density ("*g/cm^3*")"))
```
##Stratification

```r
psupplier <- rep(c("A", "B", "C"), each = 8)

boxplot(pdensity ~ psupplier,
col = "gray70",
xlab = "Supplier",
ylab = expression("Density ("*g/cm^3*")"),
main = "Box plots by supplier")
```

```r
day1 <- c(0.821, 0.846, 0.892, 0.750, 0.773, 0.786,
0.956, 0.840, 0.913, 0.737, 0.793, 0.872)
day2 <- c(0.678, 0.742, 0.684, 0.766, 0.721, 0.785,
0.759, 0.708, 0.789, 0.732, 0.804, 0.758)
plates <- data.frame(thickness = c(day1, day2),
day = rep(c("Day1", "Day2"), each = 12))

plot(plates$thickness,
type = "b",
main = "Run Chart of Thickness",
las = 1,
ylab = "Thickness",
xlab = "Plate number",
pch = 20)
abline(h = median(plates$thickness),
lwd = 2)
```

```r
qic(thickness,
data = plates,
freeze = 12,
pre.text = "Day 1",
post.text = "Day 2",
runvals = TRUE)
```

