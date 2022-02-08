# 1. Project requirements overview
1) Extract the real-time data from the business database
2) Clean and transform the data
3) Store the data into Analytics database
4) Visualize the result
Optional 5) Collect the real-time log data

# 2. Data Overview
There are 10 tables in total that are stored in the local MySQL database, including 
1) Order_infor: 

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Order index   |
| total_amount  | Order amount  |   
| order_status  | Order status  |  
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
| sku_id   | product id||
| sku_name  | product name|
| order_price | product price|
| sku_num| number of purchase|
|create_time| the time when the order is created|

3) sku_info:

| header        | meaning       |
| ------------- |:-------------:| 
| id            | order index    |
| order_id      | Order id  |   
| user_id | user id  |  
| sku_id   | product id||
| sku_name  | product name|
| order_price | product price|
| sku_num| number of purchase|
|create_time| the time when the order is created|



Project Architecture
# 3. Data overview
# 4. 

