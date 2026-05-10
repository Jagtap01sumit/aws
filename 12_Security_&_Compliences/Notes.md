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
