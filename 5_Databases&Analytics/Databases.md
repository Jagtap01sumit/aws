## Database And Analytics

- Storing data on disk (EFS,EBS, EC2 instance Store, S3) can have its limits
- Sometimes, you want to store data in a database..
- You can structure the data
- You build indexes to efficiently query/search through the data
- You define relationship between your datasets

- Databases are optimized for a purpose and come with different features, shapes and constraints

### Relational Databases
- Looks just like Excel spreadsheets, with links between them!
- Can use the SQL Language to perform queries / lookups

### No SQL Databases
- Non relational databases
- NoSQL databass are purpose build for specific data models and have flexibile schemas for building modern applications
- Benefits:
	- Flexibility: easy to evolve data model
	- Scalability: designed to scale-out by using distribuited clusters
	- High-performance: optimized for a specific data model
	- Highly functional: types optimized for the data model
-Examples: Key-value, documents, graph, in-memory, search databases.

NoSQL data example: JSON
- JSON = JavaScript Object Notation
- JSON is a common form of data that fits into a NoSQL model
- Data can be nested
- Fields can change over time
- Support for new types: array, etc..

Databases & Shared Responsibility on AWS
- AWS offers use to manage different databases
- Benefits include:
	- Quick Provisioning, High Availability, Vertical & Horizontal Scaling
	- Automated Backup & Restore, Operations, Upgrades
	- Operating System Patching is handled by AWS
	- Monitoring, alerting
- Note: Many databases technologies could be run on EC2, but you must handle yourself the resiliency, backup, patching, high availability, fault tolerance, scaling

# Amazon RDS Overview
- RDS stands for Relational Database Service
- It's managed DB service for DB use SQL as a query language.
- Its allow you to create databases in the cloud that are managed by AWS
	- Postgres
	- MySQL
	- Oracle
	- Microsoft SQL Server
	- IBM DB2
	- Aurora (AWS Proprietary database)

### Advantage over using RDS versus deploying DB on EC2
- RDS is a managed service:
	- Automated provisioning, OS patch
	- Continuous backups and restore to specific timestamp (Point in Time Restore)!
	- Monitoring dashboards
	- Read replicas for improved read performance
	- Multi AZ setup for DR(Disaster Recovery)
	- Maintain ace window for upgrades
	- Scaling capability (vertical & Horizontal)
	- Storage backed by EBS
- BUT you can't SSH into your instances

## RDS Solution Architecture

<img width="848" height="497" alt="image" src="https://github.com/user-attachments/assets/841013a0-8c93-4e9a-9425-a29fae3abbef" />


## Amazon Aurora
- Aurora is a proprietary technology from AWS (not open sourced)
- PostgreSQL and MySQL are both supported as Aurora DB
- Aurora is "AWS cloud optimized" and claim 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
- Aurora storage automatically grows in increments on 10GB, up to 256 TB
- Aurora costs more than RDS(20% more) - but is more efficient

## Amazon Aurora Serverless
- Automated database instantiation and auto-scaling based on actual usage
- PostgreSQL and MySQL are both supported as Aurora Serverless DB
- No capacity planning needed
- Least management overhead
- Pay per second, can be more cost-effective
- Use cases: good for infrequent, intermittent or unpredictable workloads...

<img width="476" height="428" alt="image" src="https://github.com/user-attachments/assets/69dbe183-1ae7-493d-9439-1fd2c8553d6b" />



## RDS Deployments: Read REplicas, Multi-AZ

- Read Replica:
	- Scale the read workload of your DB
	- Can create up to 15 Read Replicas
	- Data is only written to the main DB
<img width="416" height="258" alt="image" src="https://github.com/user-attachments/assets/449159c1-0d6a-4e9d-ad85-faf10c324c1b" />


- Multi-AZ
	- Failover in case of AZ outage (high availability)
	- Data is only read/written to the main database
	- Can only have 1 other AZ as failover

<img width="411" height="275" alt="image" src="https://github.com/user-attachments/assets/93944d3c-5459-4231-b7ab-0e1cb1c99e44" />


## RDS Deployents: Multi-Region
- Multi-Region (Read Replicas)
	- Disaster recovery in case of region issue
	- Local performance of global reads
	- Replication cose
<img width="922" height="482" alt="image" src="https://github.com/user-attachments/assets/87e30cde-73a0-46f1-915d-d459ef26dd67" />


## Amazon ElastiCache Overview
- The same way RDS is to get managed Relational Databases..
- ElasticCache is to get managed Redis or Memcached
- Caches are in-memory databases with high performance, low latency
- helps reduce load off databases for read intensive workloads
- AWS takes care of OS maintenance/Patching, optimizations, setup,configuration,monitoring,failure recovery and backups

### ElastiCache
- Solution Architecture - Cache
<img width="892" height="430" alt="image" src="https://github.com/user-attachments/assets/7e04fbb5-4057-46a4-82ef-4adddfd1ddb9" />


