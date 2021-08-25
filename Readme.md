# Bellabeat
Capstone Project for Data Analytics Certificate
```{r}
install.packages('tidyverse')
library(tidyverse)
```
##After uploading datasets, we rename them for ease of use
```{r}
daily_activity <- read.csv("dailyActivity_merged.csv")
daily_calories <- read.csv("dailyCalories_merged.csv")
sleep_day <- read.csv("sleepDay_merged.csv")
daily_intensities <- read.csv("dailyIntensities_merged.csv")
weight_log <- read.csv("weightLogInfo_merged.csv")
```
##Preview tables 
```{r}
head(daily_activity)
          Id ActivityDate TotalSteps TotalDistance TrackerDistance
1 1503960366    4/12/2016      13162          8.50            8.50
2 1503960366    4/13/2016      10735          6.97            6.97
3 1503960366    4/14/2016      10460          6.74            6.74
4 1503960366    4/15/2016       9762          6.28            6.28
5 1503960366    4/16/2016      12669          8.16            8.16
6 1503960366    4/17/2016       9705          6.48            6.48
  LoggedActivitiesDistance VeryActiveDistance ModeratelyActiveDistance
1                        0               1.88                     0.55
2                        0               1.57                     0.69
3                        0               2.44                     0.40
4                        0               2.14                     1.26
5                        0               2.71                     0.41
6                        0               3.19                     0.78
  LightActiveDistance SedentaryActiveDistance VeryActiveMinutes FairlyActiveMinutes
1                6.06                       0                25                  13
2                4.71                       0                21                  19
3                3.91                       0                30                  11
4                2.83                       0                29                  34
5                5.04                       0                36                  10
6                2.51                       0                38                  20
  LightlyActiveMinutes SedentaryMinutes Calories
1                  328              728     1985
2                  217              776     1797
3                  181             1218     1776
4                  209              726     1745
5                  221              773     1863
6                  164              539     1728
colnames(daily_activity)
 [1] "Id"                       "ActivityDate"             "TotalSteps"              
 [4] "TotalDistance"            "TrackerDistance"          "LoggedActivitiesDistance"
 [7] "VeryActiveDistance"       "ModeratelyActiveDistance" "LightActiveDistance"     
[10] "SedentaryActiveDistance"  "VeryActiveMinutes"        "FairlyActiveMinutes"     
[13] "LightlyActiveMinutes"     "SedentaryMinutes"         "Calories"                
glimpse(daily_activity)
Rows: 940
Columns: 15
$ Id                       <dbl> 1503960366, 1503960366, 1503960366, 1503960366, 15…
$ ActivityDate             <chr> "4/12/2016", "4/13/2016", "4/14/2016", "4/15/2016"…
$ TotalSteps               <int> 13162, 10735, 10460, 9762, 12669, 9705, 13019, 155…
$ TotalDistance            <dbl> 8.50, 6.97, 6.74, 6.28, 8.16, 6.48, 8.59, 9.88, 6.…
$ TrackerDistance          <dbl> 8.50, 6.97, 6.74, 6.28, 8.16, 6.48, 8.59, 9.88, 6.…
$ LoggedActivitiesDistance <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
$ VeryActiveDistance       <dbl> 1.88, 1.57, 2.44, 2.14, 2.71, 3.19, 3.25, 3.53, 1.…
$ ModeratelyActiveDistance <dbl> 0.55, 0.69, 0.40, 1.26, 0.41, 0.78, 0.64, 1.32, 0.…
$ LightActiveDistance      <dbl> 6.06, 4.71, 3.91, 2.83, 5.04, 2.51, 4.71, 5.03, 4.…
$ SedentaryActiveDistance  <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
$ VeryActiveMinutes        <int> 25, 21, 30, 29, 36, 38, 42, 50, 28, 19, 66, 41, 39…
$ FairlyActiveMinutes      <int> 13, 19, 11, 34, 10, 20, 16, 31, 12, 8, 27, 21, 5, …
$ LightlyActiveMinutes     <int> 328, 217, 181, 209, 221, 164, 233, 264, 205, 211, …
$ SedentaryMinutes         <int> 728, 776, 1218, 726, 773, 539, 1149, 775, 818, 838…
$ Calories                 <int> 1985, 1797, 1776, 1745, 1863, 1728, 1921, 2035, 17…
head(daily_calories)
          Id ActivityDay Calories
1 1503960366   4/12/2016     1985
2 1503960366   4/13/2016     1797
3 1503960366   4/14/2016     1776
4 1503960366   4/15/2016     1745
5 1503960366   4/16/2016     1863
6 1503960366   4/17/2016     1728
glimpse(daily_calories)
Rows: 940
Columns: 3
$ Id          <dbl> 1503960366, 1503960366, 1503960366, 1503960366, 1503960366, 150…
$ ActivityDay <chr> "4/12/2016", "4/13/2016", "4/14/2016", "4/15/2016", "4/16/2016"…
$ Calories    <int> 1985, 1797, 1776, 1745, 1863, 1728, 1921, 2035, 1786, 1775, 182…
head(sleep_day)
          Id              SleepDay TotalSleepRecords TotalMinutesAsleep
1 1503960366 4/12/2016 12:00:00 AM                 1                327
2 1503960366 4/13/2016 12:00:00 AM                 2                384
3 1503960366 4/15/2016 12:00:00 AM                 1                412
4 1503960366 4/16/2016 12:00:00 AM                 2                340
5 1503960366 4/17/2016 12:00:00 AM                 1                700
6 1503960366 4/19/2016 12:00:00 AM                 1                304
  TotalTimeInBed
1            346
2            407
3            442
4            367
5            712
6            320
glimpse(sleep_day)
Rows: 413
Columns: 5
$ Id                 <dbl> 1503960366, 1503960366, 1503960366, 1503960366, 15039603…
$ SleepDay           <chr> "4/12/2016 12:00:00 AM", "4/13/2016 12:00:00 AM", "4/15/…
$ TotalSleepRecords  <int> 1, 2, 1, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
$ TotalMinutesAsleep <int> 327, 384, 412, 340, 700, 304, 360, 325, 361, 430, 277, 2…
$ TotalTimeInBed     <int> 346, 407, 442, 367, 712, 320, 377, 364, 384, 449, 323, 2…
head(daily_intensities)
          Id ActivityDay SedentaryMinutes LightlyActiveMinutes FairlyActiveMinutes
1 1503960366   4/12/2016              728                  328                  13
2 1503960366   4/13/2016              776                  217                  19
3 1503960366   4/14/2016             1218                  181                  11
4 1503960366   4/15/2016              726                  209                  34
5 1503960366   4/16/2016              773                  221                  10
6 1503960366   4/17/2016              539                  164                  20
  VeryActiveMinutes SedentaryActiveDistance LightActiveDistance
1                25                       0                6.06
2                21                       0                4.71
3                30                       0                3.91
4                29                       0                2.83
5                36                       0                5.04
6                38                       0                2.51
  ModeratelyActiveDistance VeryActiveDistance
1                     0.55               1.88
2                     0.69               1.57
3                     0.40               2.44
4                     1.26               2.14
5                     0.41               2.71
6                     0.78               3.19
glimpse(daily_intensities)
Rows: 940
Columns: 10
$ Id                       <dbl> 1503960366, 1503960366, 1503960366, 1503960366, 15…
$ ActivityDay              <chr> "4/12/2016", "4/13/2016", "4/14/2016", "4/15/2016"…
$ SedentaryMinutes         <int> 728, 776, 1218, 726, 773, 539, 1149, 775, 818, 838…
$ LightlyActiveMinutes     <int> 328, 217, 181, 209, 221, 164, 233, 264, 205, 211, …
$ FairlyActiveMinutes      <int> 13, 19, 11, 34, 10, 20, 16, 31, 12, 8, 27, 21, 5, …
$ VeryActiveMinutes        <int> 25, 21, 30, 29, 36, 38, 42, 50, 28, 19, 66, 41, 39…
$ SedentaryActiveDistance  <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
$ LightActiveDistance      <dbl> 6.06, 4.71, 3.91, 2.83, 5.04, 2.51, 4.71, 5.03, 4.…
$ ModeratelyActiveDistance <dbl> 0.55, 0.69, 0.40, 1.26, 0.41, 0.78, 0.64, 1.32, 0.…
$ VeryActiveDistance       <dbl> 1.88, 1.57, 2.44, 2.14, 2.71, 3.19, 3.25, 3.53, 1.…
head(weight_log)
          Id                  Date WeightKg WeightPounds Fat   BMI IsManualReport
1 1503960366  5/2/2016 11:59:59 PM     52.6     115.9631  22 22.65           True
2 1503960366  5/3/2016 11:59:59 PM     52.6     115.9631  NA 22.65           True
3 1927972279  4/13/2016 1:08:52 AM    133.5     294.3171  NA 47.54          False
4 2873212765 4/21/2016 11:59:59 PM     56.7     125.0021  NA 21.45           True
5 2873212765 5/12/2016 11:59:59 PM     57.3     126.3249  NA 21.69           True
6 4319703577 4/17/2016 11:59:59 PM     72.4     159.6147  25 27.45           True
         LogId
1 1.462234e+12
2 1.462320e+12
3 1.460510e+12
4 1.461283e+12
5 1.463098e+12
6 1.460938e+12
```
##How many distinct users in each frame?
```{r}
n_distinct(daily_activity$Id)
[1] 33
n_distinct(sleep_day$Id)
[1] 24
n_distinct(daily_calories$Id)
[1] 33
n_distinct(daily_intensities$Id)
[1] 33
n_distinct(weight_log$Id)
[1] 8
```
##How many observations are there in each data frame
```{r}
nrow(daily_activity)
[1] 940
nrow(sleep_day)
[1] 413
nrow(daily_calories)
[1] 940
nrow(daily_intensities)
[1] 940
nrow(weight_log)
[1] 67
```{r}
##Summary statistics
daily_activity %>%  
  select(TotalSteps,
          TotalDistance,
         SedentaryMinutes) %>%
   summary()
   TotalSteps    TotalDistance    SedentaryMinutes
 Min.   :    0   Min.   : 0.000   Min.   :   0.0  
 1st Qu.: 3790   1st Qu.: 2.620   1st Qu.: 729.8  
 Median : 7406   Median : 5.245   Median :1057.5  
 Mean   : 7638   Mean   : 5.490   Mean   : 991.2  
 3rd Qu.:10727   3rd Qu.: 7.713   3rd Qu.:1229.5  
 Max.   :36019   Max.   :28.030   Max.   :1440.0  
 sleep_day %>%  
   select(TotalSleepRecords,
          TotalMinutesAsleep,
          TotalTimeInBed) %>%
   summary()
 TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :1.000     Min.   : 58.0      Min.   : 61.0  
 1st Qu.:1.000     1st Qu.:361.0      1st Qu.:403.0  
 Median :1.000     Median :433.0      Median :463.0  
 Mean   :1.119     Mean   :419.5      Mean   :458.6  
 3rd Qu.:1.000     3rd Qu.:490.0      3rd Qu.:526.0  
 Max.   :3.000     Max.   :796.0      Max.   :961.0  
 weight_log %>%  
   select(WeightPounds,
          BMI) %>%
   summary()
  WeightPounds        BMI       
 Min.   :116.0   Min.   :21.45  
 1st Qu.:135.4   1st Qu.:23.96  
 Median :137.8   Median :24.39  
 Mean   :158.8   Mean   :25.19  
 3rd Qu.:187.5   3rd Qu.:25.56  
 Max.   :294.3   Max.   :47.54 
 ```
 ##What is the relationship between steps and sedentary minutes?
 ```{r}
 ggplot(data=daily_activity, aes(x=TotalSteps, y=SedentaryMinutes)) + geom_point()




 
 ```
 ![image](https://user-images.githubusercontent.com/89541893/130853287-f85e86af-0942-4b33-988b-e6b8783c991a.png)

 ##What is the relationship between steps and sedentary minutes?
 ```{r}
 ggplot(data=daily_activity, aes(x=TotalSteps, y=SedentaryMinutes, color = Calories)) + geom_point()
 
 ```
 ##What about steps and calories burned?
 ```{r}
 ggplot(data=daily_activity, aes(x=TotalSteps, y = Calories))+ geom_point() + stat_smooth(method=lm)
`geom_smooth()` using formula 'y ~ x'

```
 ##Lets examine how sleep might affect calories burned
 ```{r}
 combined_data <- merge(sleep_day, daily_activity, by="Id")
 n_distinct(combined_data$Id)
[1] 24
 ggplot(data=combined_data, aes(x=TotalMinutesAsleep, y = Calories))+ geom_point() + stat_smooth(method=lm)
`geom_smooth()` using formula 'y ~ x'
 ggplot(data=combined_data, aes(x=TotalMinutesAsleep, y = Calories))+ geom_point()
 ggplot(data=combined_data, aes(x=TotalMinutesAsleep, y = Calories))
 ggplot(data=combined_data, aes(x=TotalMinutesAsleep, y = Calories))+ geom_point()
 ```
 ##What about intense workouts and calories burned?
 ```{r}
 
 
 ##What about intense workouts and calories burned?
 ggplot(data = daily_activity, aes(x=VeryActiveMinutes, y=Calories)) + geom_point() + stat_smooth(method = lm)
`geom_smooth()` using formula 'y ~ x'
 
```
