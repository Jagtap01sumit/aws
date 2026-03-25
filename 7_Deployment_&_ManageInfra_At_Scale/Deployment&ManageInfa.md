## Deploying workloads on AWS

- First techonology is CloudFormation
### CloudFormation
- CloudFormation is a declarative way of outlining your AWS Infrasturcture,
 for any resources (most of them are supported).
- For example, within a CloudFormation template, you say:
    - I want a security group
    - I want two Ec2 instances using this security group
    - I want an S3 bucket
    - I want a load balancer(ELB) in front of these machines
- Then CloudFOrmation creates those for you, in the right order, with the exact configuration that you specify
### Benefits of AWS CloudFormation(1/2)
##### Infrastructure as code
  - No resources are manually created, which is execellent for control
  - Changes to the infrastructure are reviewed through code
- Cost
    - Each resources within the stack is tagged with an identifier so you can easily see how much a stack costs you
    - You can estimate the costs of you resources using the CloudFormation template
    - Savings stragtegy: In Dev, you could automation deletion of templates at 5PM and recreated at 8 AM, safly
### Benefits of AWS CloudFormation (2/2)
- Productivity
    - Ability to destroy and re-create an infrastructure on the cloud on the fly
    - Automated generation of Diagram for your templates!
    - Declarative programming(no need to figure out ordering and orchestration)
- Don't re-invent the wheel
    - Leverage existing templates on the web!
    - Leverage the documentation
- Supports (almost) all AWS resources:
    - Everything we'll see in this course is supported
    - you can use "custom resources" for resouces that are not supported
 ## CloudFormation + Infrastructure Composer
 - Example: Wordpress CloudFormation Stack
 - We can see all the resouces
 - We can see the relations between the components

## AWS Cloud Development Kit (CDK)
- Define your cloud infrastructure using a familiar language:
	- JavaScript/TypeScript, Python, Java, and .NET
- The code is "compiled" into a CloudFormation template (JSON/YAML)
- You can therefore deploy infrastructure and application runtime code together
	- Great for Lambda functions
	- Great for Docker containers in ECS/EKS
<img width="1098" height="305" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_26623490" src="https://github.com/user-attachments/assets/df2d5bc0-0169-416a-824a-bd599fbacd6b" />
<img width="938" height="550" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_26623490 (1)" src="https://github.com/user-attachments/assets/94ab3879-d7f3-483d-ae4d-aef01b574c4c" />


# Beanstalk
## Typical architecture: Web App 3-tire

<img width="1055" height="570" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056068 (1)" src="https://github.com/user-attachments/assets/c12dabac-43e8-4629-8858-4b69f45d4a0e" />

### Developer problems on AWS
- Managing infrastructure
- Deploying Code
- Configuring all the databases, load balancers, etc
- Scaling concerns
- Most web apps have the same architecture (ALB + ASG)
- All the developers want is for their code to run!
- Possibly, consistently across different applications and environments

#### so there comes a Elastic Beanstalk

### AWS Elastic Beanstalk Overview
- Elastic Beanstalk is a developer centric view of deploying an application on AWS
- It uses all the component's we've seen before:
EC2, ASG, ELB, RDS, etc...
- But it's all in one view that's easy to make sense of!
- We still have full control over the configuration
- Beanstalk = Platform as a Service (PAAS)

- Beanstalk is free but you pay for the underlying instances

### Elastic Beanstalk
- Managed service 
	- Instance configuration/OS is handled by Beanstalk
	- Deployment strategy is configurable but performed by Elastic Beanstalk
	- Capacity provisioning
	- Load balancing & auto-scaling
	- Application health-monitoring & responsiveness
- Just the application code is the responsibility of the developer

- Three architecture models:
	- Single instance deployment: good for dev
	- LB + ASG: great for production or preproduction web application
	- ASG only: great for non-web apps in production (workers, etc)

-Supports for many platforms
	- GO
	- Java SE
	- java with Tomcat
	- .NET on Windows Server with IIS
	- Node.js
	- PHP
	- Python
	- Ruby
	- Packer Builder
	- Single container Docker
	- Multi-Container Docker
	- Preconfigured Docker

### Elastic Beanstalk  Health Monitoring
- Health agent pushes metrics to CloudWatch
- Checks for app health, publishes health events

## AWS CodeDeploy
- We want to deploy our application automatically
- Works with EC2 Instances
- Works with On-Premises Servers
- Hybrid service
- Servers/Instances must be provisioned and configured ahead of time with the codeDeploy Agent

## AWS CodeCommit
 - Before pushing the application code to servers, it needs to be stored somewhere
- Developers usually store code in a repository, using the Gid technology
- A famous public offering is GitHub, AWS competing product is CodeCommit
- CodeCommit:
	- 
