# Project overview

Tasks:

define schema
join master data and data sources
do queries

# INLJ algorithm

# Schema for DW

# OLAP queries with outputs

Q1 Determine the top 5 products in Dec 2019 in terms of total sales

PRODUCT_NAME TOTAL_SALES RANK 
------------ ----------- ----

Q2 Determine which store produced highest sales in the whole year?

STORE_NAME TOTAL_SALES RANK 
---------- ---------------- ----

Q3 Determine the top 3 products for a month (say, Dec 2019), and 
for the 2 months before that, in terms of total sales.

PRODUCT_NAME SUM(TOTAL_SALES) RANK 
------------- ---------------- ----

Q4 Create a materialised view called “STOREANALYSIS” that presents 
the product-wise sales analysis for each store. The results should be ordered 
by StoreID and then ProductID.

STOREID PRODUCTID SUM(STORE_TOTAL) 
-------- ---------- ----------------

Q5 Think about what information can be retrieved from the materialised view
created in Q4 using ROLLUP or CUBE concepts and provide some useful information
of your choice for management.

# Summary of what was learnt