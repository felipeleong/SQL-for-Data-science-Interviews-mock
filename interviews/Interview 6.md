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
		ID, COUNT(*) AS QUANTITY_OF_COMMENTS
	FROM interviews.users AS U 
	INNER JOIN interviews.comments AS C ON U.ID = C.USER_ID
	WHERE EXTRACT(MONTH FROM C.CREATED_AT) = 01 
	AND EXTRACT(YEAR FROM U.JOINED_AT) >= 2018
	GROUP BY 1
)
SELECT
	 ID, QUANTITY_OF_COMMENTS,
	ROW_NUMBER() OVER(PARTITION BY QUANTITY_OF_COMMENTS ORDER BY QUANTITY_OF_COMMENTS) AS NUM_OF_USERS
FROM BASE;
````
Answer: 
| id  | quantity_of_comments | num_of_users |
|-----|---------------------|--------------|
| 4   | 1                   | 1            |
| 5   | 1                   | 2            |
| 7   | 2                   | 1            |
| 11  | 2                   | 2            |
| 1   | 3                   | 1            |
| 12  | 3                   | 2            |



