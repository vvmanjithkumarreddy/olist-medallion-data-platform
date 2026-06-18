# Olist E-commerce Dashboard Design Document

## Step1 - Understand the business domin

1. what business generated this data
   Olist E-commerce marketplace

2. who are the stakeholders and what information they might be interested in

- Executive Team: total revenue, total orders, growth
- Operations Team: delivery performance, shipping delays
- Product Team: category performance
- Customer Team: customer behaviour

we can create a custom dashboard for each stakeholder

## Step2 - Identify the main business process

1. customers place orders
2. customers make payments (next iteration)
3. customers give reviews (next iteration)
4. sellers sell products

Potential KPIs (things that can be measured):
orders count, sales amount, delivery days, items sold

## Step3 - KPI Formula

For each fact table ask the questions and try to measure the value

1. what happened
2. how much
3. how long
4. how often

fact orders:

1. orders were placed, measures: count orders
2. how much revenue is generated, measures: total revenue
3. how long it took to deliver the orders, measures: average delivery time
4. how often does customer made purchases, measures: customer frequency

fact order_items:

1. order items were delivered to customers, measures: count items sold
2. how much seller earned, measures: seller revenue
3. no measures
4. no measures

Potential KPIs: orders count, total revenue, average delivery time, cusotmer frequency, items sold count, seller revenue

## Step4 - KPI matrix

| Area       | KPI                      |
| ---------- | ------------------------ |
| sales      | total orders             |
| sales      | total revenue            |
| sales      | average order value      |
| operations | average delivery days    |
| operations | late delivery percentage |
| products   | total items sold         |
| Products   | category revenue         |
| customers  | customer count           |
| customers  | customer frequency       |

## Step5 - Turn KPIs into visualizations
