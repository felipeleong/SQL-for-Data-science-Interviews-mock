## MOCK 8
Our goal is to develop a naive forecast for a new metric called monthly 'distance per dolar' defined as the:
(distance_to_traVel/monetary_cost) in our dataset and measure its accuracy. Use RSME to evaluate accuracy.

````SQL
WITH BASE AS (
	SELECT 
		DATE_TRUNC('MONTH',REQUEST_DATE)::DATE AS MONTH_YEAR,
		SUM(distance_to_travel)/SUM(monetary_cost) AS DISTANCE_PER_DOLAR_ACTAL
	FROM interviews.request_logs
	GROUP BY 1
)
, MODEL AS (
	SELECT *,
		LAG(DISTANCE_PER_DOLAR_ACTAL,1) OVER(ORDER BY MONTH_YEAR) AS DISTANCE_PER_DOLAR_MODEL
	FROM BASE
)--SELECT * FROM MODEL
SELECT  
	SQRT(AVG(POWER(DISTANCE_PER_DOLAR_ACTAL-DISTANCE_PER_DOLAR_MODEL,2))) AS RSME
FROM MODEL;
````
Answer: 
| rsme                 |
|----------------------|
| 0.2580477234953606   |
