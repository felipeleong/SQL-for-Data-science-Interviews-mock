## MOCK 1
## Average event per day 
Success rate = number of post / number of enter
````sql
SELECT 
	EXTRACT(DOW FROM CREATED_AT) AS DOW,
	ROUND(COUNT(CASE WHEN EVENT_NAME = 'post' THEN 1 ELSE NULL END)*1.00/
	COUNT(CASE WHEN EVENT_NAME = 'enter' THEN 1 ELSE NULL END),2)*100 AS SUCCES_RATE
FROM interviews.post_events
GROUP BY 1
ORDER BY 2 ASC;
````
##Answer: 
| dow | success_rate |
|-----|-------------|
| 3   | 0.00        |
| 1   | 33.00       |
| 2   | 50.00       |

## MOCK2
## FIND THE DATE WITH THE HIGHEST TOTAL ENERGY CONSUMPTION FROM OUR DATA CENTERS
OUTPUT THE DATE ALONG WITH TOTAL ENERGY CONSUMPTION ACROSS ALL DATA CENTERS
````sql
WITH CONT AS (
	SELECT * FROM interviews.eu_energy 
	UNION ALL
	SELECT * FROM interviews.asia_energy 
	UNION ALL 
	SELECT * FROM interviews.na_energy 
)
SELECT 
	DATE,
	SUM(CONSUMPTION) AS TOTAL_ENERGY_CONSUMPTION
FROM CONT
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;
## We can create a temp table to
--Create table
CREATE TEMP TABLE TEMP_ENERGY (
DATE DATE,
CONSUMPTION INT	
);
--Insert the data
INSERT INTO TEMP_ENERGY 
SELECT * FROM interviews.eu_energy 
UNION ALL
SELECT * FROM interviews.asia_energy 
UNION ALL 
SELECT * FROM interviews.na_energy;
--Query:
SELECT 
	DATE,SUM(CONSUMPTION)
FROM TEMP_ENERGY 
GROUP BY 1
ORDER BY 2 DESC
FETCH FIRST 1 ROW ONLY;
````
## Answer: 
| date       | total_energy_consumption |
|------------|-------------------------|
| 2019-06-06 | 83                      |

