# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
The goal of this project was to perform data cleaning, transformation, and quality assurance on a complex eCommerce dataset using SQL. The project also involved analyzing the dataset through SQL-based exploration.

## Process
### (Data Loading & Table Creation)
CSV data was imported through the pgAdmin UI. All necessary data and tables were created for the project. Data types were manually inputted (i.e  integers for quantities, numeric for revenues, text for identifiers). Primary and foreign keys were set to establish relational integrity. 

### (Data Cleaning & Standardization)
Null values, negative numbers and outliers were removed & replaced across all tables. Inconsistent & missing values were standardized. Key identifiers were double checked for accurate relations (i.e added analytics_id as a new unique key to handle duplicate visitid). 

### (Quality Assurance (QA) and Validation)
Asseration based checks were conducted to ensure data consistency (i.e foreign keys were appropriately set, no negative revenue, etc). All joins were validated across tables through multiple queries. All further outliers were detected (i.e unsually high item price, unusually high restocking time). Ensured all formatting was consistent across data (i.e dates, texts, numeric ranges, etc). 

### (Data Exploration and Analysis)
Assigned questions were answered appropriately whilst determining individual insights of the data sets (i.e explanation of sentiment score). Patterns and trends in the data were analyzed to determine further relevant information. 

## Results
Through data transformation and analysis the following was uncovered: 
- Products with the lowest sentiment scores (suggesting customer dissatisfactionn) were identified
- The United States was the top revenue generating country with Kickball as its top-selling product, whilst custom decals were most popular elsewhere
- Certain cities such as Council Bluffs or Bellflower showed higher product quantities per visitor
- Majority of revenues were tied to non-social engagement- which may suggest organic traffic drives the most revenue
- Evening hours had the highest sales activity, indicating an optimal window for marketing and promotions

## Challenges 
One predominant challenge was the number of nulls, missing values and zeroes across almost all tables. This made the data difficult to work with, and required extensive cleaning before any exploration could begin. 

Dealing with duplicate keys (like visitid) required independent decision making on how to deal with the data- either keeping the data & creating another identifer (which runs the risk of doubling/ inflating data) or deleting the day & keeping the original identifer (which runs the risk of losing important data and skewing results). Overall I resolved this by creating a surrogate key (analytics_id) and keeping the initial data.

Finally, the overall QA process was quite tedious and time consuming, which required multiple, layered queries for accuracy and correctness. 

## Future Goals
If I had more time, I would use a visualization tool to explain the insights (i.e creating a dashboard using Tableau or Power BI). Further, if I was part of this team, I would integrate other operational sources (i.e marketing, sales, etc) to correlate with the data and hopefully increase overall revenue. 
