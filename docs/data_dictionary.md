# Data Dictionary

## Source Files

| Dataset        | Description           | PrimaryKey                   |
| -------------- | --------------------- | ---------------------------- |
| orders         | order details         | order_id                     |
| customers      | customer details      | customer_id                  |
| products       | products details      | product_id                   |
| sellers        | sellers details       | seller_id                    |
| order_items    | order item details    | order_id, order_item_id      |
| order_payments | order payment details | order_id, payment_sequential |
| order_reviews  | order review details  | review_id                    |
| geolocation    | geolocation data      | No Primary Key               |

## Dataset Detailed Descriptions

### 1. olist_orders_dataset.csv

This contains details of each order placed

1. order_id : unique identifier of the order.
2. customer_id : Key to the customer dataset, each order has a unique customer_id.
3. order_status : Reference to the order status (delivered, shipped etc).
4. order_purchase_timestamp: shows the purchase timestamp.
5. order_approved_at : shows the payment approval timestamp.
6. order_delivered_carrier_date : Shows the order posting timestamp. When it was handled to the logistic partner
7. order_delivered_customer_date : Shows the actual order delivery date to the customer.
8. order_estimated_delivery_date : Shows the estimated delivery date that was informed to the customer at the purchase moment.
