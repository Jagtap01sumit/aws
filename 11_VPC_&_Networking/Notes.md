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




