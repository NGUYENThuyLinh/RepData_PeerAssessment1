Introduction
------------

It is now possible to collect a large amount of data about personal
movement using activity monitoring devices such as a Fitbit, Nike
Fuelband, or Jawbone Up. These type of devices are part of the
“quantified self” movement – a group of enthusiasts who take
measurements about themselves regularly to improve their health, to find
patterns in their behavior, or because they are tech geeks. But these
data remain under-utilized both because the raw data are hard to obtain
and there is a lack of statistical methods and software for processing
and interpreting the data.

This assignment makes use of data from a personal activity monitoring
device. This device collects data at 5 minute intervals through out the
day. The data consists of two months of data from an anonymous
individual collected during the months of October and November, 2012 and
include the number of steps taken in 5 minute intervals each day.

The data for this assignment can be downloaded from the course web site:

-   Dataset: [Activity monitoring
    data](https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip)

The variables included in this dataset are:

steps: Number of steps taking in a 5-minute interval (missing values are
coded as 𝙽𝙰) </br> date: The date on which the measurement was taken in
YYYY-MM-DD format </br> interval: Identifier for the 5-minute interval
in which measurement was taken </br> The dataset is stored in a
comma-separated-value (CSV) file and there are a total of 17,568
observations in this dataset.

1. Code for reading in the dataset and/or processing the data
-------------------------------------------------------------

Dowload, unzip and read data.

``` r
fileUrl<-"https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip"
download.file(fileUrl,destfile="./repdata-data-activity.zip")
unzip(zipfile="repdata-data-activity.zip")
data<-read.csv("./activity.csv")
```

2. Histogram of the total number of steps taken each day
--------------------------------------------------------

Calculate the total number of steps taken per day by tapply function
then create the histogram plot.

``` r
hist(as.table(tapply(data$steps,data$date,sum)),xlab="steps",col="blue",main="Total number of steps taken each day")
```

![](PA1_template_files/figure-markdown_github/unnamed-chunk-2-1.png)

3. Mean and median number of steps taken each day
-------------------------------------------------

Compute the mean and the median of the steps each day using tapply
function.

``` r
tapply(data$steps,data$date,mean)
```

    ## 2012-10-01 2012-10-02 2012-10-03 2012-10-04 2012-10-05 2012-10-06 2012-10-07 
    ##         NA  0.4375000 39.4166667 42.0694444 46.1597222 53.5416667 38.2465278 
    ## 2012-10-08 2012-10-09 2012-10-10 2012-10-11 2012-10-12 2012-10-13 2012-10-14 
    ##         NA 44.4826389 34.3750000 35.7777778 60.3541667 43.1458333 52.4236111 
    ## 2012-10-15 2012-10-16 2012-10-17 2012-10-18 2012-10-19 2012-10-20 2012-10-21 
    ## 35.2048611 52.3750000 46.7083333 34.9166667 41.0729167 36.0937500 30.6284722 
    ## 2012-10-22 2012-10-23 2012-10-24 2012-10-25 2012-10-26 2012-10-27 2012-10-28 
    ## 46.7361111 30.9652778 29.0104167  8.6527778 23.5347222 35.1354167 39.7847222 
    ## 2012-10-29 2012-10-30 2012-10-31 2012-11-01 2012-11-02 2012-11-03 2012-11-04 
    ## 17.4236111 34.0937500 53.5208333         NA 36.8055556 36.7048611         NA 
    ## 2012-11-05 2012-11-06 2012-11-07 2012-11-08 2012-11-09 2012-11-10 2012-11-11 
    ## 36.2465278 28.9375000 44.7326389 11.1770833         NA         NA 43.7777778 
    ## 2012-11-12 2012-11-13 2012-11-14 2012-11-15 2012-11-16 2012-11-17 2012-11-18 
    ## 37.3784722 25.4722222         NA  0.1423611 18.8923611 49.7881944 52.4652778 
    ## 2012-11-19 2012-11-20 2012-11-21 2012-11-22 2012-11-23 2012-11-24 2012-11-25 
    ## 30.6979167 15.5277778 44.3993056 70.9270833 73.5902778 50.2708333 41.0902778 
    ## 2012-11-26 2012-11-27 2012-11-28 2012-11-29 2012-11-30 
    ## 38.7569444 47.3819444 35.3576389 24.4687500         NA

