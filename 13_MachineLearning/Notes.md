<img width="1834" height="910" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056424_start=75 (2)" src="https://github.com/user-attachments/assets/d9539871-97cf-4f61-8bc9-e6cb18ea214d" />## Amazon Rekognition
- Find objects, people, text, scenes in images and videos using ML
- Facial analysis and facial search to do user verification, people counting
- Create a databbase of "Familiar faces" or compare against celebrities
- Use cases:
  - Labeling
  - Content Moderation
  - Text Detection
  - Face Detection and Analysis (gender, age range, emotions..)
  - Face Search and verification
  - Celebrity Recongnition
  - Pathing(ex:for sports game analysis)
 
## Amazon Transcribe
- Automatically convert speech to text
- Uses a deep learning process called automatic speech reconfnition (ASR) to convert speech to text quickly and accurately
- Automatically remove Personally identifiable Infromation(PII) using Redaction
- Support Automatic Language Identification for multi-lingual audio
- Use cases:
  - Transcribe customer service calls
  - automate closes captioning and subtitling
  - generate metadata for media assets to create a fully searchable arcive

## Amazon Polly
- Turn text into lifelike speech using deeplearning
- Allow9i9ng you to create applications that talk

## Amazon Translate
- Natural and accurate language translation
- Amazon Translate allows you to localize content - such as websites and applications - for international users, and to easily translate large volumes of text efficiently.


