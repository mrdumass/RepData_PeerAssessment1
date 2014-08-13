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

```r
"mean"
```

```
## [1] "mean"
```

```r
mean(stepsperday, na.rm = TRUE)
```

```
## [1] 10766
```

```r
"median"
```

```
## [1] "median"
```

```r
median(stepsperday, na.rm = TRUE)
```

```
## [1] 10765
```




## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
