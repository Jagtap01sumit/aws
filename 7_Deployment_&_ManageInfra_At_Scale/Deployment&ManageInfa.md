## Deploying workloads on AWS

- First techonology is CloudFormation
### CloudFormation
- CloudFormation is a declarative way of outlining your AWS Infrasturcture,
 for any resources (most of them are supported).
- For example, within a CloudFormation template, you say:
    - I want a security group
    - I want two Ec2 instances using this security group
    - I want an S3 bucket
    - I want a load balancer(ELB) in front of these machines
- Then CloudFOrmation creates those for you, in the right order, with the exact configuration that you specify
### Benefits of AWS CloudFormation(1/2)
##### Infrastructure as code
  - No resources are manually created, which is execellent for control
  - Changes to the infrastructure are reviewed through code
- Cost
    - Each resources within the stack is tagged with an identifier so you can easily see how much a stack costs you
    - You can estimate the costs of you resources using the CloudFormation template
    - Savings stragtegy: In Dev, you could automation deletion of templates at 5PM and recreated at 8 AM, safly
### Benefits of AWS CloudFormation (2/2)
- Productivity
    - Ability to destroy and re-create an infrastructure on the cloud on the fly
    - Automated generation of Diagram for your templates!
    - Declarative programming(no need to figure out ordering and orchestration)
- Don't re-invent the wheel
    - Leverage existing templates on the web!
    - Leverage the documentation
- Supports (almost) all AWS resources:
    - Everything we'll see in this course is supported
    - you can use "custom resources" for resouces that are not supported
 ## CloudFormation + Infrastructure Composer
 - Example: Wordpress CloudFormation Stack
 - We can see all the resouces
 - We can see the relations between the components
