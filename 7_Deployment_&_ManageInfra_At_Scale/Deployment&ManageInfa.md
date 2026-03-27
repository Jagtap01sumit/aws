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
	- Source-control service that hosts Git-based repositories
	- Make it easy to collaborate with others on code
	- The code changes are automatically versioned
Benefits:
	- Fully managed
	- Scalable & highly available
	- Private, Secured, Integrated with AWS
  ## AWS CodeBuild
	- Code building service in the cloud(name is obvious)
	- Compiles source code, run tests, and produces packages that are ready to be deployed (by CodeDeploy for example)
	- Benefits:	
		- Fully managed, serverless
		- Continuously scalable & highly available
		- Secure
		- Pay-as-you-go pricing - only pay for the build time
	
  ## AWS CodePipeling
	- Orchestrate the different steps to have the code automatically pushed to production
		- Code => Build => Test=> Provision => Deploy
		- Basic for CICD (Continue Integration & Continue Deliver)
	- Benifits:
		- Fully managed, compatible with codecommit, codebuild, codedeploy, elastic  beanstalk, cloudformation, GitHub, 3rd-party services (GitHub..) & custom plugins
############################131#######1.07

## AWS CodeArtifact
- Software packages depends on each other to be built ( also called code dependencies), and new ones are created
- Storing and retrieving these dependencies is called artifact management
- Traditionally you need to setup your own artifact management system
- CodeArtifact is a secure, scalable, and cost-effective artifact management for software development
- Works with common dependency management tools such as Maven, Gradle, npm, yarn, twine, pip, and NuGet
- Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact


## AWS System Manager (SSM)
- Helps you manage your EC2 and On-Premises systems at scale 
- Another Hybrid AWS service
- Get operational insight about the state of your infrastructure
- Suite of 10+ products
- Most important features are :
	- Patching automation for enhanced compliance
	- Run commands across an entire fleet of servers
	- Store parameter configuration with the SSM Parameter Store
- Works for Linux, Windows, MacOS, and Raspberry Pi OS (Raspbian)

### How Systems Manager works
- We need to install the SSM agent onto the systems we control
- Installed by default on Amazon Linux AMI & some ubuntu AMI
- If an instance can't be controlled with SSM, it's probably an issue with the SSM agents!
- Thanks to the SSM agent, we can run commands, patch & configure our servers

### Systems Manager - SSM Session Manager
- Allows you to start a secure shell on your EC2 and on-premises servers
- No SSH access, bastion hosts, or SSH keys needed
- No port 22 needed (Better security)
- Support Linux, macOS, and Windows
- send session log data to S3 or CloudWatch Logs
##############################134#############0.52

### System Manager Parameter Store
- Secure storage for configuration and secrets 
- API Keys, passowrds, configurations...
- Serverless, scalable, durable, easy SDK
- Control access permissions using IAM
- Version tracking & encryption (optional)
###################135#####0.49
***

### ✅ Ways to Access an EC2 Instance in AWS

| # | Method                    | Port 22 Required | SSH Key Required | IAM Role Required | OS Requirement                | Key Points                                                                     |
| - | ------------------------- | ---------------- | ---------------- | ----------------- | ----------------------------- | ------------------------------------------------------------------------------ |
| 1 | **SSH (Traditional)**     | ✅ Yes            | ✅ Yes            | ❌ No              | Any supported OS              | Uses SSH keys and terminal access. Port 22 must be open in the security group. |
| 2 | **EC2 Instance Connect**  | ✅ Yes            | ❌ No             | ❌ No              | Amazon Linux                  | AWS temporarily uploads SSH keys. Still requires port 22 to be open.           |
| 3 | **Session Manager (SSM)** | ❌ No             | ❌ No             | ✅ Yes             | Amazon Linux 2 / supported OS | Most secure option. Uses IAM role and SSM agent. No inbound ports required.    |

***

## 🔐 Security Comparison

| Method               | Network Ports    | Credential Management      | Works in Private Subnet | Security Level |
| -------------------- | ---------------- | -------------------------- | ----------------------- | -------------- |
| SSH                  | Port 22 open     | User‑managed SSH keys      | ❌ No                    | Medium         |
| EC2 Instance Connect | Port 22 open     | Temporary AWS‑managed keys | ❌ No                    | Medium         |
| Session Manager      | No inbound ports | IAM‑based access           | ✅ Yes                   | High ⭐         |

***

### One‑Line Summary

> AWS provides three ways to access EC2 instances: traditional SSH using port 22 and keys, EC2 Instance Connect using temporary SSH keys with port 22, and Session Manager which uses IAM and SSM without opening any ports and is the most secure approach.


## Deployement - Summary
- CloudFormation: (AWS only)
	- Infrastructure as Code, works with almost all of AWS resources
	- Repeat across Regions & Accounts
- Beanstalk (AWS only)
	- Platform as a Service(PaaS),limited to certain programming languages or Docker
	- Deploy code consistently with a known architecture, ALB+EC2+RDS
- CodeDeploy(hybrid): deploy & upgrade any application onto servers
- Systems Manager(hybrid):patch, configure and run commands at scales
### Developer Services - summery
- CodeCommit:Store code in private git repository (version controlled)
- CodeBuild: Build & test code in AWS
- CodeDeploy: Deploy code onto servers
- CodePipeline: Orchestration of pipeline(from code to build to deploy)
- CodeArtifact: Stroe software packages/dependencies on AWS
- AWS CDK: Define your cloud infrastructure using a programming language
 