## Amazon Lex & Connect 
- Amazon Lex:(same technology that powers Alexa
- Natural Language Understanding to recongnize the intent of text, callers
- Helps build chatbots, call center bots
## Amazon Connect:
- Receive calls, create contact flows, cloud-based virtual contact center
- Can integrate with other CRM systems or AWS
- No upfront payments, 80% cheaper than traditional contact center solutions
  <img width="1892" height="278" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20515578" src="https://github.com/user-attachments/assets/678989ba-27ea-470f-b83b-46eee9148a45" />
## Amazon Comprehend
- For Natural Language Processing - NLP
- Fully managed and serverless service
- Uses machine learning to find insights and relationships in text
  - Language of the text
  - Extracts key phrases, places, people, brands, or events
  - Understands how positive or negative the text is
  - Analyzes text using tokenization and parts of speech
  - Automatically organizes a collection of text files by topic
- Sample use cases
  - analyze customer interactions (emails) to find what leads to a positive or negative experience
  - Create and groups articles by topics that Comprehend will uncover
 
## Amazon SageMaker AI
- Fully managed service for developers / data scientists to build ML models
- Typically difficult to do all the processes in one place + provision servers
- Machine learning process (simplified): predicting your exam score
  
## Amazon Kendra
- Fully managed document search service powered by Machine Learning
- Extract answers from within a document (text, pdf, HTML, PowerPoint, MS Word, FAQ...)
- Natural language search capabilities
- Learn from user interactions/feedback to promote preferred results (Incremental Learning)
- Ability to manually fine-tune searh results (importance of data, freshness, custom,..)
<img width="1904" height="432" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_26623518_start=15" src="https://github.com/user-attachments/assets/fca8c619-fe5d-48f5-a717-bcbfb621089b" />

## Amazon Personalize
- Fully managed ML-service to build apps with real-time personalized recommendations
- Example: Personalized product recommmendations/re-ranking, customized direct marketing
  - Example: User bought gardening tools, provide recommendations on the next one to buy
- Same technology used by Amazon.com
- Integrates into existing websites, applications, SMS, email marketing system...
- Implement in day, not months (you don't need to build, train , and deploy ML solutions)
- Use cases: retail stores, media and entertainment

## Amazon Textract
- Automatically extracts text, handwriting, and data from any scanned documents using AL and ML
- Extract data from forms and tables
- Read and process any type of doucment and Imgs
- Use caese:
  - Financial Services (e.g. invoices, financial reports)
  - Healthcare (e.g. medicaal records, insurance claims)
  - Public Sector (e.g tax forms, ID document , passports)
 
## AWS Machine Learning - Summary
- Rekognition : face detection, labeling, celebrity recongnition
- Transcribe: audio to text
- Polly: text to autdio
- Translate: translations
- Lex: build conversational bots -chatbot
- Connect: cloud contact ceter
- Comprehend: natural language processing
- SageMaker: machine learning for every developer and data scientist
- Kendra : ML-powered search engine
- Personalilze: real-time personalized recommendations
- Textract: detect text and data in documents


---
---

## AWS Organizations
- Global service
- Allow to manage multiple AWS accounts
- The main account is the mast account
- Cost Benefits:
  - Consolidated Billing across all accounts - single payment method
  - Pricing benefits from aggregated usage (volume discount for EC2, S3..)
  - Pooling of Reserved EC2 instances for optimal savings
- API is available to automate AWS account creation
- Restrict account privileges using Service Control Policies (SCP)

## Multi Account Strategies
- Create accounts per department, per cost center, per dev /test/ prod, based on regulatory restrictions (using SCP), for better resourc isolation (ex:VPC), to have separated per-account service per-account service limits, isolated account for logging
- Multi account vs One Account Multi VPC
- Use tagging standards for billing purposes
- Enable CloudTrail on all accounts, send logs to central S3 account
- Send CloudWatch Logs to central logging account

## Organizational Units (OU) - Examples
<img width="2022" height="906" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056424_start=75" src="https://github.com/user-attachments/assets/1f0f51d1-3fb8-4da3-bcc8-af482795154d" />


- AWS Organization
  

<img width="1894" height="980" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056424_start=75 (1)" src="https://github.com/user-attachments/assets/c7a7fc39-fea2-4530-aa89-ab1db10c3abe" />

## Service Control Policies (SCP)
- Whitelist or blacklist IAM actions
- Applied at the OU or Account level
- Does not apply to the Master Account
- SCP is applied to all the Users and Roles of the Account, including Root
- The SCP does not affect service-linked roles
  - Service-linked roles enable other AWS services to integrate with AWS Organizations and cann't be restricted by SCP's
- SCP must have an explicit Allows (does not allow anything by default)
- Use cases:
  - Restrict access to certain services (for example:can't use EMR)
  - Enforce PCI compliance by explicitly disabling services
<img width="1834" height="910" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_20056424_start=75 (2)" src="https://github.com/user-attachments/assets/30876dcc-cfbe-4403-8a35-7721de0587bf" />


## AWS Organization - Consolidated Billing
- When enabled, provides you with:
  - Combine Usage - combined the usage across all AWS accounts in the AWS Organization to share the volume priing, Reserved Instances and Saving Plans discounts
  - One Bill - get one bill for all AWS Accounts in the AWS Organization
 
## AWS Control Tower
- Easy way to setup and govern a secure and compliant multi-account AWS environment based on best practices
- Benefits:
  - Automate the setup of your environment in a few clicks
  - Automate ongoing policy management using guardrails
  - Detect policy violations and remediate them
  - Monitor compliance through an interactive dashboard
- AWS Control Tower runs on top of AWS Organizations:
  - It automaticaly setup AWS Organizations to organize accounts and implement SCPs (Service Control Policies)

## AWS Resource Access Manager (AWS RAM)
- Share AWS resouces that you own with other AWS accounts
- Share with any account or withihng your Organization
- Avoid resource duplicaition!
- Supported resources include Aurora, VPC Subnets, Transit Gateway, Route 53, EC2 Dedicated Hosts, License Maner Configuratiosn..

## AWS Service Catalog 
- Users that are new to AWS have too many options, and may create stacks that are not compliant / in with the rest of the organization
- Some  users just want a quick self service portal to launch a set of authorized products pre-defined by admins
- Includes: virtual machines, databases, storage options, etc..
- Enter AWS Service Catalog!

### Service Categlog diagram
<img width="1846" height="1024" alt="www udemy com_course_aws-certified-cloud-practitioner-new_learn_lecture_36566038" src="https://github.com/user-attachments/assets/133b6da9-4de6-4994-b90d-ff628036d4f6" />