``` r
tapply(data$steps,data$date,FUN=median)
```

    ## 2012-10-01 2012-10-02 2012-10-03 2012-10-04 2012-10-05 2012-10-06 2012-10-07 
    ##         NA          0          0          0          0          0          0 
    ## 2012-10-08 2012-10-09 2012-10-10 2012-10-11 2012-10-12 2012-10-13 2012-10-14 
    ##         NA          0          0          0          0          0          0 
    ## 2012-10-15 2012-10-16 2012-10-17 2012-10-18 2012-10-19 2012-10-20 2012-10-21 
    ##          0          0          0          0          0          0          0 
    ## 2012-10-22 2012-10-23 2012-10-24 2012-10-25 2012-10-26 2012-10-27 2012-10-28 
    ##          0          0          0          0          0          0          0 
    ## 2012-10-29 2012-10-30 2012-10-31 2012-11-01 2012-11-02 2012-11-03 2012-11-04 
    ##          0          0          0         NA          0          0         NA 
    ## 2012-11-05 2012-11-06 2012-11-07 2012-11-08 2012-11-09 2012-11-10 2012-11-11 
    ##          0          0          0          0         NA         NA          0 
    ## 2012-11-12 2012-11-13 2012-11-14 2012-11-15 2012-11-16 2012-11-17 2012-11-18 
    ##          0          0         NA          0          0          0          0 
    ## 2012-11-19 2012-11-20 2012-11-21 2012-11-22 2012-11-23 2012-11-24 2012-11-25 
    ##          0          0          0          0          0          0          0 
    ## 2012-11-26 2012-11-27 2012-11-28 2012-11-29 2012-11-30 
    ##          0          0          0          0         NA

4. Time series plot of the average number of steps taken
--------------------------------------------------------

Create the data frame meansteps contains the dates and the
correspondence average number of steps then plot them.

``` r
meansteps<-aggregate(list(Steps=data$steps),list(Date=data$date),mean)
meansteps$Date<-strptime(as.character(meansteps$Date),"%Y-%m-%d")
plot(meansteps$Date,meansteps$Steps,type="l",xlab="Date",ylab="Steps",main="Average number of steps taken each day")
```

![](PA1_template_files/figure-markdown_github/unnamed-chunk-4-1.png)

5. The 5-minute interval that, on average, contains the maximum number of steps
-------------------------------------------------------------------------------

Create the data frame steps\_interval contains the intervals and the
correspondence average number of step, take the interval that have the
biggest average step.

``` r
steps_interval<-aggregate(list(steps=data$steps),list(interval=data$interval),FUN=mean,na.rm=TRUE)
steps_interval$interval[steps_interval$steps==max(steps_interval$steps)]
```

    ## [1] 835

6. Code to describe and show a strategy for imputing missing data
-----------------------------------------------------------------

Create a table counting the number of missing value, and the percentage
of them

``` r
table(is.na(data$steps))
```

    ## 
    ## FALSE  TRUE 
    ## 15264  2304

``` r
prop.table(table(is.na(data$steps)))
```

    ## 
    ##     FALSE      TRUE 
    ## 0.8688525 0.1311475

We can probably impute the missing values by using the mean, the median,
or the mode of the 5-minute intervals. I used the mean.

``` r
newdata<-data
for (i in 1:nrow(newdata)){
  if (is.na(newdata$steps[i])==TRUE){
    newdata$steps[i]<-steps_interval$steps[steps_interval==data$interval[i]]
  }
}
```

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

    ## Warning in newdata$steps[i] <- steps_interval$steps[steps_interval ==
    ## data$interval[i]]: number of items to replace is not a multiple of replacement
    ## length

7. Histogram of the total number of steps taken each day after missing values are imputed
-----------------------------------------------------------------------------------------

``` r
hist(as.table(tapply(newdata$steps,newdata$date,sum)),xlab="steps",col="blue",main="Total number of steps taken each day")
```

![](PA1_template_files/figure-markdown_github/unnamed-chunk-8-1.png)

8. Panel plot comparing the average number of steps taken per 5-minute interval across weekdays and weekends
------------------------------------------------------------------------------------------------------------

Calculate the average number of steps taken per 5-minute interval for
weekdays and weekends, then create the panel plot to compare them

``` r
library(timeDate)
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.6.3

``` r
weekday<-as.vector(tapply(newdata$steps[isWeekend(strptime(as.character(newdata$date),"%Y-%m-%d"),wday=1:5)==F],
         newdata$interval[isWeekend(strptime(as.character(newdata$date),"%Y-%m-%d"),wday=1:5)==F],mean))
weekend<-as.vector(tapply(newdata$steps[isWeekend(strptime(as.character(newdata$date),"%Y-%m-%d"),wday=1:5)==T],
         newdata$interval[isWeekend(strptime(as.character(newdata$date),"%Y-%m-%d"),wday=1:5)==T],mean))
weekdays<-as.data.frame(cbind(steps=c(weekday,weekend),interval=rep(unique(newdata$interval),2),
          weekday=c(rep("weekday",288),rep("weekend",288))))
qplot(as.numeric(interval),as.numeric(steps),data=weekdays,facets=weekday~.,geom="line",col=weekday,
      xlab="interval",ylab="steps",main="Average number of steps taken per 5-minute interval weekdays-weekends")
```

![](PA1_template_files/figure-markdown_github/unnamed-chunk-9-1.png)