## DynamoDB

- Fully Managed Highly available with replication across 3 AZ(available zone)
- NoSQL database - not a relational database
- Scales to massive workloads, distributed "serverless" database
- Millions of requests per seconds, trillions of row, 100s of TB of storage



## DynamoDB

- Fully Managed Highly available with replication across 3 AZ(available zone)
- NoSQL database - not a relational database
- Scales to massive workloads, distributed "serverless" database
- Millions of requests per seconds, trillions of row, 100s of TB of storage
- Fast and consistent in performance
- Single-digit millisecond latency -low latency retrieval
- Integratd with IAM for security, authorization and administration
- Low cost and auto scaling capabilities
- Standard & Infrequent Access (IA) Table Class

### Dynamo DB -Type of data
- DynamoDB is a key/value database
- Its so flexible - in first row we enter 4 fields but in second row only insert 2 then also its accepts

<img width="920" height="517" alt="image" src="https://github.com/user-attachments/assets/c37fb4fb-d1fb-43f8-bb6f-52cd11e69c32" />


### DynamoDB Accelerator - DAX
- Fully Managed in-memory cache for DynamoDB
- 10x performance improvement - sigle - digit millisecond latency to microseconds latency - when accessing you DynamoDB tables
- secure, highly scalable & highly available
- Difference with ElastiCache at the CCP level: DAX is only used for and is integrated with DynamoDB, while ElastiCache can be used for other databases
<img width="417" height="443" alt="image" src="https://github.com/user-attachments/assets/8f8b5dcc-394d-40c6-9ba5-c0b6bbcb6c68" />


### DynamoDB - Global Tables
- Make a DynamoDB table accessible with low latency in multiple-regions
- Active-Active replication(read/write to any region of AWS)
<img width="834" height="310" alt="image" src="https://github.com/user-attachments/assets/d84e889b-61d0-4bfa-9502-533a4b937637" />




## RedShift Overview

-Redshift is based on PostgreSQL, but it's not used for OLTP(online transaction processing)
-It's OLAP - online analytical processing(analytics and data warehousing)
-Load data once every hour, not every second
- 10x better performance than other data warehouses, scale to PBs of data
-Columnar storage of data (instead of row based)\
-Massively Parallel Query Execution(MPP), highly available
- Pay as you go based on the instances provisioned
- Has a SQL interface for performing the queries
- BI tools such as AWS Quicksight or Tableau integrate with it

### Redshift Serverless
- Automatically provisions and scales data warehourse underlying capcity
- Run analytics workloads without managing data warehouse infrastructure
- Pay only for what you use (save costs)

<img width="926" height="214" alt="image" src="https://github.com/user-attachments/assets/69d0fbde-1547-43f4-a18f-3281ac591e0e" />


## Amazon EMR
- EMR stands for "Elastic MapReduce"
- EMR helps creating Hadoop clusters(Big Data) to analyze and process vast amount of data
- The clusters can be made of hunderds of EC2 instances
- Also supports Apache Spark, HBase, Presto, Flink..
- EMR takes care of all the provisioning and configuration
- Auto-scaling and integrated with Spot instances
- Use cases: data processing, machine learning, web indexing, big data..

## Amazon Athena
- Serverless query service to perform analytics against S3 objects
- Uses standard SQL language to query the files
- Supports CSV, JSON,ORC,Avro,and Parquet(built on Presto)

- Pricing:$5 per TB of data scanned
- Use compressed or columnar data for cost-savings(less scan)
- Use cases: Business intelligence/analytics/reporting,analyze & query VPC flow logs, ELB logs, CloudTrail trails,etc..

<img width="241" height="525" alt="image" src="https://github.com/user-attachments/assets/3d0b85e3-f966-4c37-b4d2-c25218ade043" />


## Amazon QuickSight
- Serverless machine learning-powered business intelligence service to create interactive dashboards
- Fast, automatically scalable, embeddable, with per-session pricing
- Use cases:
	- Business analytics
	- Building visualizations
	- Perform ad-hoc analysis
	- Get business insights using data
- Integrated with RDS, Aurora,Athena,Redshift,S3...

## DocumentDB
- Aurora is an "AWS-implementation" of PostgresSQL/MySQL..
-DocumentDB is the same for MongoDB (which is a NoSQL database)

- MongoDB is used to store, query, and index JSON data
- Similar "deployment concepts" as aurora
- Fully Managed, highly available with replication across 3 AZ
- DocumentDB storage automatically grows in increments of 10GB

- Automatically scales to workloads with millions of request per seconds

