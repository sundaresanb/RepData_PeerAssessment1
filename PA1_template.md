# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
data <- read.csv("~/Documents/R/activity.csv")
data_filtered <- data[!is.na(data$steps), ]
data_split <- with(data_filtered, split(steps, date))
steps_by_day <- lapply(data_split, sum)
steps_by_day <- unlist(steps_by_day)
```


## What is mean total number of steps taken per day?

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

```
## Mean steps per day:  9354
```

```
## Median steps per day:  10395
```


## What is the average daily activity pattern?

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

```
## Interval with average maximum steps/ average maximum steps =  835 / 206.2
```


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
