


# DataCamp SQL Subquerying Inside WHERE Clauses


## Introduction 
This project demonstrates the use of SQL subqueries within WHERE clauses 
to filter and extract meaningful insights from relational datasets containing 
global population, country, and city statistics. Key areas of analysis include 
urban population size, life expectancy, and fertility rates across
countries and regions. These queries were written as part of my 
ongoing SQL training through DataCamp.

### TASK: Calculate the average life expectancy from the populations table. Filter records to only represent statistics from 2015. Use this calculation to filter populations for all records where life_expectancy is 1.15 times higher than average.


## Query
```
SELECT *
FROM populations
WHERE year = 2015
AND life_expectancy > 1.15 *(SELECT AVG(life_expectancy)FROM populations WHERE year = 2015);
```

## Results

avg
71.6763415481105 


| pop_id | country_code | year | fertility_rate | life_expectancy | size |
|:------:|:------------:|:----:|:--------------:|:---------------:|:----:|
| 21 | AUS | 2015 | 1.833 | 82.45122 | 23789752 |
| 376 | CHE | 2015 | 1.54 | 83.19756 | 8281430 |
| 356 | ESP | 2015 | 1.32 | 83.380486 | 46443992 |
| 134 | FRA | 2015 | 2.01 | 82.67073 | 66538392 |
| 170 | HKG | 2015 | 1.195 | 84.278046 | 7305700 |
| 174 | ISL | 2015 | 1.93 | 82.86098 | 330815 |
| 190 | ITA | 2015 | 1.37 | 83.49024 | 60730584 |
| 194 | JPN | 2015 | 1.46 | 83.84366 | 126958470 |
| 340 | SGP | 2015 | 1.24 | 82.59512 | 5535002 |
| 374 | SWE | 2015 | 1.88 | 82.551216 | 9799186 |





### TASK: Return the name, country_code and urbanarea_pop for all capital cities without using aliases.


## Query
```
Select
name,
country_code,
urbanarea_pop
FROM cities
# Filter using a subquery on the countries table
WHERE name IN
(SELECT capital
FROM countries)
ORDER BY urbanarea_pop DESC;
```
## Result
| name | country_code | urbanarea_pop |
|:----:|:------------:|:-------------:|
| Beijing | CHN | 21516000 |
| Dhaka | BGD | 14543124 |
| Tokyo | JPN | 13513734 |
| Moscow | RUS | 12197596 |
| Cairo | EGY | 10230350 |
