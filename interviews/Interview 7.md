## MOCK 7 
We would like to track the month over month % change revenue. Your output should be in the form of the year and month and the % change
round to 2 decimal ponts, and sort from the beginning of the year to the end of the year

````SQL
SELECT
	DATE_TRUNC('MONTH',CREATED_AT::DATE) AS MONTH,SUM(VALUE),
	ROUND((SUM(VALUE)-LAG(SUM(VALUE),1) OVER(ORDER BY DATE_TRUNC('MONTH',CREATED_AT)))/LAG(SUM(VALUE),1)OVER
		  (ORDER BY DATE_TRUNC('MONTH',CREATED_AT))*100,2)AS PERC_DIFF
FROM interviews.transactions
GROUP BY 1
ORDER BY 1;
````
Answer: 
| month                     | sum  | perc_diff |
|---------------------------|------|-----------|
| 2020-01-01 00:00:00-05    | 109  |           |
| 2020-02-01 00:00:00-05    | 611  | 400.00    |
| 2020-03-01 00:00:00-05    | 3453 | 400.00    |
| 2020-04-01 00:00:00-05    | 1565 | 0.00      |
| 2020-05-01 00:00:00-05    | 4564 | 100.00    |
