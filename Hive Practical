# Hive
HIVE Using Hive Query Language HQL


# Hive Practical-1

#### **To Login to HIVE and CLI stands for Command Line Interface**
[cloudera@quickstart ~]$ hive

Logging initialized using configuration in file:/etc/hive/conf.dist/hive-log4j.properties
WARNING: Hive CLI is deprecated and migration to Beeline is recommended.

#### To Clear the Screen use Ctrl + L
#### Each Command in Hive should be terminated by ;


#### **To Create Databases**

hive> create database trendytech;

#### To List Databases use show databases command

hive> show databases;
OK
default
trendytech
Time taken: 0.09 seconds, Fetched: 2 row(s)

#### Use Database name

hive> use trendytech;
OK
Time taken: 0.102 seconds
hive> 
#### Create Table in trendytech database
hive> create table customers
    > (
    > id bigint,
    > name string,
    > address string,
    > );
 OK
 Time taken: 1.302 seconds

#### To List the Tables

hive> show tables;
OK
customers
orders
Time taken: 0.088 seconds, Fetched: 2 row(s)

#### Describe Table Name

hive> describe customers;
OK
id                  	bigint              	                    
name                	string              	                    
address             	string              	                    
Time taken: 0.342 seconds, Fetched: 3 row(s)
hive> 


#### Describe formatted Table Name

hive> describe formatted customers;

# col_name            	data_type           	comment             
	 	 
id                  	bigint              	                    
name                	string              	                    
address             	string              	                    

#### Detailed Table Information	 	 
Database:           	trendytech          	 
Owner:              	cloudera            	 
CreateTime:         	Wed Sep 28 11:01:01 PDT 2022	 
LastAccessTime:     	UNKNOWN             	 
Protect Mode:       	None                	 
Retention:          	0                   	 
Location:           	hdfs://quickstart.cloudera:8020/user/hive/warehouse/trendytech.db/customers	 
Table Type:         	MANAGED_TABLE       	 
Table Parameters:	 	 
	COLUMN_STATS_ACCURATE	true                
	numFiles            	2                   
	numRows             	6                   
	rawDataSize         	73                  
	totalSize           	79                  
	transient_lastDdlTime	1664389501          
	 	 
#### Storage Information	 	 
SerDe Library:      	org.apache.hadoop.hive.serde2.lazy.LazySimpleSerDe	 
InputFormat:        	org.apache.hadoop.mapred.TextInputFormat	 
OutputFormat:       	org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat	 
Compressed:         	No                  	 
Num Buckets:        	-1                  	 
Bucket Columns:     	[]                  	 
Sort Columns:       	[]                  	 
Storage Desc Params:	 	 
	serialization.format	1                   
Time taken: 0.381 seconds, Fetched: 33 row(s)

#### **Insert Record into HIVE Table**
#### **Insert is not a right choice in HIVE**
#### **Whenever Insert Command is triggered MAP REDUCE JOB will be invoked and there will be only mappers since there is no aggregation**
#### **Hive is not a transactional system and in transactional system like RDBMS the inserts happens in a second**

hive> insert into customers values
    > (
    > 1111, "John", "WA"
    > );
    
#### Note: **Insert will trigger a MapReduce Job in background**

hive> insert into customers values
    > (2222, "Emily", "WA") , (3333, "Rick", "WA"), (4444, "Jane", "CA"), (5555,"Amit", "NJ"),
    > (6666, "Nina", "NY"
    > );
    
 #### **Number of Records inserted into table**
 
 hive> select * from customers;
OK
1111	John	WA
2222	Emily	WA
3333	Rick	WA
4444	Jane	CA
5555	Amit	NJ
6666	Nina	NY
Time taken: 1.245 seconds, Fetched: 6 row(s)

#### **Where exactly is the data stored by default**
#### **A Hive table has 2 things: 1. Data is stored in HDFS (default location is user/hive/warehouse) 2. Schema (metadata) is stored in a database**
#### **why metadata is kept in database? because the schema has to be udpated frequently and moreover quick access to this schema is required.**
#### **databases support updation and also support quick access thats why its an ideal choice to keep the meta data.**
#### data is kept in /user/hive/warehouse

/user/hive/warehouse
/user/hive/warehouse/trendytech.db
/user/hive/warehouse/bigdatabysumit.db

/user/hive/warehouse/trendytech.db/customers
/user/hive/warehouse/trendytech.db/orders

#### **To Check the Data is kept in **

[cloudera@quickstart ~]$ hadoop fs -ls /user/hive/warehouse
Found 1 items
drwxrwxrwx   - cloudera supergroup          0 2022-09-28 12:21 /user/hive/warehouse/trendytech.db

[cloudera@quickstart ~]$ hadoop fs -ls /user/hive/warehouse/trendytech.db
Found 2 items
drwxrwxrwx   - cloudera supergroup          0 2022-09-28 11:25 /user/hive/warehouse/trendytech.db/customers
drwxrwxrwx   - cloudera supergroup          0 2022-09-28 12:21 /user/hive/warehouse/trendytech.db/orders

[cloudera@quickstart ~]$ hadoop fs -ls /user/hive/warehouse/trendytech.db/customers
Found 2 items
-rwxrwxrwx   1 cloudera supergroup         13 2022-09-28 11:12 /user/hive/warehouse/trendytech.db/customers/000000_0
-rwxrwxrwx   1 cloudera supergroup         66 2022-09-28 11:24 /user/hive/warehouse/trendytech.db/customers/000000_0_copy_1

#### **We have made two inserts so two files are there and if we have inserts 10 times then 10 files would have been created**

[cloudera@quickstart ~]$ hadoop fs -cat /user/hive/warehouse/trendytech.db/customers/000000_0
1111JohnWA
[cloudera@quickstart ~]$ hadoop fs -cat /user/hive/warehouse/trendytech.db/customers/000000_0_c*
2222EmilyWA
3333RickWA
4444JaneCA
5555AmitNJ
6666NinaNY
[cloudera@quickstart ~]$ hadoop fs -cat /user/hive/warehouse/trendytech.db/customers/*
1111JohnWA
2222EmilyWA
3333RickWA
4444JaneCA
5555AmitNJ
6666NinaNY





