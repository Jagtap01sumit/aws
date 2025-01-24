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
 



