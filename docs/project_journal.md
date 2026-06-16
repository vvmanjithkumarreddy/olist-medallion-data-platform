# Project Journal

---

Task structure:

## Task :

### Objective :

### Activities :

### Decisions (optional) :

### Challenges (optional) :

### Outcome :

---

# Day 1 - Project Initiation

## Task 1 : Create Github Repository

### Objective :

Created the olist-medallion-data platform repository in my github account and create the project folder structure

### Activties :

created the folder structure with folders architecture, data, docs, notebooks, pipelines, sql, tests and .gitignore file

### Outcome :

Repository ready for development.

## Task 2 : Create Data Dictionary

### Objective:

Download the dataset and go through the data and create a data dictionary file for the project in detail.

### Activities:

Went though all the files in the dataset, understood them and found the primary keys for each data set as there is no reference data schema available.

created the data dictionary file with data source details, column details in each dataset

### Challenges:

finding primary keys for customers, order_items, payments
no primary key for geo location dataset

### Outcome:

Data Dictionary available for project reference with all the details

## Task 3: Creat Project Setup in Databricks

### Objective :

Create the basic project in databricks and load the data.

### Activities :

Created the catalog i.e olist_catalog and created the landing, bronze, silver and gold schemas for holding the landing data, bronze data, silver data and gold data.

loaded the data into the volumes in the landing layer.

### Outcome :

Basic Project setup is complete can start the project development in databricks.

## Day Summary

### Completed

1. Created Github Repository
2. Created Data Dictionary
3. Created Project Setup in Databricks

### Next Steps

finalize the gold layer schema

---

# Day 2 -

## Task 1: Finalize the gold layer star schema

### Objective :

Finalize the gold layer star schema for the project i.e what is the fact table and what are dimension tables and the columns inside the tables.

### Activities :

watched tutorials on dimensional modelling
refered the datawarehouse toolkit book
finalized the data dimensions for the gold layer

### Decisions :

created two versions for the dimensional model
model: basic

Facts:
fact_orders (grain: one row per order)
fact_order_items (grain: one row per order item)

Dimensions:
dim_customer
dim_product
dim_seller
dim_date

this is the simple version and in this version ignored the facts fact_reviews, fact_payments and dim_date

we can created calculated fields in BI tool if needed

model:advanced (final)

Facts:
fact_orders (grain: one row per order)
fact_order_items (grain: one row per order item)
fact_reviews (grain: one row per review)
fact_payments (grain: one row per payment record)

dim_customer
dim_product
dim_seller
dim_date

Also implement SCD (slowly changing dimensions)

### Challenges :

deciding on whether to keep two facts order, order_items or should merge into one fact

deciding on how many fact tables and dimension tables should be and how they connect to each other.

### Outcome :

Created the dimensional model for the gold layer and can proceed further with the project

## Day Summary

### Completed

completed the dimensional modelling for the project

### Next Steps

start the project development of creating bronze layer

---

# Day 3 -

## Task : Create bronze layer

### Objective :

Create bronze layer for the olist medallion data platform

### Activities :

Created the Ingestion notebook for each dataset

1. In each notebook Ingested the data from the landing layer
2. Defined and enforced schema
3. Added metadata columns filepath and ingestion timestamp columns to the dataset
4. written the data to the bronze delta table

### Outcome :

bronze layer is completed and can proceed futher with silver transformations

## Day Summary

### Completed

completed the building of bronze layer for the project

### Next Steps

start the building of silver layer for the project

---

# Day 4 -

## Task : Create Silver Layer for the project

### Objective :

Create silver layer for the olist medallion data platform

### Activities :

Created Transformaion notebook for each dataset

1. Filtered out invalid rows i.e rows with null primary key or duplicate key
2. Standardized string columns by converting to lower case/upper case and trimming the extra spaces
3. Filtered out rows having null values in important columns
4. written custom data validations like making sure review_score is between 1 and 5,
   timpestamp logic for delivered orders etc, review_id being 32 character length alphanumeric string etc
5. Did data enrichment using lookup tables like translating product category name from portuguese to english.
6. written the transformed data to silver tables.

### Outcome :

silver layer is completed and can proceed further with gold layer creation

## Day Summary

### Completed

completed the building of silver layer for the project

### Next Steps

start the building of gold layer for the project

---

# Day 5 -

## Task : Create gold layer for the project

### Objective :

Create gold layer for the olist medallion data platform
i.e create fact tables and dimension tables for the star schema

### Activities :

### Decisions (optional) :

### Challenges (optional) :

### Outcome :
