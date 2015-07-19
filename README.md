# RResearch_PeerAssessment1


---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data

```{r}
library(knitr)
library(dplyr)
library(ggplot2)
getwd()
opts_chunk$set(echo = TRUE)
```

```{r}
mydata <- read.csv('activity.csv')

check <- nrow(mydata) == 17568
if (check == FALSE) stop("The number of rows in the dataset is not 17,568.")

mydata <- mydata[ with (mydata, { !(is.na(steps)) } ), ]

```



## What is mean total number of steps taken per day?
```{r}

by_day <- group_by(mydata, date)
steps_by_day <- summarise(by_day, total = sum(steps))
steps_by_day

```
```{r}
hist(steps_by_day$total, main="Histogram of total number of steps per day", 
     xlab="Total number of steps in a day")
```
```{r}
summary(steps_by_day)

```




## What is the average daily activity pattern?

```{r}
steps_by_interval <- aggregate(steps ~ interval, data, mean)
plot(steps_by_interval$interval, steps_by_interval$steps, type='l', 
     main="Average number of steps over all days", xlab="Interval", 
     ylab="Average number of steps")

```
```{r}
max_steps_row <- which.max(steps_by_interval$steps)
steps_by_interval[max_steps_row, 

```


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
