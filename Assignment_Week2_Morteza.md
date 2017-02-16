# Assignment_Week2_Morteza
Morteza  
February 13, 2017  

Part 1: Loading and preprocessing the data:


```r
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 3.2.5
```

```r
activity<-read.csv("./activity.csv", header = TRUE)
str(activity)
```

```
## 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```

Part 2: What is mean total number of steps taken per day?

```r
agg_activity_mean<-aggregate(steps~date,activity,mean)
agg_activity_mean
```

```
##          date      steps
## 1  2012-10-02  0.4375000
## 2  2012-10-03 39.4166667
## 3  2012-10-04 42.0694444
## 4  2012-10-05 46.1597222
## 5  2012-10-06 53.5416667
## 6  2012-10-07 38.2465278
## 7  2012-10-09 44.4826389
## 8  2012-10-10 34.3750000
## 9  2012-10-11 35.7777778
## 10 2012-10-12 60.3541667
## 11 2012-10-13 43.1458333
## 12 2012-10-14 52.4236111
## 13 2012-10-15 35.2048611
## 14 2012-10-16 52.3750000
## 15 2012-10-17 46.7083333
## 16 2012-10-18 34.9166667
## 17 2012-10-19 41.0729167
## 18 2012-10-20 36.0937500
## 19 2012-10-21 30.6284722
## 20 2012-10-22 46.7361111
## 21 2012-10-23 30.9652778
## 22 2012-10-24 29.0104167
## 23 2012-10-25  8.6527778
## 24 2012-10-26 23.5347222
## 25 2012-10-27 35.1354167
## 26 2012-10-28 39.7847222
## 27 2012-10-29 17.4236111
## 28 2012-10-30 34.0937500
## 29 2012-10-31 53.5208333
## 30 2012-11-02 36.8055556
## 31 2012-11-03 36.7048611
## 32 2012-11-05 36.2465278
## 33 2012-11-06 28.9375000
## 34 2012-11-07 44.7326389
## 35 2012-11-08 11.1770833
## 36 2012-11-11 43.7777778
## 37 2012-11-12 37.3784722
## 38 2012-11-13 25.4722222
## 39 2012-11-15  0.1423611
## 40 2012-11-16 18.8923611
## 41 2012-11-17 49.7881944
## 42 2012-11-18 52.4652778
## 43 2012-11-19 30.6979167
## 44 2012-11-20 15.5277778
## 45 2012-11-21 44.3993056
## 46 2012-11-22 70.9270833
## 47 2012-11-23 73.5902778
## 48 2012-11-24 50.2708333
## 49 2012-11-25 41.0902778
## 50 2012-11-26 38.7569444
## 51 2012-11-27 47.3819444
## 52 2012-11-28 35.3576389
## 53 2012-11-29 24.4687500
```
Calculate the total number of steps taken per day?


```r
agg_activity_sum<-aggregate(steps~date,activity,sum)
agg_activity_sum
```

```
##          date steps
## 1  2012-10-02   126
## 2  2012-10-03 11352
## 3  2012-10-04 12116
## 4  2012-10-05 13294
## 5  2012-10-06 15420
## 6  2012-10-07 11015
## 7  2012-10-09 12811
## 8  2012-10-10  9900
## 9  2012-10-11 10304
## 10 2012-10-12 17382
## 11 2012-10-13 12426
## 12 2012-10-14 15098
## 13 2012-10-15 10139
## 14 2012-10-16 15084
## 15 2012-10-17 13452
## 16 2012-10-18 10056
## 17 2012-10-19 11829
## 18 2012-10-20 10395
## 19 2012-10-21  8821
## 20 2012-10-22 13460
## 21 2012-10-23  8918
## 22 2012-10-24  8355
## 23 2012-10-25  2492
## 24 2012-10-26  6778
## 25 2012-10-27 10119
## 26 2012-10-28 11458
## 27 2012-10-29  5018
## 28 2012-10-30  9819
## 29 2012-10-31 15414
## 30 2012-11-02 10600
## 31 2012-11-03 10571
## 32 2012-11-05 10439
## 33 2012-11-06  8334
## 34 2012-11-07 12883
## 35 2012-11-08  3219
## 36 2012-11-11 12608
## 37 2012-11-12 10765
## 38 2012-11-13  7336
## 39 2012-11-15    41
## 40 2012-11-16  5441
## 41 2012-11-17 14339
## 42 2012-11-18 15110
## 43 2012-11-19  8841
## 44 2012-11-20  4472
## 45 2012-11-21 12787
## 46 2012-11-22 20427
## 47 2012-11-23 21194
## 48 2012-11-24 14478
## 49 2012-11-25 11834
## 50 2012-11-26 11162
## 51 2012-11-27 13646
## 52 2012-11-28 10183
## 53 2012-11-29  7047
```

