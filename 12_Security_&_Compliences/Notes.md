### AWS Shared Responsibility Model
- AWS responsibility - Securitiy of the Cloud
    - Protecting infrastructure (hardware, software, facilities, and networking) that runs all the AWS services
    - Managed services like S3, DynamoDB, RDS, etc.
- Customer responsibility - Security in the Cloud
    - For EC2 instance, customer is responsible for management of the guest OS (including security patches and updates), fireall & network configuration, IAM
    - Encrypting application data
- Shared controls:
    - Patch Management, configuration Management, Awareness & Training
 
#### Example, for RDS
- AWS responsibility:
    - Manage the underlying EC2 isntance, disable SSH access
    - Automated DB patching
    - Automated OS pathching
    - Audit the underlying instance and disks & guarantee it functions
- Your responsibility:
    - Check the ports/IP/security group inbound rules in DB's SG
    - In-database user creation and permissions
    - Creating a database with or without public access
    - Ensure parameter groups or DB is configured to only allow SSL connections
    - Database encryption setting
#### Example, for S3
- AWS responsibility:
    - Guarantee you get unlimited storage
    - Guarantee you get encryption
    - Ensure separation of the data between diffenent customers
    - Ensure AWS employees can't access your data
- Your responsibility:
    - Bucket configuration
    - Bucket policy/public setting
    - IAM user and roles
    - Enabling encrytion
 
<img width="669" height="381" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056304_start=30" src="https://github.com/user-attachments/assets/ed829e15-7e54-4ce2-91c1-cec189a5e588" />


### DDOS Protection on AWS
- AWS shield standard: protects against DDOS attack for your website and applications, for all customers at no additional costs
- AWS Shield Advanced: 24/7 premium DDoS protection
- AWS WAF: FIlter specific requests based on rules
- CloudFront and Route 53:
      - Availability protection using global edge network
      - Combined with AWS shield, provides attack mitigation at the edge
- Be ready to scale - leverage AWS Auto Scaling
- <img width="2506" height="1379" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056310" src="https://github.com/user-attachments/assets/ac8bb0cb-51e4-46d6-94b2-2ca2c07ebf18" />

### AWS Shield
- AWS Shield Standard:
    - Free service that is activated for every AWS customer
    - Provides protection from attacks such as SYN/UDP Floods, Reflection attacks and other layer 3/layer 4 attacks
- AWS Shield Advanced:
    - Optional DDOS mitigation service ($3000 per month per organization)
    - Protect against more sophisticated attack on Amazon EC2, Elastic Load Balancing (ELB), Amazon CloundFront, AWS Global Accelerator, and Route 53
    - 24/7 access to AWS DDoS response team (DRP)
    - Protect against higher fees during usage spikes due to DDoS
### AWS WAF - Web Application Firewall
- Protects your web application from common web exploits (Layer 7)
- Layer 7 is HTTP (vs Layer 4 is TCP)
- Deploye on Application Load Balancer, API Gateway, GloudFront
- Define Web ACL (Web access control List):
      - Rules can include IP addresses, HTTP headers, HTTP body, or URI strings
      - Protects from common attack - SQL injection and Cross-Site Scripting(XSS)
      - Size constraints, geo-match (block countries)
      - Rate-based rules(to count occurrences of events) - for DD0S protection

#### AWS Network Firewall
- Protect your entire Amazon VPC
- From layer 3 to layer 7 protection
- ANy direction, you can inspect
      - VPC to VPC Traffic
      - Outbound to internet
      - Inbound from internet
  
