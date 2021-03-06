---
title: "Case Study 2 Project"
author: "Lauren Darr, Emmanuel Farrugia, John Heinen, Johnson Ekedum"
date: "`r format(Sys.time(), '%d %B, %Y')`"
output: 
  html_document:
    theme: united
    highlight: zenburn
---


# Introduction
There are two parts to this project.  The first part entails looking at the native data set Orange to analyze three tree types and their age and circumference.  First, we will find the circumference median and mean of each tree type, then we will plot the data of the tree's age versus circumference.  Finally, we will compare the circumferences of each tree type visually using boxplots.

Add text for Question 3

This document will go through any data downloads, cleaning of data, visualization, and analysis conclusion.

Before getting started, load the doBy, ggplot2, and add text packages into your R workspace. We will use functions from both packages through the project.


```r
if (!require("doBy")) {
  install.packages("doBy", repos="http://cran.rstudio.com/") 
}
```

```r
library(doBy)
if (!require("ggplot2")) {
  install.packages("ggplot2", repos="http://cran.rstudio.com/") 
}
```

```r
library(ggplot2)
```


## Question 2 Orange Trees
The Orange data is native to R, so we do not have to download from anywhere.  We can move right in to answering the questions of interest for this problem.  A little information on the data:

Tree: an ordered factor indicating the tree on which the measurement is made. The ordering is
according to increasing maximum diameter.
age: a numeric vector giving the age of the tree (days since 1968/12/31)
circumference: a numeric vector of trunk circumferences (mm). This is probably “circumference
at breast height”, a standard measurement in forestry.

First, we want to get the circumference mean and median for the trees.
```r

summaryBy(circumference ~ Tree, data = Orange, FUN = list(mean, median))

```

Next, we would like to plot the Age in days versus the Circumference of the trees, the plot will show different symbols and colors for each tree.
```r
plot(circumference ~ age,
           xlab = "Age (Days)",
           ylab = "Circumference (mm)",
           pch = c(16, 17, 18, 19, 20)[as.numeric(Tree)],  # different 'pch' types 
           main = "Age versus Circumference",
           col = c("red", "green","blue", "yellow", "orange")[as.numeric(Tree)],
           data = Orange)
           
legend("topleft", pch = c(16, 17, 18, 19, 20), col = c("red", "green","blue", "yellow", "orange"), legend = c("1","2","3","4","5"), title = "Trees")
```

Finally, we will look at comparitive boxplots of circumferences by tree, sorted in increasing order of maximum diameter.
```r
boxplot(circumference~Tree,data=Orange, main="Boxplot Circumference by Tree", xlab="Tree", ylab="Circumference")

```


## Conclusion
Write Conclusion here