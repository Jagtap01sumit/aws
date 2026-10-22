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
