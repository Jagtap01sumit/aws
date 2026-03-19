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


##########################112################3.06

## ECS
- ECS = Elastic Container Services
- Launch Docker containers on AWS
- You much provision & maintain the infrastructure (the EC2 instances)
- AWS takes care of starting/stopping containers
- Has integrations with the application Load Balancer

##############################113############0.59

### Fargate
- Launch Docker containers on AWS
- You do not provision the infrastructure (no EC2 instance to manage) - simpler!
- Serverless offering
- AWS just runs containers for you based on the CPU/RAM you need

##############################113############2.00##

### ECR
- Elastic Container Registry
- Private Docker Registry on AWS
- This is where you store your Docker images so they can be run by ECS or Fragate

##############################113############2.48##

### Amazon EKS
- EKS = Elastic Kubernetes Service
- Allows you to launch managed Kubernetes clusters on AWS
- Kubernetes is an open-source system for management, deployment, and scaling of containerized apps(Docker)
- Containers can be hosted on:
	- EC2 instances
	- Fargate(serverless)
- Kubernetes is cloud-agnostic
(can be used in any cloud-Azure, GCP..)


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
	- Event-Driven: functions get invoked by AWS when nee``````````````````````



