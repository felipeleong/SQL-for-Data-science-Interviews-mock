## MOCK 3 
 ## COMPUTE THE % OF ACCOUNTS THAT WERE CLOSED ON JANUARY 10 
 ````sql
 SELECT 
 	ROUND(COUNT(CASE WHEN STATUS = 'closed' THEN 1 ELSE NULL END)*1.00/
	COUNT(*),2) * 100 AS RATE_CLOSED 
 FROM interviews.account_status
 WHERE DATE = '2020-01-10';
````
 ## Answer: 
 | rate_closed |
|-------------|
| 25.00       |




 
