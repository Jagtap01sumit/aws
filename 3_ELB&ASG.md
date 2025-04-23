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

### Why use a load balancers ?
* Spread load across multiple downstream instances
