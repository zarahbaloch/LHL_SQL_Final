What issues will you address by cleaning the data?

Firstly, Alteration of Unit Cost per 1,000,000

    Products Table
Checked and ensured stock levels were all 0 and above (none).

Checked and ensured sentiment scores were between -1 and 1 (all nulls were set to 0).

Checked and ensured sentiment magnitudes were less than 0 (all nulls were set to 0).

Checked and ensured ordered quantities were 0 or above (none).

Checked and ensured restocking lead times were 0 or above and within a reasonable range (50-day threshold, none).

Checked and ensured all products had a name (no null values).

Checked and ensured all SKUs were unique (no duplicates, as this was the primary identifier).

    Analytics Table
visitnumber: all above 0 and no null values.

visitID: removed null values (none), duplicates deleted (as it is the primary key).

visitstarttime: no negative values, no null values, and cannot start in the future (duplicates are allowed).

dates: removed null values (none), ensured all dates were in the correct format (all set).

fullvisitorID: removed null values (none).

bounces: ensured bounces were not negative, set nulls to 0.

revenue: no negative values, nulls set to 0.

unit_price: removed negative values and nulls (neither were present).

units_sold: removed negative values (set to 0) and nulls (set to 0).

pageviews: removed negative values (none) and nulls (set to 0).

timeonesite: removed negative values (none) and nulls (set to 0).

userid: removed null values and replaced them with "Unknown."

channelgrouping: removed null values (none were present).

socialengagementtype: removed null values (none were present).

    Sales by SKU
Total ordered: removed negative values, removed null values (none).

    Sales Reports
Ratios: removed negative values and nulls, set nulls to the average value (0.10191703104332729711).

Total ordered: removed negative values and null values (none).

Sentiment scores: ensured values were within 0 and 1, removed null values (none).

    All Sessions
sessionqualitydim: set null values to 0.

productrefundamount: set null values to 0.

product quantity: set null values to 0.

itemquantity: set null values to 0.

productrevenue: set null values to 0.

transactionrevenue: set null values to 0.

totaltransactionrevenue: set null values to 0.

item revenue: set null values to 0.


Queries:
Below, provide the SQL queries you used to clean your data.

Example SQL Queries (units_sold)- ensuring it is not NULL or Negative + Setting NULL values to 0 

    SELECT * FROM analytics WHERE units_sold < 0 OR units_sold IS NULL;

    UPDATE analytics SET units_sold = 0 WHERE units_sold IS NULL;
*this was completed for all columns, in all tables with applicable data types (listed above)

Example SQL Queries (visitid)- check for duplicates  + attatch each visitid (duplicate or not) to a unique key to ensure no data necessary data is being deleted. 

    #Check for duplicates
    SELECT visitid, COUNT(*) 
    FROM analytics
    GROUP BY visitid
    HAVING COUNT(*) > 1;

    #Add a new column ensuring a unique key
    ALTER TABLE analytics ADD COLUMN analytics_id SERIAL PRIMARY KEY;

    #Assign new column (analytics_id) as the primary kery 
    ALTER TABLE analytics ADD CONSTRAINT pk_analytics PRIMARY KEY (analytics_id);


    









