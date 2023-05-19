## MOCK 5 
## for each date find the difference between the distance per dollar for that date and the average distance per dollar for that year/month
/*DISTANCE PER DOLLAR = DISTANCE TRAVELED/COST RIDE
FINDE THE DIFFERENCE AS AN ABSOLUTE VALUE AND ROUND IT TO THE SECOND DECIMAL PLACE
ORDER THE RESULT BY REQUEST DATE
This table does not exsits*/
````SQL
SELECT
	request_date,
	ROUND(ABS(distance_to_travel / monetary_cost-
	AVG(distance_to_travel/monetary_cost) OVER(PARTITION BY DATE_TRUNC('MONTH',request_date)ORDER BY DATE_TRUNC('MONTH',request_date)))::NUMERIC,2) 
		AS difference
FROM interviews.request_logs;
````
Answer: 
| request_date | difference |
|--------------|------------|
| 2020-01-07   | 0.65       |
| 2020-01-09   | 0.13       |
| 2020-01-11   | 0.92       |
| 2020-01-21   | 0.15       |
| 2020-02-07   | 0.03       |
| 2020-02-09   | 0.09       |
| 2020-02-11   | 0.22       |
| 2020-02-21   | 0.11       |
| 2020-03-07   | 0.65       |
| 2020-03-09   | 0.13       |
| 2020-03-11   | 0.92       |
| 2020-03-21   | 0.15       |
| 2020-04-07   | 0.29       |
| 2020-04-09   | 0.80       |
| 2020-04-11   | 0.26       |
| 2020-04-21   | 0.25       |
