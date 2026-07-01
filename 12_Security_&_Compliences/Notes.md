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

### AWS Network Firewall

- Protect your entire Amazon VPC
- From Layer 3 to  7 protection
- Any direction, you can inspect
  - VPC to VPC traffic
    - Outbound to internet
    - Inbound from internet
    - To / from Direct Connect & Site-to-Site VPN
  
### AWS Firewall Manager
- Mange security rules in all accounts of an AWS Organization
- Security policy: common set of security rules
  - VPC security Groups for EC2, Application Load Balancer, etc...
    - WAF rules
    - AWS Shield Advanced
    - AWS Network Firewall
- Rules are applied to new resources as they are created (good for compliance) across all and future accounts in your organization

### Penetration Testing on AWS Cloud
- AWS customers are welcome to carry out security assessments or penetration tests against their AWS infrastructure without prior approval for 8 serices:
  - Amazon EC2 instances, NAT Gateways, and Elastic Load Balancers
    - Amazon RDS
    - Amazon CloudFront
    - Amazon Aurora
    - Amazon API Gateways
    - AWS Lambda and Lambda Edge functions
    - Amazon Lightsail resources
    - AMazon Elastic Beanstalk environments
- List can increase over time (you won't be tested on that at the exam)

- Prohibited Activities
    - DNS zone walking via Amazon Route 53 Hosted Zones
    - Denial of Services(DoS),Distributed Denial of service(DDoS), Simulated DoS, Simulated DDoS
    - Port flooding
    - Protocol flooding
    - Request flooding (login request flooding, API request flooding)
 
## Encryption with KMS & CloudISM
- Data at rest vs. Data in transit
   - At rest: data stored or archived on a device
     - On a hard disk, on a RDS instance, in S3 Glacier Deep Archive, etc.
- In transit (in motion): data being moved from one location to another
    - Transfer from on-premises to AWS, Ec2 to dynamoDB, etc
    - Means data transferred on the network
- We want to encryt data in both the states to protect it!
- For this we leverage encryption keys

### AWS KMS (Key Management Service)
- Anytime you hear "encryption" for an AWS service, it's most likely KMS
- KMS = AWS manages the encryption keys for us
- Encryption Opt-in:
    - EBS volumes: encrypt volumes
    - S3 buckets: server-side encryption of objects (SSE-S3 enabled by default, SSE-KME opt in)
    - Redshift database: encryption of data
    - RDS database: encryption of data
    - EFS drives: encryption of data

- Encryption Automatically enabled:
   - CloudTrain Logs
   - S3 Glacier
   - Storage Gateway
 
### CloudHSM
- KMS => AWS manage the software for encryption
- CloudHSM => AWS provisions encryption hardware
- Dedicated Hardware (HSM = Hardware Security Module)
- you manage you own encryption keys entiredly (not AWS)
- HSM device is tamper resistant, FIPS | 40-2 Level 3 compliance

- Types of KMS Keys
   - Customer Managed Key:
      - Create, manage and used by the customer, can enable or disable
      - Possibility of rotation policy (new ey generated every year, old key preserved)
      - Possibility to bring-your-own-key
    - AWS Managed key:
      - Created, managed and used on the customer's behalf by AWS
      - Used by AWS services (aws/s3, aws/ebs,aws/redshift)
    - AWS Owned Key:
      - Collection of CMKs that an AWS service owns and manages to use in multiple accounts
      - AWS can use those to protect resources in your account (but you can't view the keys)
    - CloudHSM Keys(custom keystore):
       - Key generated from your own CloudHSM hardware device
       - Cryptographic operations are performed within the CloudHSM cluster
     
## AWS Certificate Manager(ACM)
- Let's you easily provision, manage, and deploy SSL/TLS Certificates
- Used to provide in-flight encryption for websites(HTTPS)
- Supports both public and private TLS certificates
- Free of charge for public and private TLS certificates
- Free of charge for public TLS certificates
- Automatic TLS certificate renewal
- Integrations with (load TLS certificates on)
   - Elastic Load Balancers
   - CLoudFront Distributions
   - APIs on API gateway
 
## AWS Secrets Manager
- Newer service, meant for storing secrets
- Capability to force rotation of secrets egvery X days
- Automate generation of secretes on rotation (uses Lambda)
- Integration with Amazon RDS (MySQL, PostgresSQL, Autota)
- Secrets are encrypted using KMS
- Mostly meant for RDS Integration

## AWS Artifacte (not really a service)
- Portal that provides customers with on-demand access to AWS compliance documentation and AWS agreements
- Artifact Reports - Allows you to download AWS security and compliance documents from third-party autditors, like AWS ISO certifications, Payment Card Industry ( PCI), and System and Organization Control (SOC) reports
- Artifact Agreements - Allows you to review, accept, and track the status of AWS agreements such as the Business Associate Addendum (BAA) or the Health Insurance Portability and Accountability ACT (HIPAA) for an individual account or in your organization
- Can be used to support internal audit or compliance

## Amazon GuardDuty
- Intelligent Threat discovery to protect your AWS Account
- Uses Machine Learning algorithms, anomaly detection, 3rd party data
- One click to enable (30 days traial), no need to install software
- Input data includes:
  - CloudTrail Events Logs - unusal API calls , unauthorized deploments
      - CloudTrain Management Events - create VPC subnet, create trail,..
      - CloudTrail S3 Data events - get object, list objects, delete object,..
   - VPC Flow Logs - unusual internal traffic, unusal IP address
   - DNS Logs - compormised EC2 instances sending encoded data within DNS queries
   - Optional Features - EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events...
- Can setup EventBridge rules to be notified in case of findings
- EventBridge rules can target AWS Lambda or SNS
- Can protect against CryptoCurrency attacks (has a dedicated "finding:" for it)
<img width="1904" height="954" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056330" src="https://github.com/user-attachments/assets/4fe7f935-2251-4f9b-bd57-306637171368" />

## Amazon Inspector
- Automated sercurity Assessments
- For EC2 instances
  - Legveraging the AWS System Manager (SSM) agent
  - Analyze against unintended network accessibility
  - Analyze the running OS against known vulnerabilities
- For Container Images push to Amazon ECR
  - 
