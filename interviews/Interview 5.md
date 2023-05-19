## MOCK 5 
## for each date find the difference between the distance per dollar for that date and the average distance per dollar for that year/month
/*DISTANCE PER DOLLAR = DISTANCE TRAVELED/COST RIDE
FINDE THE DIFFERENCE AS AN ABSOLUTE VALUE AND ROUND IT TO THE SECOND DECIMAL PLACE
ORDER THE RESULT BY REQUEST DATE
This table does not exsits*/
--uber_rides
request_id int
request_date datetime
request_status varchar ('canceled_by_driver','canceled_by_client','success')
distance_to_travel float
monetary_cost float
driver_to_client_distance float
--------------------------
````SQL
SELECT 
	REQUEST_DATE AS DATE,
	ROUND(ABS(SUM(DISTANCE_TO_TRAVEL / MONETARY_COST) - AVG(DISTANCE_TO_TRAVEL / MONETARY_COST)),2) AS DIFFERENCE
FROM UBER_RIDES
WHERE REQUEST_STATUS = 'success'
GROUP BY 1
ORDER BY 1;
````








