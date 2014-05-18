# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
data <- read.csv("activity.csv")
data_filtered <- data[!is.na(data$steps), ]
data_split <- with(data_filtered, split(steps, date))
steps_by_day <- lapply(data_split, sum)
steps_by_day <- unlist(steps_by_day)
```


## Mean total number of steps taken per day

![plot of chunk Mean total number of steps taken per day](figure/Mean_total_number_of_steps_taken_per_day.png) 

```
## Mean steps per day:  9354
```

```
## Median steps per day:  10395
```


## Average daily activity pattern

![plot of chunk Average daily activity pattern](figure/Average_daily_activity_pattern.png) 

```
## Interval with average maximum steps, average maximum steps =  835 , 206.2
```


## Inputing missing values (NAs replaced with mean of steps across intervals)


```
## Number of missing values:  2304
```



```r
# replacing missing values with mean of steps across respective interval
temp <- with(data_filtered, split(steps, interval))
temp <- lapply(temp, mean)
temp <- data.frame(interval = names(temp), steps = unlist(temp))
data[is.na(data)] <- ceiling(temp$steps)
```


![plot of chunk Histogram with NAs replaced](figure/Histogram_with_NAs_replaced.png) 

```
## Mean steps per day (after replacing NAs):  10785
```

```
## Median steps per day (after replacing NAs):  10909
```

```
## Observation in mean/ median: mean has shifted, median has not.
```


## Differences in activity patterns between weekdays and weekends
![plot of chunk Activity pattern between weekdays and weekends](figure/Activity_pattern_between_weekdays_and_weekends.png) 