## Amazon Neptune
- Fully managed graph database
- A popular graph dataset would be a social network
- Highly available across 3AZ, with up to 15 read replicas
- Build and run applications working with highly connected datasets- optimized for these complex and hard queries
- Can store up to billions of relations and query the graph with milliseconds latency
- Highly available with replications across multiple AZs
- Great for knowledge graphs (Wikipedia), fraud detection, recommendation engines, social networking

	
## Amazon Timestream
- Fully managed, fast, scalable, serverless time series database
- Automatically scales up/down to adjust capacity
- Store and analyze trillions of events per day
- 1000s times faster & 1/10th the cost of relational databases
- Build-in time series analytics functions (helps you identify patterns in your data in near real-time)

### Amazon Managed Blockchain
- Blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted, central authority
- Amazon Managed Blockchain is a managed service to:
	- join public blockchain networks
	- Or create your own scalable private network
- Compatible with the frameworks Hyperledger Fabric & Ethereum

### AWS Glue
- Managed extract, transform, and load(ETL) service
- Useful to prepare and transform data for analytics
- Fully serverless service
<img width="884" height="275" alt="image" src="https://github.com/user-attachments/assets/d2b2f6c0-b211-49ee-95fa-a7d51557fcf3" />


### DMS - Database Migration Services
- Quickly and securely migrate databases to AWS, resilient, self healing
- The source database remains available during the migration
- Supports:
	- Homogeneous migrations: ex Oracle to Oracle
	- Hetrogeneous migrations: ex Microsoft SQL Server to Aurora

---
| Service                                  | Type            | Category      | Use Case                         | Key Features                                                 |
| ---------------------------------------- | --------------- | ------------- | -------------------------------- | ------------------------------------------------------------ |
| **Amazon RDS**                           | Relational      | OLTP          | Traditional apps, transactions   | Managed SQL DB, backups, Multi-AZ, Read Replicas             |
| **Amazon Aurora**                        | Relational      | OLTP          | High-performance apps            | 5x faster than MySQL, auto-scaling storage, highly available |
| **Amazon Aurora Serverless**             | Relational      | OLTP          | Unpredictable workloads          | Auto-scaling, pay-per-use, no capacity planning              |
| **Amazon ElastiCache**                   | In-Memory       | Cache         | Speed up apps                    | Redis/Memcached, microsecond latency                         |
| **Amazon DynamoDB**                      | NoSQL           | Key-Value     | High-scale apps                  | Serverless, millisecond latency, auto scaling                |
| **DynamoDB Accelerator (DAX)**           | In-Memory       | Cache         | Faster DynamoDB reads            | Microsecond latency, 10x faster                              |
| **Amazon Redshift**                      | Relational      | OLAP          | Analytics & BI                   | Columnar storage, MPP, PB-scale                              |
| **Amazon Redshift Serverless**           | Relational      | OLAP          | Analytics without infra          | Auto-scaling, pay-per-use                                    |
| **Amazon EMR**                           | Big Data        | Processing    | Hadoop, Spark jobs               | Scalable clusters, supports big data frameworks              |
| **Amazon Athena**                        | Analytics       | Query         | Query S3 data                    | SQL-based, pay per TB scanned                                |
| **Amazon QuickSight**                    | BI              | Visualization | Dashboards                       | ML-powered insights, serverless                              |
| **Amazon DocumentDB**                    | NoSQL           | Document      | JSON data storage                | MongoDB compatible, scalable                                 |
| **Amazon Neptune**                       | NoSQL           | Graph         | Social networks, fraud detection | Graph queries, high connectivity                             |
| **Amazon Timestream**                    | NoSQL           | Time-Series   | IoT, metrics                     | Fast time-based analytics                                    |
| **AWS Glue**                             | Data Processing | ETL           | Data transformation              | Serverless ETL, data catalog                                 |
| **AWS Database Migration Service (DMS)** | Migration       | Migration     | Move DBs to AWS                  | Supports live migration                                      |
| **Amazon Managed Blockchain**            | Blockchain      | Distributed   | Decentralized apps               | Supports Hyperledger & Ethereum                              |


# Databases & Analytics Summary in AWS
- Relational Databases - OLTP: RDS & Aurora (SQL)
- Difference between Multi-AZ, Read Replicas, Multi-Region
- In-memory Database: Elastic Cache
- Key/Value Database: DynamoDB(serverless) & DAX (cache for DynamoDB)
- Warehouse -OLAP:Redshift(SQL)
- Hadoop Cluster:EMR
- Athena: query data on Amazon S3 (serverless & SQL)
- QuickSight: dashboards on you data (serverless)
- DocumentDB:"Aurora for MongoDB"(JSON-NoSQL database)
-Amazon managed blockchain: managed Hyperledger Fabric & Ethereum blockchains 
- Glue: Managed ETL(Extract Transform Load) and Data Catalog service
- Database Migration: DMS
- Neptune: graph database
- Timestream: time-series database

- Fast and consistent in performance
- Single-digit millisecond latency,low latency retrieval




