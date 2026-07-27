## Amazon WorkSpaces
- Managed Desktop as a Service (DaaS) solution to easily provision Windows or Linux desktops
- Great to eliminate management of on-premise VDI (Virtual Desktop Infrastructure)
- Fast and quickly scalable to thousands of users
- Secured data - integrates with KMS
- Pay-as-you-go service with monthly or hourly rates
---
## Amazon AppStream 2.0
- Desktop Application Streaming Service
- Deliver to any computer, without acquiring, provisioning infrastructure
- The application is delivered from within a web browser

### Amazon AppStream 2.0 vs WorkSpaces
- Workspaces
  - Fully managed VDI and desktop available
  - The users connect to the VDI and open native or WAM applications
  - Workspaces are on-demand or always on
 
- AppStream 2.0
  - Stream a desktop application to web browsers (no need to connect to a VDI)
  - Works with any device (that has a web browser)
  - Allow to configure an instance type per application type (CPU, RAM, GPU)
 
---

## AWS IoT Core
- IoT stands fro "Internet of Things" - the network of internet- connected devices that are able to collect and transer data
- AWS IoT Core allows you to easily connect IoT devices to the AWS Cloud
- Serverless, secure & Scalable to billions of devices and trillions of messages
- Your applications can communicate with your devices even when they aren't connected
- Integrates with a lot of AWS servicesf (Lambda, S3, sagaMaker, etc)
- Build IoT application that gather, process, analyze, and act on data

---

### AWS AppSync
- Store and sync data across mobile and web apps in real-time
- Makes use of GraphQL (mobile technology from Facebook)
- Client Code can be generated automatically
- Integrations with DynamoDB/Lambda
- Real-time subscriptions
- Offline data Synchronization (replaces Congnito Sync)
- Fine Grained Security
- AWS Amplify can leverage AWS AppSync in the background!
---
AWS Amplify 
- A set of tools and services that helps you develop and deploy scalable full stack web and mobile application
- Authentication, Storage, API(REST<GreaphQL), CI/CD, PubSub, Analytics, AI/ML Predictions, Monitoring , Source Code from AWS, Github,etc...

## AWS Infrastructure Composer
- Visually desing and build serverless applications quickly on AWS
- Deploy AWS infrastructure code wihtout needing to be an expert in AWS
- Configure how your resources interact with each other
- Generates Infrastructure as Code (IaC) using CloudFormation
- Ability to import existing CloudFormation / SAM templates to visualize them


## AWS Device Farm
- Fully0managed service that tests your web and mobile apps against desktop browsers, real mobile devices, and tablets
- Run tests concurrently on multiple devices9 speed up execution)
- Ability to configure device settings (GPS. language, Wi-fi, Bluetooth,...)

---

## AWS Backup
- Fully-managed service to centrally manage and automate backups  across AWS services
- On-demand and sheduled backups
- Support PITR(Point-in-time Recovery)
- Retention Periods, Lifecycle Management, Backup Policies,...
- Cross-Region Backup
- Cross-Account Backup (using AWS Organizations)

## Disater Recovery Strategies
- Backup & recovery ( cheapest ) (best)
- Pilot light ( only core functions of the app ready to scale but minimal setup)
- Warm Standby (full version of the app, but at minimum size)
- Multi-site /Hot-Site( full version of the app at full size)

## AWS Elastic Disaster Recovery (DRS)
- Used to be named "CloudEndure Disaster Recovery"
- Quickly and easily recover your physical, virtual, and cloud-based servers into AWS
- Example: protect your most critical databases (including Oracles, MySQL, and SQL Server), enterprice apps (SAP), protect your data from ransomware attacks,...
- Continue block-level replication for your servers

## AWS DataSync
- Move large amount of data from on-premises to AWS
- Can synchronize to: Amazon S3(any storage classes - including Glacier), Amazon EFS, Amazon FSx for Windows
- Replication tasks can be scheduled hourly, daily, weekly
- The replication tasks are incremental after the first full load

## Cloud Migration Strategies: The 7Rs
- Retire
  - Turn off things you don't need (maybe as a result of Re-architecting)
  - Helps with reducing the surface areas for attacks(more security)
  - Save cost, may up to 10% to 20%
  - Focus your attention on resources that must be maintained
- Retain
  - Do nothing for now (it's still a decision to make in a Cloud Migration)
  - Security, data compliance, performance, unresolved dependencies
  - No business value to migrate, mainframe or mid-range and non-x86 Unix apps
- Relocate
  - Move apps from on-premises to its Cloud version
  - Move EC2 instances to a different VPC, AWS account or AWS Region
  - Example: transfer servers from VMware Software-defined Data Center (SSDC)to VMware Cloud on AWS
- Rehost "lift and shift"
  - Simple migrations by re-hosting on AWS (applications, databases,data...)
  - Migrate machines (physical, virtual, another Cloud) to AWS Cloud
  - No cloud optimizations being done, applications is migrated as is
  - Cloud save as much as 30% on cost
  - Example: Migrate using AWS Application Migration Service
 
- Replateform "lift and reshape"
  - Example: migrate your database to RDS
  - Example: migrate your application to Elastic Beanstalk
  - Not changing to core architecture, but leverage some Cloud Optimizations
  - Save time and money by moving to a fully managed service or Serverless
 
- Repurchase "drop and shop"
  - Moving to a different product while moving to the cloud
  - Often you move to a SaaS Platform
  - Expensive in the short term, but quick to deploy
  - Example: CRM to Salesforce.com, HR to Workday, CMS to Drupal
- Refactor/ Re-architect
  - Reimaging how the application is architected using Cloud Native features
  - Driven by the need of the business to add features and improve scalability, performance, security, and agility
  - Move from a monolithic application to micro-services
  - Example: move an application to Serverless architecture, use AWS S3
 
## AWS Application Discovery Service
- Plan migration projects by gathering information about on-premises data centers
- Server utilization data and dependency mapping are important for migrations
- Agentless Discovery(AWS Agentless Discovery connector)
  - VM inventory, configuration, and performance history such as CPU, memory and disk usage
- Agent-based Discovery (AWS Applicaton Discovry Agent)
  - System configuration, system performance, running processses, and details of the network connections between systems
- Resulting data can be viewed within AWS Migration Hub
### AWS applicaton Migration Service (MGN)
- The "AWS evolution" of CloudEndure MIgration, replcing AWS server Migration Service (SMS)
- Lift-and-shift (rehost) solution which simplify migration applications to AWS
- Converts your physical,virtual, and cloud-based migration to run natively on AWS
- Minimal downtime, reduce costs
- Support wide range of platforms, os, and db
