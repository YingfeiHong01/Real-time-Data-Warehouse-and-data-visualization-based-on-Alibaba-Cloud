# 1. Project requirements overview
- Extract the real-time data from the business database
- Clean and transform the data
- Store the data into Analytics database
- Visualize the result
Optional: Collect the real-time log data

# 2. Data Overview
There are 10 tables in total that are stored in the RDS and can be divided into two groups.  
one mainly contains the fact tables: 

(1) Order_infor: 

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Order id      |
| total_amount  | Order amount  |   
| order_status  | Order status  |  
| user_id       | User id|
| providence_id | Providence id|
| payment_way   | Way of payment|
| out_trade_no  | Payment serial number|
| create_time | Time when the order is created|
| operate_time| Time when the order is operated|  

(2) Order_detail:

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Order index    |
| order_id      | Order id  |   
| user_id | User id  |  
| sku_id   | Product id|
| sku_name  | Product name|
| order_price | Product price|
| sku_num| Number of purchase|
| create_time| Time when the order is created|


(3) payment_info

| header        | meaning       |
| ------------- |:-------------:| 
| id            |Payment id  |
| out_trade_id     | Payment serial number   | 
| order_id|  Order id |
| user_id | User id |
| alipay_trade_no|  Payment serial number of Alipay|
|total_amount | Total amount of payment|
|subject| Content of the transaction| 
|payment_type| Type of payment|
|payment_time| Time of payment|

The other mainly includes the dimension tables:

(1) base_category1

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Primary category id  |
| name     | Primary category name  |   

(2) base_category2

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Secondary category id  |
| name     | Secondary category name  |
| category1_id| Primary category id |

(3) base_category3

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Three-level category id  |
| name     | Three-level category name  | 
| category2_id|  Secondary category id |

(4) sku_info:

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Product id    |
| price     | Product price  |   
| sku_name | User id  |  
| sku_id   | Product id|
| sku_name  | Product name|
| sku_desc | Product description|
| weight| Product weight|
| tm_id| Product brand id|
| category3_id|Product three-level category|
| create_time|Time when the order is created|


(5) user_infor:

| header        | meaning       |
| ------------- |:-------------:| 
| id            |  User id    |
| name     | User name  |   
| birthday | User birthday  |  
| gender   | User gender|
| email  | User email|
| user_level | User level|
| create_time| Time when the order is created|
| operate_time| Time when the order is operated|

(6) base_providence

| header        | meaning       |
| ------------- |:-------------:| 
| id            | Providence id    |
| name     | Providence name |   
| region_id | Region_id  |
|area_code| Code of the area|

(7) base_region


| header        | meaning       |
| ------------- |:-------------:| 
| id            | Region id   |
| name     | Region name |   


# 3. Project Architecture
![Big data cloud 流程图](https://user-images.githubusercontent.com/89432543/153076731-b732bb28-7d26-4830-a123-66a5854cf45d.png)
- Relational Database Service(RDS) is a stable and elastic service that can be used to store our data. Here, I use two RDSs, one is to store the whole dataset and the other is to store the dimensional tables.
- Datahub plays a similar role as Kafka which provides the data queueing function for buffering. Datahub can also distributed the data because it can be connected to various services at AliCloud.
- Data Transmission Service(DTS) support the data transmission among SQL database, NoSQL database, OLAP and so on. It provides a secure and scalable data schema for asynchronous data transmission.
- Realtime Compute is a platform build on Apache Flink that provides realtime data processing flow.
- AnalyticDB is a realtime data warehouse that can procive multi-dimensional data analysis and data exploration
- DataV provides multiple visualization samples that can help customers quickly get familiar with the visualization tools and create professional visualization applications.

The data process and analysis are as follows:  
(1) paid_order_detail table
- Collect the information and details of the orders with completed payment from the order_info tables and order_detail at Datahub
- Store them in the paid_order_detail table in the Datahub  
(2) province_stat table
- Analyse the sales distribution in different provinces and regions from the paid_order_detail table at Datahub and the dimensional tables at RDS
- Store the result in the province_stat table in the AnalyticDB  
(3) sku_stat table
- Analyse the sales by category from the paid_oder_detail table at Datahub and the dimensional tables at RDS
- Store the result in the sku_stat table in the AnalyticDB

# 4. Result Screenshot
![analysis result](https://user-images.githubusercontent.com/89432543/153076858-50733d99-ec09-445b-bd26-afa22a3aff72.jpg)
