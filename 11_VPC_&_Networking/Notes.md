## VPC 

### IP Addresses in AWS
- IPv4 - Internet Protocol version 4 (4.3 Billion Addresses)
	- Public IPv4 - can be used on the Internet
	- EC2 instance gets a new a public IP address every time you stop then start it (default)
	- Private IPv4 - can be used on private network (LAN) such as internal AWS networking (eg.,192.168.1.1)
	- Private IPv4 is fixed for EC2 Instances even if you start/stop them



## VPC 

### IP Addresses in AWS
- IPv4 - Internet Protocol version 4 (4.3 Billion Addresses)
	- Public IPv4 - can be used on the Internet
	- EC2 instance gets a new a public IP address every time you stop then start it (default)
	- Private IPv4 - can be used on private network (LAN) such as internal AWS networking (eg.,192.168.1.1)
	- Private IPv4 is fixed for EC2 Instances even if you start/stop them

- Elastic IP - allow you to attach a fixed public IPv4 address to EC2 instance
- Note: allow public IPv4 on AWS will be charged $0.005 per hour (including EIP)

- IPv6 - Internet Protocol version 6 (3.4 * 10^38 Addresses)
	- Every Ip address is public in AWS(no private range)
	- Example: 200I:db8.3333:4444:cccc:dddd:eeee:ffff
	- Free

### VPC & Subnets primer
- VPC - Virtual Private cloud: private network to deploy your sources (regional resource)
- Subnets allow you to partition your network inside your VPC (AZ resource)
- A public subnet is a subnet that is accessible from the internet
- To define access to the internet and between subnets, we use Route Tables

### VPC Diagram
<img width="1014" height="583" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20237290 (1)" src="https://github.com/user-attachments/assets/1b7f733b-a0e0-4199-ab38-1d76495fce01" />

### Internet Gateway & NAT Gateways
- Internet Gateways helps our VPC instance connect with the internet
- Public Subnets have a route to the internet gateway
- NAT Gateways(AWS-managed) & NAT Instances(self-managed) allow your instances in your Private subnets to access the internet while remaining private
##################172########2.30

### Network ACL & Security Groups
- NACL (Network ACL)
  	- A firewall which controls traffic from and to subnet
  	- Can have ALLOW and DENY rules
  	- Are attached at the subnet level
  	- Rules only include IP adresses

- Security Groups
  	- A firewall that controls traffic to and from an EC2 Instance
  	- Can have only ALLOW rules
  	- Rules include IP addresses and other security groups
  <img width="1048" height="528" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056244" src="https://github.com/user-attachments/assets/8013cbf5-40ab-430a-9c21-c2a0e03a00e6" />

### VPC Flow logs
- Capture information about IP traffic going into your interfaces:
  	- VPC Flow Logs
  	- Subnet Flow logs
  	- Elastic Network Interface Flow logs
  - Helps to monitor & troubleshoot connectivity issues. Example:
    	- Subnets to internet
    	- Subnets to subnets
  		- Internet to subnets
  - Captures network information from AWS managed interface too: Elastic Load Balancers, ElasticCache, RDS, Aurora, etc...
  -  VPC Flow logs data can go to S3, CloudWatch Logs, and Amazon Data Firehouse
 
  ### VPC Peering
  - Connect two VPC, privately using AWS network
  - Make them behave as if they were in the same network
  - Must not have overlapping CIDR(IP address range)
  - VPC Peering connection is not trasitive (must be established for each VPC that need to communicate with one another)
