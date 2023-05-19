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
## Answer: 
| salary  | department    | ranked |
|---------|---------------|--------|
|         | entertainment | 1      |
| 300000  | hr            | 1      |
| 60000   | hr            | 2      |
| 40000   | hr            | 3      |
| 1200000 | product       | 1      |
| 100000  | product       | 2      |
| 40000   | product       | 3      |
| 400000  | tech          | 1      |
| 110000  | tech          | 2      |
| 80000   | tech          | 3      |
