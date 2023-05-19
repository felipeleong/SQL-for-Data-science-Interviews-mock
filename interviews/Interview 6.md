## MOCK 6
/*
the company want to take a look at the level of participation across ther platform
your task is to write a query to calculate the distribution of comments by the count of users that joined the platform between 2018 and 2020
for the month of january 2020. the output should contain a count of comments and the corresponding number of users that made that number 
of comments
for example, youll be counting how many users made 1 comment, 2 comment, 3 comment etc jan 2020
use this tables: users and comments*/
````SQL
WITH BASE AS (
	SELECT 
		u.id AS userID ,COUNT(*) AS QUANTITY_OF_COMMENTS
	FROM interviews.users u
	JOIN interviews.comments c ON U.id = c.user_id
	WHERE EXTRACT(MONTH FROM C.CREATED_AT) = 01 AND EXTRACT(YEAR FROM U.JOINED_AT) >= 2018
	GROUP BY 1
), 
CONSOLIDATION AS (
	SELECT 
		QUANTITY_OF_COMMENTS,
		ROW_NUMBER() OVER(PARTITION BY QUANTITY_OF_COMMENTS ORDER BY QUANTITY_OF_COMMENTS) AS TOTAL
	FROM BASE
)
SELECT * FROM CONSOLIDATION
WHERE TOTAL >1;
````
Answer: 
| quantity_of_comments | total |
|---------------------|-------|
| 1                   | 2     |
| 2                   | 2     |
| 3                   | 2     |



