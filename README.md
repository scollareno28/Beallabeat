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
head(daily_activity)
colnames(daily_activity)
glimpse(daily_activity)
head(daily_calories)
glimpse(daily_calories)
head(sleep_day)
glimpse(sleep_day)
head(daily_intensities)
glimpse(daily_intensities)
head(weight_log)

##Every data frame has an ID column. This can be used in order to merge datasets

##How many distinct users in each frame?
n_distinct(daily_activity$Id)
n_distinct(sleep_day$Id)
n_distinct(daily_calories$Id)
n_distinct(daily_intensities$Id)
n_distinct(weight_log$Id)

##There aren't the same number of distinct users for each data frame.

##How many observations are there in each data frame
nrow(daily_activity)
nrow(sleep_day)
nrow(daily_calories)
nrow(daily_intensities)
nrow(weight_log)

##Calories, intensity, and daily activity all have 940 rows

##Summary statistics
daily_activity %>%  
  select(TotalSteps,
         TotalDistance,
         SedentaryMinutes) %>%
  summary()

sleep_day %>%  
  select(TotalSleepRecords,
         TotalMinutesAsleep,
         TotalTimeInBed) %>%
  summary()

weight_log %>%  
  select(WeightPounds,
         BMI) %>%
  summary()

##What is the relationship between steps and sedentary minutes?
ggplot(data=daily_activity, aes(x=TotalSteps, y=SedentaryMinutes, color = Calories)) + geom_point()

##What about steps and calories burned?
ggplot(data=daily_activity, aes(x=TotalSteps, y = Calories))+ geom_point() + stat_smooth(method=lm)

##Lets examine how sleep might affect calories burned
combined_data <- merge(sleep_day, daily_activity, by="Id")
n_distinct(combined_data$Id)
ggplot(data=combined_data, aes(x=TotalMinutesAsleep, y = Calories))+ geom_point()

##What about intense workouts and calories burned?
ggplot(data = daily_activity, aes(x=VeryActiveMinutes, y=Calories)) + geom_point() + stat_smooth(method = lm)
