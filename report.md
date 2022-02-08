# 1. Project requirements overview
1) Extract the real-time data from the business database
2) Clean and transform the data
3) Store the data into Analytics database
4) Visualize the result
Optional 5) Collect the real-time log data

# 2. Data Overview
There are 10 tables in total that are stored in the local MySQL database and can be divided into two groups.
one mainly contains the fact tables:
1) Order_infor: 

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Order id      |
| total_amount  | Order amount  |   
| order_status  | Order status  |  
| user_id       | User id|
| payment_way   | Way of payment|
| out_trade_no  | Payment serial number|
| create_time | the time when the order is created|
| operate_time| the time when the order is operated|

2 )Order_detail:

| header        | meaning       |
| ------------- |:-------------:| 
| id            | order index    |
| order_id      | Order id  |   
| user_id | user id  |  
| sku_id   | product id|
| sku_name  | product name|
| order_price | product price|
| sku_num| number of purchase|
| create_time| the time when the order is created|


3) payment_info

| header        | meaning       |
| ------------- |:-------------:| 
| id            |payment id  |
| out_trade_id     | id for out trading   | 
| order_id|  order id |
| user_id | user id |
| alipay_trade_no|  Payment serial number of Alipay|
|total_amount | total amount|
|subject| content of the transaction| 
|payment_type| type of payment|
|payment_time| time of payment|



The other mainly includes the dimension tables:
1) base_category1

| header        | meaning       |
| ------------- |:-------------:| 
| id            | primary category id  |
| name     | primary category name  |   

2) base_category2

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Secondary category id  |
| name     | Secondary category name  |
| category1_id| primary category id |

3)base_category3

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Three-level category id  |
| name     | Three-level category name  | 
| category2_id|  Secondary category id |

4) sku_info:

| header        | meaning       |
| ------------- |:-------------:| 
| id            | product id    |
| price     | product price  |   
| sku_name | user id  |  
| sku_id   | product id|
| sku_name  | product name|
| sku_desc | product description|
| weight| product weight|
| tm_id| product brand id|
| category3_id|product three-level category|
| create_time|the time when the order is created|


5)user_infor:
| header        | meaning       |
| ------------- |:-------------:| 
| id            | user id    |
| name     | user name  |   
| birthday | user birthday  |  
| gender   | user gender|
| email  | user email|
| user_level | user level|
| create_time| the time when the order is created|
| operate_time| the time when the order is operated|

6) base_providence

| header        | meaning       |
| ------------- |:-------------:| 
| id            | providence id    |
| name     | providence name |   
| region_id | region_id  |
|area_code| code of the area|

7) base_region


| header        | meaning       |
| ------------- |:-------------:| 
| id            | region id   |
| name     | region name |   


# 3. Project Architecture
# 4. 

