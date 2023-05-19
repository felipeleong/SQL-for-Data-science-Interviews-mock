## MOCK 9
Highest cost orders
find the customer with the highest total order cost between 2019-02-01 to 2019-05-01
Output thetr name, total cost of their items and the date
asume that every name is unique
use customers and orders tables
````SQL
WITH BASE AS (
	SELECT 
		C.FIRST_NAME,
		SUM(O.ORDER_COST*O.ORDER_QUANTITY) AS ORDER_COST,
		O.ORDER_DATE
	FROM interviews.customers AS C
	INNER JOIN interviews.orders AS O ON O.CUST_ID = C.ID
	WHERE O.ORDER_DATE BETWEEN '2019-02-01' AND '2019-05-01'
	GROUP BY 1,3
)
SELECT * FROM BASE --ORDER BY ORDER_COST DESC LIMIT 1
WHERE ORDER_COST = (SELECT MAX(ORDER_COST) FROM BASE);
````
## Answer:
| first_name | order_cost | order_date  |
|------------|------------|-------------|
| Karen      | 900        | 2019-04-01  |
| Pauline    | 900        | 2019-04-12  |
