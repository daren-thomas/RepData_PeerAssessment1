# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

Read in the `activity.csv` file:


```r
library(lubridate)
```

```
## Warning: package 'lubridate' was built under R version 3.2.3
```

```r
activity = read.csv('activity.csv', na.strings = "NA")
activity$date <- ymd(activity$date)
head(activity)
```

```
##   steps       date interval
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
## 4    NA 2012-10-01       15
## 5    NA 2012-10-01       20
## 6    NA 2012-10-01       25
```


## What is mean total number of steps taken per day?


```r
library(dplyr)
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:lubridate':
## 
##     intersect, setdiff, union
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
daily.activity <- group_by(activity, date) %>% summarize(total = sum(steps))
```

1. Histogram of the total number of steps taken each day 
(choosing a `binwidth=1000` based on experience with my Fitbit Surge...)


```r
library(ggplot2)
qplot(daily.activity$total, binwidth=1000)
```

```
## Warning: Removed 8 rows containing non-finite values (stat_bin).
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png)

We see that hitting 10'000 steps a day (and above) was achieved quite often. Yay! I wish *my* Fitbit stats looked like that...


2. *mean* and *median* total number of steps taken each day

Let's add some more statistical punch to the observation above... 

- The mean total number of steps taken each day was 

```r
mean(daily.activity$total, na.rm=TRUE)
```

```
## [1] 10766.19
```
- and the median was 

```r
median(daily.activity$total, na.rm=TRUE)
```

```
## [1] 10765
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
