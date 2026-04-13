
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


### Integration Section - Summary
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
