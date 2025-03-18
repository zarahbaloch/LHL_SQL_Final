Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

SELECT country, city, SUM(totaltransactionrevenue) AS total_revenue
FROM all_sessions
GROUP BY country, city
ORDER BY total_revenue DESC

Answer:

i. United States (City not available in demo dataset) | Revenue Total: $6,092,560,000 USD
ii. San Francisco, United States | Revenue Total: $1,564,320,000 USD
iii. Sunnyvale, United States | Revenue Total: $992,230,000 USD
iv. Atlanta, United States | Revenue Total: $854,440,000 USD
v. Palo Alto, United States | Revenue Total: $608,000,000 USD

**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







