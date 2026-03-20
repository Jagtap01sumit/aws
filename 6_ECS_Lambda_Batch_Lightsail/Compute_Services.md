## Docker

- Docker is a software development platform to deploy apps
- Apps are packaged in containers that can be run on any OS
- Apps run the same, regardless of where they're run
	- Any machine
	- No compatibility issues
	- Predictable behavior
	- Less work
	- Easier to maintain and deploy
	- Works with any language, any OS, any technology
- Scale containers up and down very quickly (seconds)

### Where Docker images are stored?
- Docker images are stored in Docker Repositories
- Public: Docker Hub https://hub.docker.com/
	- Find base images for many technologies or OS:
	- Ubuntu
	- MySQL
	- NodeJs, Java
- Private: Amazon ECR(Elastic Container Registry)


### Docker versus Virtual Machines
- Docker is "sort of" a virtualization technology, but not exactly
- Resources are shared with host -> many containers on one server
<img width="928" height="399" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056040 (1)" src="https://github.com/user-attachments/assets/c0028b27-ab31-448f-81c5-0730a7b0e6b1" />



## ECS
- ECS = Elastic Container Services
- Launch Docker containers on AWS
- You much provision & maintain the infrastructure (the EC2 instances)
- AWS takes care of starting/stopping containers
- Has integrations with the application Load Balancer

<img width="575" height="599" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056046" src="https://github.com/user-attachments/assets/7a39a2fe-145f-467d-b482-cf82141957f3" />


### Fargate
- Launch Docker containers on AWS
- You do not provision the infrastructure (no EC2 instance to manage) - simpler!
- Serverless offering
- AWS just runs containers for you based on the CPU/RAM you need
<img width="601" height="546" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056046 (1)" src="https://github.com/user-attachments/assets/fb002668-f145-4f3a-9fff-f9a105796fb2" />


### ECR
- Elastic Container Registry
- Private Docker Registry on AWS
- This is where you store your Docker images so they can be run by ECS or Fragate
<img width="634" height="476" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056046 (2)" src="https://github.com/user-attachments/assets/4420cfc4-90b8-4dcc-935c-90d807502a80" />


### Amazon EKS
- EKS = Elastic Kubernetes Service
- Allows you to launch managed Kubernetes clusters on AWS
- Kubernetes is an open-source system for management, deployment, and scaling of containerized apps(Docker)
- Containers can be hosted on:
	- EC2 instances
	- Fargate(serverless)
- Kubernetes is cloud-agnostic
(can be used in any cloud-Azure, GCP..)

---
## What's Serverless?
- Serverless is a new paradigm in which the developers don't have to mange servers anymore..
- They just deploy code
- They just deploy...functions!
- Initially.. Serverless== FAAS(Function as a Service)
- Serverless was pioneered by AWS Lambda but now also includes anything that's managed:"databases, messaging,storage,etc."

### Why AWS lambda
In Amazon EC2:
	- Virtual servers in the cloud 
	- Limited by RAM and CPU 
	- Continuously running
	- Scaling means intervention to add/remove servers

In Amazon Lambda:
	- Virtual functions - no servers to manage!
	- Limited by time - short executions
	- Run on-demand
	- Scaling is automated!


### Benefits of AWS Lambda
- Easy Pricing
	- Pay per request and compute time
	- Free tier of 10,000,000 AWS lambda requests and 4,00,000 GBs of compute time
	- Integrated with the whole AWS suite of services
	- Event-Driven: functions get invoked by AWS when needed
   	- Integrate with many programming languages
   	- Easy monitoring through AWS CloudWatch
   	- Easy to get more resources per functions(up to 10GB RAM!)
   	- Increasing RAM will also improve CPU and network!
 
  ### AWS Lambda language support
  	- Node.js(JavaScript)
  	- Python
  	- Java
  	- C# (.NET Core)/Powershell
  	- Ruby
  	- Custom Runtime API (Community supported, example Rust or Golang)
  	- Lambda Container Image
  	  	- The container image must implement the lambda runtime API
		- ECS/Fragate is preferred for running arbitrary Docker Images
 
  ### AWS Lambda Pricing: example
	- You can find overall pricing information here:
		https://aws.amazon.com/lamda/pricing
	- Pay per cells:
		- First 1 million requests are free
		- $0.20 per 1 million requests thereafter ($0.000002 per request)
	- Pay per duration:(in increment of 1ms)
		- 400000 GB-seconds of compute time per month if FREE
		- == 400000 seconds if functions is 1 GB RAM
		- == 3200000 seconds if function is 128 MB RAM
		- After that $1.00 for 600000 GB-seconds
	- Its is usually very cheap to run AWS Lambda so it's very popular

  ### Amazon API Gateway
	-  Example: building a serverless API
   	- Fully managed service for developers to easily create, publish maintain, monitor, and secure API's
   	- serverless and scalable
   	- Supports RESTful APIs and WebSocket APIs
   	- Support for security, user authentication, API throttling, API keys, monitoring..
  ---
  ## AWS Batch
  	- Fully managed batch processing at any scale
  	- Efficiently run 1,00,000s of computing batch jobs on AWS
  	- A "batch" job is a job with a start and an end (opposed to continuos)
  	- Batch will dynamically launch EC2 instances or Spot Instances
  	- AWS Batch provisions the right amount of compute /memory
  	- You submit or schedule batch jobs and AWS Batch does the rest!
  	- Batch jobs are defined as Docker images and run non ECS
  	- Helpful for cost optimizations and focusing less on the infrastructure
 
  ## AWS Batch - Simplified Example
  <img width="1165" height="510" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20515556" src="https://github.com/user-attachments/assets/d8a0d447-f739-44e8-a4a3-f04eec4032c8" />

  ### Batch vs Lambda
 	 - Lambda:
    	- Time limit
    	- Limited runtimes (15 min)
    	- Limitd temporary disk space
    	- Serverless
    - Batch:
      	- No time limt
      	- Any runtime as long as it's packaged as a Docker image
      	- Rely on EBS/Instance store for disk space
      	- Relies on EC2 (can be manged by AWS)
     
	---
  	## Amazon Lightsail (lightweight version of AWS)
  	- Virtual servers, storage, databases, and networking
  	- Low & predictable pricing
  	- Simpler alternative to using EC2, RDS,ELB,EBS,Route S3...
  	- Great for people with little cloud experience!
  	- Can setup notifications and monitoring of your Lightsail resources
  	- Use cases:
  	  	- Simple web applications (has templates for LAMP, Nginx, MEAN, Node.js...)
  	  	- Websites (templates for WordPress, Magento, Plesk, Joomla)
  	  	- Dev/Test environment
 	## Other Compute - Summary
  	- Docker: container technology to run  applications
  	- ECS:run Docker containers on EC2 instances
  	- Fargate:
  	  	- Run docker containers without provisioning the infrastructure
  	  	- Sererless offering (no EC2 instances)
  	- ECR: Private Docker Images Repository
  	- Batch: run batch jobs on AWS across managed EC2 instances
  	- Lightsail:Predictable & low pricing for simple application & DB stacks
 
  	 ## Lambda Summary
  	- Lambda is Serverless, Function as a service, seamless scaling, reactive
  	- Lambda Billing:
  	  	- By the time run x by the RAM provisioned
  	  	- By the number of invocations
  	- language Support: many programming languages except (arbitrary) Docker
  	- Invocation time: up to 15 minutes
  	- Use cases:
  	  	- Create Thumbnails for images uploaded onto S3
  	  	- Run a Serverless cron job
  	- API Gateway : expose Lambda functions as HTTP API