Make a histogram of the total number of steps taken each day?


```r
g<-ggplot(data=agg_activity_sum, aes(steps))
g+geom_histogram(breaks=seq(0,21200, by=2050), col="red", fill="green", alpha=0.2)
```

![](Assignment_Week2_Morteza_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

Calculate and report the mean and median of the total number of steps taken per day?

```r
summary(agg_activity_sum)
```

```
##          date        steps      
##  2012-10-02: 1   Min.   :   41  
##  2012-10-03: 1   1st Qu.: 8841  
##  2012-10-04: 1   Median :10765  
##  2012-10-05: 1   Mean   :10766  
##  2012-10-06: 1   3rd Qu.:13294  
##  2012-10-07: 1   Max.   :21194  
##  (Other)   :47
```

Part 3: What is the average daily activity pattern?

Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

```r
agg_activity_interval<-aggregate(steps~interval, activity, mean)
g<-ggplot(data=agg_activity_interval, aes(interval,steps))
g+geom_line()+labs(x="5 Minutes Interval", y="Average Number of Steps taken",title="Average Number of Steps per Each Interval")+theme(plot.title = element_text(hjust = 0.5))+scale_x_continuous(breaks = seq(0,3000,by=500))
```

![](Assignment_Week2_Morteza_files/figure-html/unnamed-chunk-6-1.png)<!-- -->
Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```r
agg_activity_interval[which.max(agg_activity_interval$steps),]
```

```
##     interval    steps
## 104      835 206.1698
```

Part 4: Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NAs)

```r
sapply(activity,function(x)sum(is.na(x)))
```

```
##    steps     date interval 
##     2304        0        0
```
Create a new dataset that is equal to the original dataset but with the missing data filled in.
My strategy for imputing missing values in Activity dataset is replacing them by the average of number of steps during the same interval acress all days,i.e., by using the steps' values in agg_activity_interval.

```r
activity_Missing_Imputed<-activity
for (i in 1:dim(activity_Missing_Imputed)[1])
if (is.na(activity_Missing_Imputed[i,1]))
activity_Missing_Imputed[i,1]=agg_activity_interval[which(agg_activity_interval[,1]==activity_Missing_Imputed[i,3]),2]
sapply(activity_Missing_Imputed,function(x)sum(is.na(x)))
```

```
##    steps     date interval 
##        0        0        0
```

Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?

```r
agg_activity_sum_2<-aggregate(steps~date,activity_Missing_Imputed,sum)
summary(agg_activity_sum_2)
```

```
##          date        steps      
##  2012-10-01: 1   Min.   :   41  
##  2012-10-02: 1   1st Qu.: 9819  
##  2012-10-03: 1   Median :10766  
##  2012-10-04: 1   Mean   :10766  
##  2012-10-05: 1   3rd Qu.:12811  
##  2012-10-06: 1   Max.   :21194  
##  (Other)   :55
```

```r
g<-ggplot(data=agg_activity_sum_2, aes(steps))
g+geom_histogram(breaks=seq(0,21200, by=2050), col="red", fill="green", alpha=0.2)
```

![](Assignment_Week2_Morteza_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

Part 5: Are there differences in activity patterns between weekdays and weekends?

Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis). See the README file in the GitHub repository to see an example of what this plot should look like using simulated data.

```r
library(plyr);library(dplyr)
```

```
## Warning: package 'plyr' was built under R version 3.2.5
```

```
## Warning: package 'dplyr' was built under R version 3.2.5
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:plyr':
## 
##     arrange, count, desc, failwith, id, mutate, rename, summarise,
##     summarize
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
activity_Missing_Imputed$day<-weekdays(as.Date(activity_Missing_Imputed$date))
activity_Missing_Imputed$day_cat<-mapvalues(activity_Missing_Imputed$day, from = c("Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"),to=c("weekday","weekday","weekday","weekday","weekday","weekend","weekend"))
agg_activity_interval_2<-aggregate(steps~interval+day_cat, activity_Missing_Imputed, mean)
g<-ggplot(data=agg_activity_interval_2, aes(interval,steps))
g+geom_line()+facet_grid(day_cat~., margins = TRUE)+labs(x="5 Minutes Interval", y="Average Number of Steps taken",title="Average Number of Steps per Each Interval")+theme(plot.title = element_text(hjust = 0.5))+scale_x_continuous(breaks = seq(0,3000,by=500))
```

![](Assignment_Week2_Morteza_files/figure-html/unnamed-chunk-11-1.png)<!-- -->





