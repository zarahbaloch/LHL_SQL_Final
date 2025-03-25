What are your risk areas? Identify and describe them.

1. Missing/ NULL Values: having null or missing values in specific fields (i.e productsku, visitid, etc.) can make joins difficult to complete as well as interfere with numeric operations (adding, counting, etc.), which can skew results needed in analysis.
  
2. Duplicate Keys: duplicate keys (that are supposed to be unique identifiers) can lead to poor joins and incorrect aggregations of information. This can lead to problems such as duplicated metrics, overcounting, etc.

3.  Invalid Ranges: having ranges outside of expected boundaries (i.e sentimenscores being outside of range, units_sold being negative, etc.) can signal further data issues, which can distort data & analysis.
    
4. Inconsistent Keys: when foreign keys in one table, do not exist in another table, they cannot function appropriately as the 'connector'. This means that joins will fail, or important data can be omitted. Further we can have incomplete datasets to draw conclusions from.
   
6. Formatting: improper formatting (i.e for dates, times, ID's) can make aggregations, filtering and groupings difficult. Further, it may lead to data being excluded further down the line when analaysis is being completed. 

QA Process:
Describe your QA process and include the SQL queries used to execute it.

1. Data Types Checks (Examples- Not all) 

        #Check all tables 
        SELECT table_name 
        FROM information_schema.tables 
        WHERE table_schema = 'public';

        #Check datatypes per table (repeat for every table)
        SELECT column_name, data_type
        FROM information_schema.columns 
        WHERE table_name = 'products';
  
2. Assertion-Based Validity Checks (Examples- Not all) 

        #Ensuring data within logical ranges 
        SELECT * FROM analytics WHERE revenue < 0;
     
        SELECT * FROM products WHERE sentimentscore < -1 OR sentimentscore > 1;


       #Checking FK Consistency
       SELECT sales_reports.productsku 
       FROM sales_reports 
       LEFT JOIN products ON sales_reports.productsku = products.productsku
       WHERE products.productsku IS NULL;


        #Checking for Uniqueness
        SELECT productsku, COUNT(*) 
        FROM products 
        GROUP BY productsku 
        HAVING COUNT(*) > 1;

   
4. Outlier Checks (Examples- Not all) 

        #Ensuring data within business metrics 
        SELECT * FROM all_sessions WHERE itemrevenue > 1000000;

  
6. Join Validation

        #Ensuring all relationships are intact 
        SELECT all_sessions.visitid, all_sessions.productsku, products.productname, analytics.revenue
        FROM all_sessions
        JOIN products ON all_sessions.productsku = products.productsku
        JOIN analytics ON all_sessions.visitid = analytics.visitid
        WHERE all_sessions.productsku IS NOT NULL 
          AND all_sessions.visitid IS NOT NULL;
