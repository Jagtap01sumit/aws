## ELS & ASG - Elastic Load Balancing & Auto Scaling Groups

### Scalability
 * Scalability means that an application/ system can handle greater loads by adapting
 * There are two kinds of scalability:
     * 1. Vertical Scalability
     * 2. Horizontal Scalability (= elasticity)
* Scalability is linked but different to High Availability
* Let's deep dive into the distinction, using a call center as an example

#### 1. Veritical Scalability
* Vertical Scalability means increasing the size of the instance
* For example, your application runs on a t2.micro
* Scaling that application vertically means running it on a t2.large
* Vertical scalability is very common for non distributed systems, such as a databases.
* There's usually a limit to how much you can vertically scale (hardware limit)

#### 2. Horizontal Scalability
* Horizontal Scalability means increasing the number of instances/ systems for your application
* Horizontal scaling implies distributed systems.
* This is very common for web application/ modern applications.
* It's easy to horizontally scale thanks the cloud offering such as Amazon EC2

#### High Availability
* High Availability usually goes hand in hand with horizontal scaling
* High availibility means running your application/ system in at least 2 Availability zones
* The goal of high availability is to survive a data center loss (disaster)

## High Availability & Scalability for EC2
* Vertical Scaling : Increase instance size (= scale up / down)
    * From: t2.nano - o.5G of RAM, 1 vCPU
    * To: u-I2tb I . metal -123 TB of RAM, 448 vCPUs
  * Horizontal Scaling: Increase number of instances (= scale out /in)
      * Auto scaling group
      * Load Balancer
  * High Availability: Run instances for the same application across multi AZ
      * Auto Scaling Group multi AZ
      * Load Balancer multi AZ
> [!note]
> IMP - Scalability vs Elasticity (vs Agility)

>  [!IMPORTANT]
> <b>Scalability</b>: ability to accommondate a large load by making the hardware stronger (scale up) , or by adding nodes (scale out)

> [!IMPORTANT]
>  <b>Elasticity</b>: once a system is scalable, elasticity means that there will be some "auto-scaling" so that the system can scale based on the load. This is "cloud-friendly": pay-per-use, match demand, optimize costs.

>  [!IMPORTANT]
>  <b>Agility</b>: (not related to scalability - distractor) new IT resources are only a click away, which means that you reduce the time to make those resources availble to your developers from weeks to just minutes.


## Elastic Load Balancing

### what is load balancing ?
##### Load balancers are servers that forward internet traffic to muliple servers (EC2 instances) downstream.

![image](https://github.com/user-attachments/assets/2bc1285f-0529-40d9-9591-0ea4b04ebf19)

#### Why use a load balancers ?
* Spread load across multiple downstream instances
* Expose a single point of access (DNS) to your applicatiohn
* Seamlessly handle failures of downstream instances
* Do regular healt checks to your instances
* Provide SSL termination (HTTPS) for your websites
* High availability across zones

#### Why use an Elastic Load Balancer ?
* An ELB (Elastic Load Balancer) is a managed load balancer
     *  AWS guarantees that it will be working
     *  AWS takes casreof upgrades, maintaince, high availability
     *  AWS provides only a few configuration knobs
* It costs less to setup your own load balancer but it will be a lot more efforts on your end (maintenance, integreation)
* 4 Kinds of load balancers offered by AWS:
      * Application Load Balancer (HTTP/ HTTPS only) - layer 7
      * Network Load Balancer (ultra - high performance, allows for TCP ) - layer 4
      * Gateway Load Balancer - Layer 3
      * Classic Load Balancer (retired in 2023) - Layer 4 & 7

![image](https://github.com/user-attachments/assets/e113b3b9-2b69-48e5-95aa-60423ed9078e)
## Auto Scaling Group 

#### What's an Auto Scaling Group ?
* In real-life, the load on your websites and application can change
* In the cloud, you can create and get rid of servers very quickly
* The goal of an Auto Scaling Group (ASG) is to:
    * Scale out (add EC2  instances) to match an increased load
    * Scale in (remove EC2 instance) to match a decreased load
    * Ensure we have a minimum and a maximum number of machines running
    * Automatically register new instances to a load balancer
    * Rplace unhealthy instances
  * Cost savings: only run at an optimal capacity (principle of the cloud) 

![image](https://github.com/user-attachments/assets/c155a6bf-31f6-497d-a869-928dec77f48d)

![image](https://github.com/user-attachments/assets/57e2578c-507e-4ec5-b24b-579218d84be9)

### Auto Scaling Groups - Scaling Strategies

* Manual Scaling : Update the size of an ASG manually
* Dynamic Scalilng : Respond to changing demand
      * Simple / Step Scaling:
          * When a CloudWatch alarm is triggered (example CPU > 0% ), then add 2 units
          * When a CloudWatch alarm is triggered (example CPU < 30%) , thene remove 1
* Target Tracking Scaling
      * Example: I want the average ASG CPU to stay at around 40%
* Scheduled Scaling:
      * Anticipate a scaling based on known usage patterns
      * Example: increase the min. capacity to 10 at 5 pm on Fridays
* Predictive Scaling:
      * Uses Machine learning to predict future traffic ahead of time.
      * Automatically provisions the right number of EC2 instances in advance
