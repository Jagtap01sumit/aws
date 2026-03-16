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
- Fast and consistent in performance
- Single-digit millisecond latency,low latency retrieval




