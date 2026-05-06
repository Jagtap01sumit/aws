
## Cloud Monitoring Section

### CloudWatch Metrics
- CloudWatch providers metrics for every services in AWS
- Metric is a variable to monitor (CPUUtilization, Networkln..)
- Metrics have timestamps
- Example: CloudWatch Billing metric
-Important Metrics
	- EC2 instances:CPU Utilization, Status Checks, Network (not RAM)
		- Default metrics every 5 minutes
		- Option for Detailed Monitoring($$$): metrics every 1 minute
	- EBS volumes: Disk Read/writes
	- S3 bucket: BucketSizeBytes, NumberOfObjects, AllRequests
	- Billing: Total Estimated Charge(Only in us-east-1)
	- Service limits: how much you've been using a service API
	- Custom metrics: push your own metrics

### cloudWatch Alarms
- Alarms are used to trigger notifications for any metric
- Alarm actions...
	- Auto Scaling: increase or decrease Ec2 instances "desired" count
	- EC2 Actions: stop, terminate, reboot or recover an EC2 instance
	 SNS notifications: send a notification into an SNS topic
- Various options(sampling, %, max, min, etc..)
- Can choose the period on which to evaluate an alarm
- Example: create a billing alarm on the CloudWatch Billing metric
- Alarm states: OK. INSUFFICIENT_DATA, ALARM

#### Create alarm
- CloudWatch -> Alarms -> all alarms -> create alarm -> select metric (EC2) -> statstic(Average)-> conditions (if cpu utilization is greater than 80) treat them as alarm

### Amazon CloudWatch Logs
- CloudWatch Logs can collect log from:
	- Elastic Beanstalk: collection of logs from application
	- ECS: collection from containers
	- AWS Lambda: collection from function logs
	- CloudTrail based on filter
	- CloudWatch log agents: on EC2 machines or on-premises servers
	- Route53:Log DNS queries
- Enable real-time monitoring of logs
- Adjustable CloudWatch Logs retention
- By default, no logs from your EC2 instance will got to CloudWatch
- you need to run a CloudWatch agent on EC2 to push the log files you want 
- Make sure IAM permissions are correct
- The CloudWatch log agent can be setup on-premises too

### Amazon EventBridge (formerly CloudWatch Events)
- Schedule: Cron jobs (scheduled scripts)
- Event Pattern: Event rules to react to a service doing something
- Trigger lambda functions, send SQS/SNS notifications
<img width="1159" height="600" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056214" src="https://github.com/user-attachments/assets/bfebf344-b23f-44d9-adf0-9b8ce790c47a" />

### Amazon EventBridge

<img width="1074" height="556" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056214 (1)" src="https://github.com/user-attachments/assets/21388e1b-b706-48bb-bd1a-dbd7f5828931" />

### AWS CloudTrail
- Provides governance, compliance and audit for your AWS Account
- CloudTrail is enabled by default!
- Get an history of events/API calls made within your AWS Account by:
	- Console
	- SDK
	- CLI
	- AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3
- A trail can be applied to All Regions (Default) or a Single Region
- If a resource is deleted in AWS, investigate CloudTrail first!

 ###########163#################2.1


- search cloudtrail -> lefthand side -> event history -> all history will be there


### AWS X-Ray
- Debugging in production, the good old way:
	- Test locally
	- Add log statements everywhere
	- Redeploy in production
- Log formats differ across applications and log analysis is hard.
- Debugging: one big monolith "easy", distributed services "hard"
- No common views of your entire architecture
- Enter... AWS X-Ray!

#### Visual analysis of our application
################################165##########1,15

#### AWS X-Ray advantages
- Troubleshooting performance (bottlenecks)
- Understand dependencies in a miroservice architecture
- Pinpoint service issues
- Review request behavior
- Find errors and exceptions
- Are we meeting time SLA?
- Where I am throttled?
- Identify users that are impacted


### Amazon CodeGuru
- An ML-powered service for automated code reviews and application performance recommendations
- Provides two functionalities
	- CodeGuru Reviewer: autoamated code reviews for static code analysis(development)
	- CodeGuru profiler: visibility/recommendations about application performance during runtime(production)
########################166#######1.15

#### Amazon CodeGuru Reviewer
- Identify critical issues, security vulnereability, and hard-to-find bugs
- Example: common coding best practices, resource leaks, security detection, input validation
- Uses Machine learning and automated reasoning
- Hard-learned lesson across millions of code reviews on 1000s of open-source and Amazon respositories
- Supports java and python
- Integrates with Git-hub, Bitbucket, and AWS codecommit

#### Amazon CodeGuru profiler
- Helps understand the runtime behavior of your application
- Example: identify if your application is consuming excessive CPU capacity on a logging routine
- Features:
	- Identify and remove code inefficiencies
	- Improve application performance (e.g. reduce CPU utilization)
	- Decrease compute costs
	- Provides heap summary (identify which objects using up memory)
	- Anomaly Detection
- Support applications running on AWS or on-premise
	- Minimal overhead on application




### AWS Health Dashboard

### Monitoring Summary
- CloudWatch 
	- Metric: monitor the performance of AWS services and billing metrics
	- Alarms: automate notification, perform EC2 action, notify to SNS based on metric
	- Logs: collect log files from EC2 instances, servers, Lambda functions...
	- Events (or EventBride): react to events in AWS, or trigger a rule on a schedule
- CloudTrail Insights: automated analysis of your CloudTrail Events
- X-Ray: trace requests made through your distributed application
- AWS Health Dashboard:  status of all AWS services across all regions
- AWS Account Health Dashboard: AWS events that impact your infrastructure 
- Amazon CodeGuru: automated code reviews and application performance recommendations







