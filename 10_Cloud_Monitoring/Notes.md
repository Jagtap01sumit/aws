
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

##################161######1.46#######
### Amazon EventBridge
##################161##############2.30

### AWS CloudTrail
- Provides governance, compliance and audit for your AWS Account
- CloudTrail is enabled by default!
- Get an history of events/API calls made within your AWS Account by:
	- Console
	- SDK
	- CLI





