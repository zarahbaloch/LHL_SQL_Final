Question 1: 

A sentiment score is a measure of emotional tone expressed in text. This falls within a range of -1 (very negative) to +1 (very positive). A sentiment magnitude is a measure of how much emotion is in a text (be it positive or negative). Understanding these values may allow for businesses to determine how their products are performing in the market. 

Which products have low sentiment scores (possible dissatisfaction)?

SQL Queries:

    SELECT 
    products.productsku,
    products.productname,
    products.orderedquantity,
    products.sentimentscore,
    products.sentimentmagnitude
    FROM products
    ORDER BY products.sentimentscore ASC

Answer: 
<img width="882" alt="Screenshot 2025-03-24 at 5 07 20 PM" src="https://github.com/user-attachments/assets/370bdfb7-9cf0-4f7a-9a1e-9d89261f604c" />
*Top 5 products with the lowest sentiment scores (potentially unsatisfied customers). 

Question 2: 

Understanding which types of social engangement drives brands & companies to achieve their highest purchases & revenues, allows for the optimization of marketing strategies to further increase earnings. 

What is the most effective engagement type for purchases? 

SQL Queries:

    SELECT 
    socialengagementtype,
    SUM(revenue) AS total_revenue,
    COUNT(DISTINCT visitid) AS number_of_sessions_with_this_engagement
    FROM analytics
    GROUP BY socialengagementtype;

Answer:

Overall, it seems the most revenue ($1 167 078 437 957) is collectively achieved through No Social Engangement ('Not Socially Enganged'). 

Question 3: 

As a business, it is important to recognize what time of day the most purchases occur. This can be for sales (optimizing sales strategies to target that time), for the technical support aspect (ensuring extra support in case the site goes down for increased activity) and for more! 

What times of day have the highest sales activity?

SQL Queries:

    Walkthrough of the code: 
    #Purpose of Line 1: Removing the exact hour from the timestamp 
    #'epoch' allows for the code to count hours from midnight onwards (00:00:00)
    #(INTERVAL '1 second') will convert the numeric value into a unit of time
    
    SELECT 
    EXTRACT(HOUR FROM TIMESTAMP 'epoch' + visitstarttime * INTERVAL '1 second') AS hour_of_day,
    SUM(revenue) AS total_revenue,
    COUNT(DISTINCT visitid) AS sessions_with_sales
    FROM analytics
    GROUP BY hour_of_day
    ORDER BY total_revenue DESC;

Answer:
<img width="535" alt="Screenshot 2025-03-24 at 5 38 41 PM" src="https://github.com/user-attachments/assets/af1e89ea-55aa-4dbb-a67a-57b77ca6eb44" />
*The hour which brings the highest revenue is 19 (7:00PM), followed by 17 (5:00PM), 20 (8:00PM), 18 (6:00PM) and 21 (9:00PM). This provides a general trend of the evening being the largest purchasing time.

Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
