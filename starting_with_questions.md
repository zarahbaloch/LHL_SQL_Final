**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**
----------------------------------------------------------------------------------------------------

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
----------------------------------------------------------------------------------------------------

SQL Queries:

    SELECT
    all_sessions.country, 
    all_sessions.city, 
    COUNT(DISTINCT all_sessions.fullvisitorid) AS unique_visitors, 
    SUM(products.orderedquantity) AS total_products_ordered,
    SUM(products.orderedquantity) / (COUNT(all_sessions.fullvisitorid)) AS avg_products_per_visitor
    FROM all_sessions
    JOIN products ON all_sessions.productsku = products.productsku
    GROUP BY all_sessions.country, all_sessions.city
    ORDER BY avg_products_per_visitor DESC;

Answer:

For the top 10 countries sorted by average products per visitor: 

<img width="812" alt="Screenshot 2025-03-18 at 4 38 47 AM" src="https://github.com/user-attachments/assets/0fa706b0-24db-48d1-b294-6a601360ac77" />

Understanding purchasing behavior of site visitors from different regions globally can allow for businesses to optimize marketing, inventory, and customer engagement strategies. This query determines the average number of products ordered per visitor, calculated by dividing total products ordered by the number of unique visitors per location. The highest recorded averages were from Council Bluffs, US, with 2 visitors ordering 7,589 products per visitor, followed by Bellflower, US, with 2 visitors ordering 3,786 products per visitor. Additionally, Montenegro, Côte d'Ivoire, and Cork, Ireland each had 1 visitor ordering 3,786 products per visitor.

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**
----------------------------------------------------------------------------------------------------

SQL Queries:

    SELECT DISTINCT ON (all_sessions.country) 
    all_sessions.country, 
    all_sessions.v2productcategory, 
    SUM(products.orderedquantity) AS total_sold
    FROM all_sessions
    JOIN products ON all_sessions.productsku = products.productsku
    GROUP BY all_sessions.country, all_sessions.v2productcategory
    ORDER BY total_sold DESC;

Answer:

<img width="531" alt="Screenshot 2025-03-18 at 4 40 40 AM" src="https://github.com/user-attachments/assets/56966218-83e2-470a-8ca1-227658da3028" />

Across the top 10 countries analyzed (US, UK, India, Germany, Canada, Australia, France, Netherlands, and Italy), a clear pattern emerged in product category preferences. The most frequently ordered category in all these regions was "Home/Shop by Brand/YouTube," suggesting a strong influence of digital content and brand-driven shopping. This trend may indicate that consumers across these countries are engaging with online influencers or specific brand promotions whilst making purchasing decisions. 

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**
----------------------------------------------------------------------------------------------------

SQL Queries:

    SELECT country, v2productcategory, total_sold
    FROM (
    SELECT DISTINCT ON (all_sessions.country) 
        all_sessions.country, 
        all_sessions.v2productcategory, 
        SUM(products.orderedquantity) AS total_sold
    FROM all_sessions
    JOIN products ON all_sessions.productsku = products.productsku
    GROUP BY all_sessions.country, all_sessions.v2productcategory
    ORDER BY all_sessions.country, total_sold DESC
    ORDER BY total_sold DESC;


Answer:

<img width="681" alt="Screenshot 2025-03-18 at 4 42 49 AM" src="https://github.com/user-attachments/assets/c1458e08-2c3a-4e8c-b4a0-e66b3fef7673" />


The top-selling product by country reveals trends in purchasing behavior across different regions. The United States led with Kickball, selling 409,590 units, significantly outpacing other regions. Following this, custom decals emerged as the most popular product in multiple countries, including India, the UK, Germany, Canada, France, Japan, Romania, and Australia, with sales ranging from 83,292 units in India to 18,930 units in Australia. Meanwhile, Chile also showed a strong preference for Kickball, purchasing 15,170 units. This pattern suggests a regional preference for sports-related items in the US and Chile, whilst custom decals dominate in other international markets- perhaps indicating differences in consumer interests, cultural preferences, or local demand drivers.


**Question 5: Can we summarize the impact of revenue generated from each city/country?**
----------------------------------------------------------------------------------------------------
SQL Queries: 


Answer:

By using the information gained from Questions 1-4, we can summarize revenue impact across different cities and countries. The highest revenue-generating region is the United States, where Kickball sold 409,590 units, contributing significantly to sales volume. Other major revenue-driving countries include India, the UK, Germany, and Canada, where custom decals were the top-selling product. The dominance of the "Home/Shop by Brand/YouTube" category across multiple countries suggests that brand-driven and influencer-led marketing plays a key role in sales performance. These insights can guide businesses in optimizing inventory, pricing, and marketing strategies to maximize revenue potential globally.




