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

### 2. olist_customers_dataset.csv

This dataset has information about the the customers

1. customer_id : Key to the orders dataset. Each order has a unique customer_id.
2. customer_unique_id : unique identifier of a customer
3. customer_zip_code_prefix : first five digits of customer zip code
4. customer_city : customer city name
5. customer_state : customer state

The system assigns unique customer_id for each order i.e same customer will get different customer_ids for different orders.
customer_unique_id is used to identify the customer uniquely and to identify the customers that made repurchases at store.

### 3. olist_products_dataset.csv

This dataset includes the data about the products sold by Olist.

1. product_id : unique product identifier
2. product_category_name : root category of product, in Portuguese
3. product_name_length : number of characters extracted from the product name
4. product_description_length : number of characters extracted from the product description
5. product_photos_qty : number of product published photos
6. product_weight_g : product weight measured in grams
7. product_length_cm : product length measured in centimeters.
8. product_height_cm : product height measured in centimeters.
9. product_width_cm : product width measured in centimeters.

### 4. olist_sellers_dataset.csv

This dataset includes data about the sellers that fullfilled orders made at Olist.

1. seller_id : seller unique identifier
2. seller_zip_code_prefix : first 5 digits of seller zip code
3. seller_city : seller city name
4. seller_state : seller state

### 5. olist_order_items_dataset.csv

This dataset includes data about the items purchased within each order.

1. order_id : order unique identifier
2. order_item_id : sequential number identifying number of items included in the same order.
3. product_id : product unique identifier.
4. seller_id : seller unique identifier
5. shipping_limit_date : Shows the seller shipping limit date for handling the order over to the logistic partner.
6. price : item price
7. freight_value : item frieight value (if an order has more than one item the freight value is splitted between the items)

### 6. olist_order_payments_dataset.csv

This dataset includes data about the orders payment options.

1. order_id : unique identifier of an order
2. payment_sequential : a customer may pay an order with more than one payment method. If he does so, a sequence will be created to accommodate all payments.
3. payment_type : method of payment chosen by the customer.
4. payment_installments : number of installments chosen by the customer.
5. payment_value : transaction value

### 7. olist_order_reviews_dataset.csv

This dataset includes data about the reviews made by the customers.

1. review_id : unique review identifier
2. order_id : unique order identifier
3. review_score : score ranging from 1 to 5 given by the customer on a satisfaction survey.
4. review_comment_title : Comment title from the review left by the customer, in Portuguese.
5. review_comment_message : Comment message from the review left by the customer, in Portuguese.
6. review_creation_date : shows the date in which the satisfaction survey was sent to the customer.
7. review_answer_timestamp : Shows satisfaction survey answer timestamp.

### 8. olist_geolocation_dataset.csv

This dataset has information about brazillian zip codes and its latitude and longitude coordinates

1. geolocation_zip_code_prefix : first 5 digits of the zip code
2. geolocation_lat : latitude
3. geolocation_long : longitude
4. geolocation_city : city name
5. geolocation_state : state

There is no primary key for this dataset

Also, there is an extra file product_category_name_translation.csv file for translation of the product names
