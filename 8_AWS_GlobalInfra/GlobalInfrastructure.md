### Why make a global application?
- A global application is an application deployed in mulitple geographies
- On AWS: this coulb be Regions and /or Edge Locations
- Degreased Latency
    - Latency is the time it takes for anetwork packet to reach a server
    - It takes time for a packet from Asia to reach the US
    - Deploy your applications closer to your users to decrease latency, better experience
- Diasster Recovery (DR)
    - If an AWS region goes down(earthquake, storms, power shutdown, politics)..
    - You can fail-over to another region and have your application still working
    - A DR plan is important to increase the availability of your application
 
- Attack protection: distributed global infrastruture is harder to attack
### Global Applications in AWS:
- Global DNS:Route 53
    - Great to route users to the closest deployment with least latency
    - Great for disaster recovery strategies
- Global Content Delivery Network (CDN):CLoudFront
    - Replicate part of your application to AWS edge Locations - decrease latency
    - Cache common requests-imporved user experience and decreased latency
- S3 Transfer Acceleration
    - Accelerate global upload & downloads into Amazon S3
- AWS Global Accelerator:
    - Improve global application availability and performace using the AWS global network
## 1. Amazono Route 53 Overview
 - Route 53 is a Managed DNS(Domain Name System)
 - DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
<img width="995" height="589" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112" src="https://github.com/user-attachments/assets/87b9d8c1-72df-45df-bcb9-c4b8701d59e0" />

### Route 53 Routing Policies
- Need to know them at a high-level for the Cloud practitioner exam
    1. Simple Routing Policy
    2. Weight Routing Policy
    3. Latency Routing Policy
    4. Failover Routing Policy
<img width="1089" height="564" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (2)" src="https://github.com/user-attachments/assets/18fcc309-2c78-40a8-b93c-245616aeb72b" />
<img width="1093" height="573" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (3)" src="https://github.com/user-attachments/assets/5b5b0d34-5889-4feb-8193-e9b7ad9065c2" />

### AWS CloudFront
- Content Delivery Network (CDN)
- Improves read performance, content is cached at the edge
- Improves users experience
- Hundreds of Points of Presenece globally (edge locations, caches)
- DDos protection (because worldwide), integration with shield, AWS Web Application Firewall
#### CloudFront Origins
- S3 bucket
    - For distributing files and caching them at the edge
    - For uploading files to S3 through CloudFront
    - Secured using Origin Access Control (OAC)
- VPC Origin
    - For applications hosted in VPC private subnets
    - Private Application Load Balancer/Network Load Balancer /EC2 Instances
- Custom Origin (HTTP)
    - S3 website (must first enable the bucket as a static S3 webstite)
    - Any public HTTP backed you want (example:public ALB)
#### CloudFront at a high level
<img width="1098" height="548" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056120" src="https://github.com/user-attachments/assets/e11f55f5-a408-4387-8e43-0bfa1671dd70" />
<img width="1101" height="568" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (1)" src="https://github.com/user-attachments/assets/e38ea359-099c-4ec1-8b8e-b5766c2be1c4" />
- data was cached in edged locations

### CloudFront Vs S3 Cross Region Relication
- CloudFront
    - Use Global Edge network
    - Files are cached for a TTL(maybe a day)
    - Great for static content that must be available everywhere
- S3 Cross Region Replication:
    - Must be setup for each region you want replication to happen
    - Files are updated in near real-time
    - Read only
    - Great for dynamic content that needs to be available at low-latency in few regions
      
### S3 Transfer Acceleration
- Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region
  <img width="919" height="244" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056132" src="https://github.com/user-attachments/assets/0cd11c6d-f1f9-4bc0-aa63-fe76f6980679" />
### AWS Global Accelerator
- Improve global application availability and performance using the AWS global network
- Leverage the AWS internal network to optimize the route to your application(60% improvement)
- 2 Anycast IP are created for your application and traffic is sent through Edge locations
- The Edge locations send the traffic to your application
<img width="1126" height="586" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056140" src="https://github.com/user-attachments/assets/afdb297b-618c-431e-a653-236dd79753d1" />

- This diagram shows what happens without a global accelerator , so you client to get to your application in your region can go through a lot of hops an lot of network and there could be latencies added to it. But if you use the Global Accelerator then you just connect to an Edge location to the region you're connecting to, it goes through the private AWS network, which is much faster.

