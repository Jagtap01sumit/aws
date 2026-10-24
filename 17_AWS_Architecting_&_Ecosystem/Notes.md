### Well Architected Framework General guiding principle
- Stop guessing you capacity needs
- Test systems at production scale
- Automate to make architectural experimentation easier
- Allow for evolutionary architectures
    - Design based on changing requirements
- Drive architectures using data
- Improve through game days
  - Simulate applications for flash sale days


### AWS Cloud Best Practices - Design Principles
- Scalability: vertical & Horizontal
- Disposable Resources: servers should be disposable & easily configured
- Automation: Serverless, Infrastructure as a Service, auto scaling...
- Lose Coupling:
    - Monolith are applications that do more and more over time, become bigger
    - Break it down into smaller, loosely coupled components
    - A change or a failure in one component should not cascade to other components
- Services, not servers:
    - don't use just EC2
    - Use manged services, databases, serverless, etc!
 
## Well Architected Framework 6 pillors
1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainablity

- They are not something to balance, or trade-offs, they're a synergy

## 1. Operational Excellence 
- Includes the ability to run and monitor systems to deliver business value and to continueally improve supporting processes and procedures
- Design Principles
    - Perform operations as code - Infrastructure as code
    - Make frequent, small, reversible changes - So that in case of any failure, you can reverse it
    - Refine operations procedures frequntly - And ensure that team members are familiar with it
    - Anticipate failure
    - Learn from all operational failures
    - Use managed services - to reduce operational burden
    - Implement observability for actionable insights - performance, reliability, cost...

#### 1. Operational Excellence AWS Service
   - Prepare
       - AWS CloudFormation
       - AWS Config
   - Operate
       - AWS CloudFormation
       - AWS Config
       - AWS CloudTrail
       - Amazon CloudWatch
       - AWS X-Ray
  - Evolve
       - AWS CLoudFormation
       - AWS CodeBuild
       - CodeCOmmit
       - CodeDeploy
       - CodePipeline
#### 2. Security
- Security
    - Includes the ability to protect information, systems, and assests while delivering business value through risk assessments and miitigation strategies
    - Design principles
        - Implement a strong identify foundation - Centralize privilege management and reduce (or even eliminate) reliance on long-term credentials - principle of least privilege - IAM
        - Enable traceability - Integrate logs and metrics with system to automatically respond and take action
        - Apply security at all layers - Like edge network, VPC, subnet, load balancer, every isntance, operating system, and application
        - Automate security best practices
        - Protect data in transit and at rest - Encryption, tokenization, and access control
        - Keep people away from data - Reduce incident response simulations and use tools with automation to increase your speed to detection, investigation and recover
        
- AWS Services
    - Identity and Access Management
        - IAM
        - AWS-STS
        - MFA token
        - AWS Organizations
      - Detective Controls
        - AWS Config
        - AWS CloudTrail
        - Amazon CloudWatch
      - Infrastructure Protection
          - Amazon CloudFront
          - Amazon VPC
          - AWS Shield
          - AWS WAF
          - Amazon Inspector
      - Data protections
          - KMS
          - S3
          - Elastic Load Balancing (ELB)
          - Amazon EBS
          - Amazon RDS
     - Incident Response
          - IAM
          - AWS CloudFormation
          - Amazon CloudWatch Events


#### 3. Reliability
- Ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues
- Design Principles
    - Test recovery procedures - Use automation to simulate different failures or to recreate scenarios that let to failures before
    - Automatically recover from failure - Anticipate and remediate failures before they occure multiple, smaller resources to ensure that they don't share a common point of failure
      - Stop guessing capacity - Maintain the optimal level to satisfy demand without over or under provisioning - Use Auto Scaling
      - Manage change in automation - Use automation to make changes to infrastrucure

- AWS Services
    - Foundations
        - IAMM
        - Amazon VPC
        - Service Limits
        - AWS Trusted Advisor
    - Change Management
        - AWS Auto Scaling
        - Amazon CloudWatch
        - AWS CloudTrail
        - AWS Config
    - Failure Managment
        - Backups
        - AWS CloudFormation
        - Amazon S3
        - Amazon S3 Glacier
        - Amazon Route 53
     
#### 4. Performace Efficiency
- Includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve
- Design Principles
    - Democratize advanced techonogies - Advance technologies become services and hence you can focus more on product development
    - Go global in minutes - Easy deployment in multiple  regions
    - Use serverless architectures - Avoid burden of managing servers
    - Experiment more often - Easy to carry out comparative testing
    - Mechanical sympathy - Be aware of all AWS Services
 
- AWS Services
    - Selections
          - AWS autoscaling
          - AWS Lambda
          - Amazon Elastic Block Store (EBS)
          - Amazon Simple Storage Service (S3)
          - Amazon RDS
      - Review
            - Aws CloudFormation
            - AWS News Blog
      - Monitoring
            - Amazon CloudWatch
            - AWS Lambda
      - Tradeoffs
            - Amazon RDS
            - Amazon ElasticCache
            - Amazon CloudFront
