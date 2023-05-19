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
		u.id AS userID ,COUNT(*) AS amount_comments
	FROM interviews.users u
	JOIN interviews.comments c ON U.id = c.user_id
	WHERE created_at BETWEEN '2020-01-01' AND '2020-01-31' 
	AND  created_at > joined_at 
	GROUP BY 1
)
SELECT 
	COUNT(userID) AS amount_users,amount_comments
FROM BASE
GROUP BY 2
ORDER BY 2; 
````
Answer: 
| amount_users | amount_comments |
|--------------|-----------------|
| 2            | 1               |
| 1            | 2               |
| 2            | 3               |





