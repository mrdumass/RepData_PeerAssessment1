# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
act <- read.csv("activity.csv")
```

## What is mean total number of steps taken per day?

```r
stepsperday <- as.vector(tapply(act$step, act$date, sum))
hist(stepsperday, main = "Histogram of Total Steps Per Day", xlab = "Steps")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

The mean is

```r
mean(stepsperday, na.rm = TRUE)
```

```
## [1] 10766
```

The median is

```r
median(stepsperday, na.rm = TRUE)
```

```
## [1] 10765
```

## What is the average daily activity pattern?
Average the number of steps for each interval for all days
removing the missing. Plot that versus intervals in a day

```r
averagesteps <- tapply(act$steps, act$interval, mean, na.rm = TRUE)
plot(names(averagesteps), as.vector(averagesteps), type = "l", main = "Average Steps per Interval", 
    ylab = "Steps", xlab = "interval")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
