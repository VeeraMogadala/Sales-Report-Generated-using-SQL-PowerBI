# Sales-Report-Generated-using-SQL-PowerBI
-- Show all Records

	SELECT * FROM customers;

-- Show count of Records

	SELECT COUNT(*) FROM customers ;
    
-- Show transactions for Chennai market (market code for chennai is Mark001)

	SELECT 
    *
    FROM
    sales.transactions
    WHERE
    market_code = 'Mark001';

-- Show distrinct product codes that were sold in chennai

    SELECT DISTINCT
    product_code
    FROM
    transactions
    WHERE
    market_code = 'Mark001';

-- Show transactions where currency is US dollars

	SELECT 
    *
    FROM
    transactions
    WHERE
    currency = 'USD';
    
-- Show transactions in 2020 join by date table

SELECT 
    t.*, d.*
FROM
    sales.transactions AS t
        INNER JOIN
    sales.date AS d ON t.order_date = d.date
WHERE
    d.year = '2020';

--  Show total revenue in year 2020

SELECT 
    SUM(t.sales_amount) AS Revenue_2020
FROM
    transactions AS t
        INNER JOIN
    date AS d ON t.order_date = d.date
WHERE
    d.year = '2020';
-- Show total revenue in year 2020, January Month 

SELECT 
    SUM(t.sales_amount)
FROM
    transactions t
        INNER JOIN
    date d ON t.order_date = d.date
WHERE
    d.year = 2020
        AND d.month_name = 'January'
        AND (t.currency = 'INR' OR t.currency = 'USD');
             
-- Show total revenue in year 2020,Chennai Market


SELECT 
    SUM(t.sales_amount) AS Revenue_2020
FROM
    sales.transactions AS t
        INNER JOIN
    sales.date AS d ON t.order_date = d.date
WHERE
    d.year = '2020'
        AND t.market_code = 'Mark001';

    


    

    


