## find the top 3 unique salaries of each department
--revert the results alphabetically by department and by highest to lowest salary
````sql
WITH CTE AS (
	SELECT 
	 	SALARY,
		DEPARTMENT, 
		DENSE_RANK() OVER(PARTITION BY DEPARTMENT ORDER BY SALARY DESC) AS RANKED
	FROM interviews.twitter_employee
)
SELECT DISTINCT SALARY,DEPARTMENT, RANKED
FROM CTE
WHERE RANKED <=3
ORDER BY 2 ASC , 1 DESC;
````
