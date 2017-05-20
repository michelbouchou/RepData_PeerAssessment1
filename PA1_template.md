# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
library("ggplot2")
activity <- read.csv("activity.csv")
```

## What is mean total number of steps taken per day?


```r
activity.nna <- activity[!is.na(activity$steps),]
nb.steps <- aggregate(x = activity.nna$steps, by = list(activity.nna$date), FUN = sum)
qplot(as.Date(nb.steps$Group.1), nb.steps$x) + 
    geom_bar(stat = "identity") + 
    labs(title = "Total number of steps taken per day",
         x = "Time in days",
         y = "Number of steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

```r
mean(nb.steps$x)
```

```
## [1] 10766.19
```

```r
median(nb.steps$x)
```

```
## [1] 10765
```

## What is the average daily activity pattern?


```r
av.steps.int <- aggregate(x = activity.nna$steps, by = list(activity.nna$interval), FUN = mean)
ggplot(data = av.steps.int, aes(x = Group.1, y = x)) +
    geom_line() +
    labs(title = "Average daily activity pattern",
         x = "Average of steps",
         y = "Interval")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
