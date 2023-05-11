# sql
Analyses using SQL
##Will begin by determining the number of participants
SELECT DISTINCT
  Id
FROM `sql-practce.fitbit_study.dailyactivity_merged`
#Participants = 33#
#Determining how many participants tracked weight data#
SELECT DISTINCT
  Id
FROM fitbit_study.weight_data
#Only 8 participants tracked weight data. Due to low number, weight Data will be omitted from final analysis.#
#Determining how many participants tracked sleep data#
SELECT DISTINCT
  Id
FROM fitbit_study.sleep_data
#24 participants tracked sleep data.#
#Next chunk wil return average sleep time and time spent in bed. Group by user ID
SELECT
  Id,
  AVG (TotalMinutesAsleep) AS AVG_Mins_Asleep,
  AVG (TotalTimeInBed) AS AVG_Time_in_Bed
FROM fitbit_study.sleep_data
GROUP BY Id
#Next chunk will return average veryactiveminutes and average calories burned. Group by user ID#
SELECT
  Id,
  AVG (VeryActiveMinutes) AS exercise_mins,
  AVG (Calories) AS Calories_burned
FROM `sql-practce.fitbit_study.dailyactivity_merged`
GROUP BY Id