### AWS Global Accelerator vs CloudFront
- They both use the AWS global network and its edge locations around the world
- Both services integrate with AWS shield for DDOS protection.
- CloudFront- CDN
       - Improve performace for your cacheable content (such as images and videos
       - content is served at the edge
- Global Accelerator
       - No caching, proxing packets at the edge to applications running in one or more AWS Regions.
       - imporves performace for a wide range of applications over TCp or UDP
       - Good for HTTP use cases that require static IP addresses
       - Good for HTTP use cases that required deterministic, fase regional failover

## AWS Outpost
- Hybrid Cloud:
	- Businesses that keep an on-premises infrastructure alongside a cloud infrastructure
	- Therefore, two ways of dealing with IT systems:
		- One for the AWS cloud(using the AWS console, CLI, and AWS APIs)
		- One for their on-premises infrastructure
- AWS Outposts are "server racks" that offers the same AWS infrastructure, services, APIs & tools to build your own application on-premises infrastructure and you can start leveraging AWS services on-premises

#### Benefits:
- Low-latency access to on-premises systems
- Local data processing
- Data residency
- Easier migration from on-premises to the cloud
- Fully managed service
- Some Services that work on Outposts:
	- Amazon EC2
	- Amazon EBS
	- Amazon S3
	- Amazon EKS
	- Amazon ECS
	- Amazon RDS
	- Amazon EMR

### AWS Wavelength:
- Wavelength zones are infrastructure deployments, embedded within the telecommunications providers datacenters at the edge of the 5G networks
- Brings AWS service to the edge of the 5G networks
- Example: EC2, EBS,VPC..
- Ultra-low latency applications through 5G network
- Traffic doesn't leave the Communication Service provider's (CSP) network
- High-bandwidth and secure connection to the parent AWS region
- No additional charges or service agreements
- Use cases: smart cities, ML-assisted diagnostics, connected vehicles, interactive live video streams, AR/VR,
Real-time Gaming..

###################145##########1.49

### AWS Local zones:
- Places AWS compute storage, database, and other selected AWS services closer to end users to run latency-sensitive applications
- Extend your VPC to more locations- "Extension of an AWS Region"
- Compatible with EC2, RDS, ECS, EBS, ElasticCache, Direct connect..
- Example:
	- AWS Region:N.Virginia(us-eash-1)
	- AWS Local Zones: Boston,Chiago, Dallas, Houston,Miami,
################################1.07################146 
### Global Applications Architecture
##################################147#####0.48
- Single Region, Single AZ
- Single Region, Multi AZ
- Multi Region, Active-Passive
- Multi Region, Active-Active
##################################147#####2.20

## Global Applications in AWS - Summary
- Global DNS: Route 53
	- Great to route users to the closest deployment with least latency
	- Great for disaster recovery strategies
- Global CDN: CloudFront
	- Replicate part of your application to AWS Edge locations - decreases the latency
	- Cache common requests -improved user experience and decreased latency
- S3 Transfer Acceleration
	- Accelerate global uploads & downloads into Amazon S3
- AWS Global Accelerator
	- Improve global application availability and performance using the AWS global network
- AWS Outposts:
	- Deploy outposts racks in you own data centers to extend AWS Services
- AWS Wavelength:
	- Brings AWS services to the edge of the 5G networks
	- Ultra-low latency applications
- AWS Local Zones:
	- Bring AWS resources (compute, database, storage,...) closer to your userss-TestAutomation-Parent-pipeline/1783/


---


### Section Introduction
- When we start deploying multiple applications, they will inevitably need to communicate with one another
- There are two patterns of application communication
	1. Synchronous communication(application to application)
		- Buying service <--> Shipping service
	2. Asynchronous/Event based (application to queue to application)
		- Buying service --> Queue --> Shipping service

- Synchronous between applications can be problematic if there are sudden spikes of traffic
- What if you need to suddenly encode 1000 videos but usually it's 10?
- In that case, it's better to decouple your applications:
	- using SQS: queue model
	- using SNS: pub/sub model
	- using Kinesis: real-time data streaming model
- These services can scale independently from our application!

## Amazon SQS - Simple Queue Service 
- What's a queue?
#############################################150###0.38
### Amazon SQA - Standard Queue
- Oldest AWS offering (over 10 years old)
- Fully managed service(serverless), use to decouple applications.
- Scales from 1 message per second to 10,000s per second
- Default retention of messages: 4 days, maximum of 14 days
- No limit to how many messages can be in the queue
- Messages are deleted after they're read by consumers
- Low latency(<10 ms on publish and receive)
- Consumers share the work to read messages & scale horizontally
#########################150######2.48

## Amazon SQS - FIFO Queue
- FIFO - First In First Out (ordering of messages in the queue)
#########################150######3.20

- Messages are processed in order by the consumer

## Amazon Kinesis Data Streams

- For the exam: real-time big data streaming
- Managed service to collect, process, and analyze real-time streaming data at any scale
- Too detailed for the Cloud Practitioner exam but good to know:
	- Amazon Kinesis Data Streams: low latency streaming to ingest data at scale from hundreds of thousands of sources
	- Amazon Data Firehouse: load Kinesis data streams into Amazon S3, RedShift, OpenSearch, etc..
### Amazon Kinesis (High-level overview)
##################################152#########1.10

## Amazon SNS
- What if you want to send one message to many receivers?
###################################153#######0.37
- The "event publishers" only sends message to one SNS topic
- As many "event subscribers" as we want to listen to the SNS topic notifications
- Each subscriber to the topic will get all the messages
- Up to 12,50,000 subscriptions per topic, 1,00,000 topics limit1.49
########################################153####

## Amazon MQ
- SQS, SNS are "cloud-native" services: proprietary protocols from AWS 
- Traditional applications running from on-premises may use open protocols such as:MQTT,AMQP,STOMP, Openwire, WSS
- When migrating to the cloud, instead of re-engineering the application to use SQS and SNS, we can use Amazon MQ
- Amazon MQ is a managed message broker service for RabbitMQ, ActiveMQ
- Amazon MQ doesn't "scale" as much as SQS/SNS
- Amazon MQ runs on servers, can run in Multi-AZ with failover
- Amazon MQ has both queue feature(SQS) and topic features(SNS)


- Integration Section - Summary
- SQS:
	- Queue service in AWS
	- Multiple Producers, messages are kept up to 14 days
	- Multiple Consumers share the read and delete messages when done
	- Used to decouple applications in AWS
- SNS:
	- Notification service in AWS
	- Subscribers: Email, Lambda, SQS, HTTP, Mobile...
	- Multiple Subscribers, send all messages to all of them
	- No message retention
- Kinesis: real-time data streaming, persistence and analysis
- Amazon MQ: managed message broken for ActiveMQ and RabbitMQ in the cloud(MQTT,AMQP.. protocols)

---
