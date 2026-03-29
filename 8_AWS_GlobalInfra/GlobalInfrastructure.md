### Why make a global application?
- A global application is an application deployed in mulitple geographies
- On AWS: this coulb be Regions and /or Edge Locations
- Degreased Latency
    - Latency is the time it takes for anetwork packet to reach a server
    - It takes time for a packet from Asia to reach the US
    - Deploy your applications closer to your users to decrease latency, better experience
- Diasster Recovery (DR)
    - If an AWS region goes down(earthquake, storms, power shutdown, politics)..
    - You can fail-over to another region and have your application still working
    - A DR plan is important to increase the availability of your application
 
- Attack protection: distributed global infrastruture is harder to attack
### Global Applications in AWS:
- Global DNS:Route 53
    - Great to route users to the closest deployment with least latency
    - Great for disaster recovery strategies
- Global Content Delivery Network (CDN):CLoudFront
    - Replicate part of your application to AWS edge Locations - decrease latency
    - Cache common requests-imporved user experience and decreased latency
- S3 Transfer Acceleration
    - Accelerate global upload & downloads into Amazon S3
- AWS Global Accelerator:
    - Improve global application availability and performace using the AWS global network
## 1. Amazono Route 53 Overview
 - Route 53 is a Managed DNS(Domain Name System)
 - DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
<img width="995" height="589" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112" src="https://github.com/user-attachments/assets/87b9d8c1-72df-45df-bcb9-c4b8701d59e0" />

### Route 53 Routing Policies
- Need to know them at a high-level for the Cloud practitioner exam
    1. Simple Routing Policy
    2. Weight Routing Policy
    3. Latency Routing Policy
    4. Failover Routing Policy
<img width="1089" height="564" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (2)" src="https://github.com/user-attachments/assets/18fcc309-2c78-40a8-b93c-245616aeb72b" />
<img width="1093" height="573" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (3)" src="https://github.com/user-attachments/assets/5b5b0d34-5889-4feb-8193-e9b7ad9065c2" />

### AWS CloudFront
- Content Delivery Network (CDN)
- Improves read performance, content is cached at the edge
- Improves users experience
- Hundreds of Points of Presenece globally (edge locations, caches)
- DDos protection (because worldwide), integration with shield, AWS Web Application Firewall
#### CloudFront Origins
- S3 bucket
    - For distributing files and caching them at the edge
    - For uploading files to S3 through CloudFront
    - Secured using Origin Access Control (OAC)
- VPC Origin
    - For applications hosted in VPC private subnets
    - Private Application Load Balancer/Network Load Balancer /EC2 Instances
- Custom Origin (HTTP)
    - S3 website (must first enable the bucket as a static S3 webstite)
    - Any public HTTP backed you want (example:public ALB)
#### CloudFront at a high level
<img width="1098" height="548" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056120" src="https://github.com/user-attachments/assets/e11f55f5-a408-4387-8e43-0bfa1671dd70" />
<img width="1101" height="568" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056112 (1)" src="https://github.com/user-attachments/assets/e38ea359-099c-4ec1-8b8e-b5766c2be1c4" />
- data was cached in edged locations

### CloudFront Vs S3 Cross Region Relication
- CloudFront
    - Use Global Edge network
    - Files are cached for a TTL(maybe a day)
    - Great for static content that must be available everywhere
- S3 Cross Region Replication:
    - Must be setup for each region you want replication to happen
    - Files are updated in near real-time
    - Read only
    - Great for dynamic content that needs to be available at low-latency in few regions
