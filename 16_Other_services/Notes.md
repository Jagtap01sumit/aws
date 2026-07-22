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
