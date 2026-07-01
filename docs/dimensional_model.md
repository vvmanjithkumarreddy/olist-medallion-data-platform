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
sellers sell products

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

fact_orders
fact_order_items
fact_payments
fact_reviews

## Step5 - identify dimensions

fact table: orders

who placed the order: customer (dimension - customer) \
who recieved the order: seller (different items by different seller so no dimension) \
what did he order: multiple products (no single answer so no dimension) \
where - olist store (same for all so no dimension) \
when - order_purchase date (Date dimension) \
how - through olist (same for all so no dimension)

fact table: order_items

who bough the item - customer (customer dimension) \
who sold the item - seller (seller dimension) \
what - a product so (product dimension) \
where - through olist (same for all so no dimension) \
when - order_purchase date (Date dimension) \
how - through olist (same for all so no dimension)

fact: payments
who made the payment - customer (customer dimension) \
who recieved the payment - seller (different item payment recieved by different seller so no dimension) \
what did he pay for - multiple products (no single answer so no dimension) \
where - olist store (same for all so no dimension)
when - order_purchase_date (Date dimension)
how - through payment type (Degenerate Dimension)

fact: reviews
who answered the reviews - customer (customer dimension) \
who recieved the reviews - olist (same for all so no dimension)
what did he review - multiple products (no single answer so no dimension) \
where - online (same for all so no dimension)
when - review_creation_date and review_answer_date (Date dimension)
how - through online (same for all so no dimension)

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

fact: order_payment
measures: \
payment_value

fact: order_reviews
measures: \
review_score

## Step 8 - build the star schema

fact_order \
dim_customer \
dim_date

fact_order_item \
dim_product \
dim_seller \
dim_customer \
dim_date

fact_payment \
dim_customer \
dim_date

fact_review \
dim_customer \
dim_date

## Step 9 - identify the conformed dimensions

dim_date and dim_customer

## Step 10 - build the facts and dimensions

built them in project gold layer
