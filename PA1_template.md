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
Determine the step intervals that are missing data

```r
sum(is.na(act$steps))
```

```
## [1] 2304
```

Replace the missing value with the median of the average number of steps for that interval

```r
temp <- cbind(as.array(act$steps), averagesteps)
problems <- which(is.na(temp))
temp[problems, 1] <- temp[problems, 2]
act2 <- act
act2$steps <- temp[, 1]
```

repeat the analysis steps per day after the imputation

```r
stepsperday2 <- as.vector(tapply(act2$step, act2$date, sum))
hist(stepsperday2, main = "Histogram of Total Steps Per Day after imputation", 
    xlab = "Steps")
```

![plot of chunk unnamed-chunk-8](figure/unnamed-chunk-8.png) 

The mean is

```r
mean(stepsperday2)
```

```
## [1] 10766
```

The median is

```r
median(stepsperday2)
```

```
## [1] 10766
```

## Are there differences in activity patterns between weekdays and weekends?
