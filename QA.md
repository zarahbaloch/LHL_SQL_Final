What are your risk areas? Identify and describe them.

1. Missing/ NULL Values: having null or missing values in specific fields (i.e productsku, visitid, etc.) can make joins difficult to complete as well as interfere with numeric operations (adding, counting, etc.), which can skew results needed in analysis.
  
2. Duplicate Keys: duplicate keys (that are supposed to be unique identifiers) can lead to poor joins and incorrect aggregations of information. This can lead to problems such as duplicated metrics, overcounting, etc.

3.  Invalid Ranges: having ranges outside of expected boundaries (i.e sentimenscores being outside of range, units_sold being negative, etc.) can signal further data issues, which can distort data & analysis.
    
4. Inconsistent Keys: when foreign keys in one table, do not exist in another table, they cannot function appropriately as the 'connector'. This means that joins will fail, or important data can be omitted. Further we can have incomplete datasets to draw conclusions from.
   
6. Formatting: improper formatting (i.e for dates, times, ID's) can make aggregations, filtering and groupings difficult. Further, it may lead to data being excluded further down the line when analaysis is being completed. 

QA Process:
Describe your QA process and include the SQL queries used to execute it.

1. Data Types Checks
2. Assertion-Based Validity Checks
3. Outlier Checks
4. Join Validation
