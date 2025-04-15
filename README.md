# aws

### What is Cloud Computing? 
##### Cloud computing is the on-demand delivery of compute power, database storage, application, and other IT resources

### The Deployement Models of the Cloud
| Private Cloud      | Public Cloud| Hybrid Cloud |

### The five Characteristics of Cloud Computing
##### On-demad self service
##### Broad network access
##### Multi-tenancy and resource pooling
##### Rapid elasticity and scalability
##### Measured service

## Types of Cloud Computing 
### Infrastructure as a service(IaaS)
###### - Provice building block for cloud IT
###### - Provides networking, computers, data storage space
###### - Highest level of flexiblity
###### - Easy Parallel with traditional on-premises IT

### Platform as a Service(PaaS)
###### - Removes the need for your organization to  manage the underlying infrastructure
###### - Focous on the deployment and management of your applications

### Software as a Service(SaaS)
###### Completed product that is run and managed by the service provider


![image](https://github.com/user-attachments/assets/d62b8e3b-63a5-4040-af11-da19a445fafa)


### History of AWS 
![image](https://github.com/user-attachments/assets/6738ac60-d7fb-481a-8f00-f9fc679dc318)



### AWS Global Services:
###### Identity and Access Management (IAM)
###### Route 53 (DNS Services)
###### CloudFront (Content Delivery Network)
###### WAF (Web Application FireWall)

### Most AWS Services are Region-scoped:
###### Amazon EC2 (Infrastructure as a Service)
###### Elastic Beanstlk (Platform as a Service)
###### Lambda (function as a Service)
###### Rekognition (Software as a Service)


### IAM:Users & Groups
##### Identity and Access Management, Global service
###### Root Account created by default, shouldn't be used or shared
###### IAM is a global service because we are create user and assign them to group
###### Users are people within your organization, and can be grouped
###### Groups only contains users, not other groups
###### Users don't have to belong to a group, and user can belong to multiple groups

##### IAM: Permissions
###### Users or Groups can be assiged JSON documents called policies
###### These policies define the permissions of the users
###### In AWS you apply the least privilege principle: dont give more permissions than a user needs


### IAM Policies Structure

![image](https://github.com/user-attachments/assets/a6006f57-9110-404a-bd2d-24b2f4b81311)

#### Consist of
1. Version : Policy language version, always include " 2012-10-17 "
2. Id : An Identifier for the policy (optinal)
3. Statement : One or more individual statement (required)

#### Statements consist of 
1. Sid : an identifier for the statment (optinal)
2. Effect : whether the statement allows or denies access (Allow , Deny)
3. Principle: account/user/role to which this policy applied to
4. Action : list of actions this policy allows or denies
5. Resouce : list of resources to which the actions applied to
6. Codition: condition for when this policy is in effect(optinal)


### IAM - Password Policy
1. Strong Password = higher security for your account
2. In AWS, you can setup a password policy.
   1. Set a minimum password lenght
   2. Require specific character types
       1. including uppercase letters
       2. lowercase letters
       3. numbers
       4. non-alphanumeric characters
  3. Allow all IAM users to change their own passwords
  4. Requie users to change their password after sometime (password expiration)
  5. Prevent password re-use

     #### Multi Factor Authentication - MFA
     ###### Users have access to your account and can possibly change configuration or delete resources in your AWS account
     ###### You want to protect your root accounts and IAM users
     ##### MFA = password you know + security device you own
     ##### Main benefit of MFA:
     ###### if a password is stolen or hacked the account is not compromised

## How can user access AWS ?
* To access AWS, you have three options:
   *  AWS Management Console(Protected by password + MFA)
   *  AWS Command Line Interface(CLI): protected by access keys
       * Install AWS CLI > https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions
   *  AWS Software Deveoper Kit(SDK) - for code: Protected by access keys
       * Language - specific APIs (set of libraries)
       * Enable you to access and manage AWS services programmatically
       * Embedded within your application
       * Supports
           * SDKs (JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++)


### How to create and use access key
###### IAM > Users > "username" > Create access key
###### IN CMD: 
      - aws configure
      - "Enter AWS Secret Access ID"
      - "Enter AWS Secret Access Key"
      - "Default region name" ex. ap-south-1 -> Mumbai
      - aws iam list-users
 
### IAM Section - Summary
###### Users: Mapped to a physical user, has a password for AWS Console
###### Groups: Contains users only
###### Policies: JSON Document that outlines pemissions for users or groups
###### Roles: for EC2  Instance or AWS Services
###### Security: MFA + Password Policy
###### AWS CLI: Manage you AWS services 
###### AWS SDK: Manage your AWS Services using a programming language
###### Access Keys: access AWS using the CLI or SDK
###### Audit: IAM Credential Reports & IAM Access Advisor


### AWS Budget Setup 
-> root user -> Account -> IAm user and role access to Billing information (if its deactivated , activate it) 
-> Budgets and planning -> Budgets -> create Budget -> Use a template (Simplified) -> Zero spend budget -> Budget name - My Zero-Spend Budget -> Email recipients <EmailId> -> create budget


*************************************************************************************************************************************************************************************************************************

### Amazon EC2

##### EC2 is one of the most popular of AWS offering
##### EC2 = Elastic Compute Cloud = Infrastructure as a Service
##### It mainly consists in the capability of :
   1. Reting virtiual machines( EC2)
   2. Storing data on virtual drives (EBS)
   3. Distributing load across machines (ELB)
   4. Scaling the services using an auto-scaling group (ASG)
##### Knowing EC2 is fundamental to understand how the Cloud works

#### EC2 sizing & configuration options
###### Operating System(OS): Linux, Window or Mac OS
###### How much compute power & cores (CPU) 
###### How much random-access memory (RAM)
###### How much storage space:
      1. Network-attached (EBS & EFS)
      2. hardware (EC2 Instance Store)
###### Network card: speed of the card, Public IP address
###### Firewall rules: security group
###### Bootstrap Script (configure at first launch): EC2 User Data

### EC2 User Data
###### It is possible to bootstrap our instance using an EC2 user data script.
###### bootstraping means launching commands when a machine starts
###### The script is ony run once at the instance first start
###### EC2 user data is used to automate boot tasks such as:
   1. Installing updates
   2. Installing software
   3. Downloading common files from the internet
   4. Anything you can think of
##### The EC2 User Data Script runs with the root user.

### EC2 instance types: example
![image](https://github.com/user-attachments/assets/2b6578a9-92ea-4215-ac2f-ec408cc30871)

> [!NOTE]
> ### t2.micro is part of the AWS free tier (Up to 750 hours per month)


#### Hands-On : Launching and EC2 Instance running Linux

##### Wee'll be launching our firest virtual server using the AWS Console
##### WE'll get a first hight-leel approach to various paramenters 
##### We'll see that our server is lauched using EC2 use data
##### We'll learn how to start / stop / terminate our instance

-> Ec2 console -> Launch instances -> Name and tags <My First Instance> -> Quick Start <Amazon Linux> -> Free tier eligible (default) -> Architecture <64 bit(x86)>(default) ->Instance type <t2.micro> (default) -> key pair(login) -> create new keypair -> checkbox HTTP traffic from the internet -> Advanced Details -> User data <Scripts which need to execute on first launch> -> Launch Instance

<Scripts which need to execute on first launch?
```
#!/bin/bash

# Use this for your user data (script from top to bottom)

# install httpd (Linux 2 version)

yum update -y

yum install -y httpd

systemctl start httpd

systemctl enable httpd

echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```

#### Instance Types
https://aws.amazon.com/ec2/instance-types/

* Instance Types
   * General Purpose - for web server or code repo - balanced between compute, memorey, networking 
   * Compute Optimized - for processing load - high performace web server - gaming server - ML and scentific models
   * Memory Optimized - for fast performace for workloads that process large data sets in memory - optimized for BI - process big unstructed data
   * Accelerated Computing
   * Storage Optimized - for High freq online transaction processing system (OLTP) - relation & NOSQL Databases - data warehouse application
   * HPC Optimized
   * Instance Features
   * Measuring Instance Performance
 
#### AWS has the following naming convention:  m5.2xlarge
- m: instance class
- 5: generation (AWS improves them over time
- 2xlarge: size within the instance class

#### Security Group
##### Security groups are the fundamental of network security in AWS
##### They control how traffic is allowed into or out of our EC2 Instance.
![image](https://github.com/user-attachments/assets/9e4fc1e1-35cc-44f3-a5e9-68ebf60be96f)
##### Security groups only contains rules
##### Security groups rules can reference by IP or by security groups

##### Security groups are acting as a "firewall" on EC2 rules
* They regulate:
     * Access to ports
     * Authorised IP ranges - IPv4 and IPv6
     * Control of inbound network (from other to the instance)
     * Control on outbound network ( from the instance to other)
![image](https://github.com/user-attachments/assets/fe3692fc-fe83-4cf9-9285-22dffb44edd4)

#### Classic ports to know 
* 22 = SSH(Secure Shell) - log into a Linux instance(allow to login EC2 instance on Linux)
* 21 = FTP (File Transfer Protocol) - upload files into a file shares
* 22 = SFTP (Secure File Transfer Protocol) -upload files using SSH
* 80 = HTTP - access unsecured websites
* 443 = HTTPS - access secured websties
* 3389 = RDP (Remote Desktop Protocol ) - log into a windows instance

#### SSH Summary Table   (allow to login EC2 instance on Linux)
![image](https://github.com/user-attachments/assets/8e35a517-ea21-465a-aaf6-f378e93f0734)


### How to SSH into your EC2 Instance

##### SSH is one of the most important function. It allows you to control a remote machine, all using the command line.
###### copy public IPv4 address from instance
###### confirm the Inbound rules in security group [ port 22, protocol TCP, source 0.0.0.0/0] if not then edit and add rules
###### You wanted to SSH into your EC2 instance using: open the folder where you saved your .pem file(key pair)
```
ssh -i .\firstInstance.pem ec2-user@13.51.70.152
```
###### amazon linux 2 AMI has one user already setup for use -> ec2-user, @ say that the user for that specific server
![image](https://github.com/user-attachments/assets/2e67c971-6b56-48c7-999b-89b90781bad1)
> [!CAUTION]
>  This means the .pem file had too many permissions, making it insecure. SSH won’t allow that.
> 
##### ✅ You did the right thing using icacls, which is Windows' way of managing file permissions.

```
## For windows
icacls .\firstInstance.pem /inheritance:r

icacls .\firstInstance.pem /remove "Users" "BUILTIN\Users" "Everyone"

icacls .\firstInstance.pem /grant:r "${env:USERNAME}:R"


## For Linux/Mac
chmod 0400 .\firstInstance.pem

```
| Command                            | What it Does                                                                 |
|------------------------------------|------------------------------------------------------------------------------|
| `/inheritance:r`                  | Removes inherited permissions (like from Desktop or parent folder)           |
| `/remove ...`                     | Removes read access from all users/groups except your user                   |
| `/grant:r "${env:USERNAME}:R"`    | Grants read-only permission to your current user       |
| `$env:USERNAME`                   | Displays the username of the currently logged-in user in PowerShell          |

##### ✅ Then You Tried SSH Again:
```
ssh -i .\firstInstance.pem ec2-user@<your-instance-public-ip>
```
##### ✅ Connected Sucessfully 🎉
###### you can try some commands 
``` whoami
```
![image](https://github.com/user-attachments/assets/e1ad3e77-1988-4c63-a2db-5a5779213947)
```
logout
```
##### ✅ Connection Closed🎉







      




