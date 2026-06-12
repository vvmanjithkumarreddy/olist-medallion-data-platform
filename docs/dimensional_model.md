# Dimensional Modelling Process

step1: list all the business process in the system

step2: list all source tables and mark them as event or entity
Event tables are potential fact tables
Entity tables are potential dimension tables

step3: Declare grain for each business process

step4: finalize the fact tables (decide which grains deserve their own fact table)

step5: identify dimensions
for each fact ask who, what, where, when, how

step6: consolidate and finalize dimension tables (combine dimensions discovered across all facts and finalize which becomes actual dimensions)

step7: identify measures for each event i.e what numeric values are recorded in
each event

step8: build stars i.e one star at a time
for each fact connet the related dimensions
do this for all the facts

step9: Identify confirmed dimensions (shared dimensions used by multiple facts)

step10: build the facts and dimensions

Above process is eloboration of Kimball's 4-step Design process

Kimballs 4-step dimensional modelling process:

1. select the business process
2. Declare the grain
3. Identify dimensions
4. Identify facts

---

# Dimensional Modelling for Olist Project (basic model)

## Step1 - list all the business processes in the system

what business processes exist in this system?

customers place orders \
customers make payments \
customers leave reviews \
sellers sell prodcuts

## Step2 - list all source tables and mark them as event or entity

Event tables: \
orders \
order_items \
order_payments \
order_reviews

Entity tables: \
customers \
sellers \
products \
geolocation

## Step3 - declare grain for each business process

Fact order - one row per order \
Fact order item - one row per order item \
Fact payment - one row per payment \
fact review - one row per review

## Step4 -finalize the fact tables

in the basic model we are just considering the fact_order and fact_order_item

## Step5 - identify dimensions

fact table: order

who placed the order: customer (dimension - customer) \
who recieved the order: seller (different items by different seller so no dimension) \
what did he order: multiple products (no single answer so no dimension) \
where - olist store (same for all so no dimension) \
when - order_purchase date (Date dimension) \
how - through olist (same for all so no dimension)

fact table: order_item

who bough the item - customer (customer dimension) \
who sold the item - seller (seller dimension) \
what - a product so (product dimension) \
where - through olist (same for all so no dimension) \
when - order_purchase date (Date dimension) \
how - through olist (same for all so no dimension)

## Step 6 - finalize dimension tables

dim_customers \
dim_sellers \
dim_products \
dim_date

## Step 7 - identify measures in each fact table

fact: order \
measures: \
order delivery days

fact: order_item \
measures: \
price \
freight_value

## Step 8 - build the star schema

fact_order \
dim_customer \
dim_date

fact_order_item \
dim_product \
dim_seller \
dim_customer \
dim_date
