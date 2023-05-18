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
