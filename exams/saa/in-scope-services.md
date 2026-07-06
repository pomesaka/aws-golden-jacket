# SAA-C03 In-Scope Services

Source of truth: AWS official SAA-C03 in-scope services page.

AWS states that the in-scope list is non-exhaustive and subject to change.

## Priority 1: Must be covered before first diagnostic quiz

These services are either high-frequency SAA topics or already appeared as weak/important areas.

### Security, identity, and compliance

- IAM
- AWS IAM Identity Center
- AWS KMS
- AWS Secrets Manager
- AWS Certificate Manager
- AWS WAF
- AWS Shield
- Amazon Cognito

### Networking and content delivery

- Amazon VPC
- Elastic Load Balancing
- Amazon Route 53
- Amazon CloudFront
- AWS Global Accelerator
- AWS PrivateLink
- AWS Transit Gateway
- AWS Direct Connect
- AWS Site-to-Site VPN

### Storage

- Amazon S3
- Amazon S3 Glacier
- Amazon EBS
- Amazon EFS
- Amazon FSx
- AWS Backup
- AWS Storage Gateway

### Compute and containers

- Amazon EC2
- Amazon EC2 Auto Scaling
- AWS Lambda
- AWS Fargate
- Amazon ECS
- Amazon EKS
- AWS Batch

### Database

- Amazon RDS
- Amazon Aurora
- Amazon DynamoDB
- Amazon ElastiCache
- Amazon RDS Proxy

### Integration and serverless architecture

- Amazon SQS
- Amazon SNS
- Amazon EventBridge
- AWS Step Functions
- Amazon API Gateway

### Management and governance

- Amazon CloudWatch
- AWS CloudTrail
- AWS CloudFormation
- AWS Organizations
- AWS Control Tower
- AWS Systems Manager
- AWS Trusted Advisor
- AWS Cost Explorer
- AWS Budgets

## Priority 2: Cover after first diagnostic quiz

### Analytics and data movement

- Amazon Athena
- Amazon Data Firehose
- Amazon EMR
- AWS Glue
- Amazon Kinesis
- AWS Lake Formation
- Amazon MSK
- Amazon OpenSearch Service
- Amazon Redshift
- AWS DataSync
- AWS Database Migration Service
- AWS Transfer Family
- AWS Snow Family

### Additional database services

- Amazon DocumentDB
- Amazon Keyspaces
- Amazon Neptune

### Additional security services

- AWS Artifact
- AWS Audit Manager
- AWS CloudHSM
- Amazon Detective
- AWS Directory Service
- AWS Firewall Manager
- Amazon GuardDuty
- Amazon Inspector
- Amazon Macie
- AWS Network Firewall
- AWS Resource Access Manager
- AWS Security Hub

### Additional compute / edge / hybrid

- AWS Elastic Beanstalk
- AWS Outposts
- AWS Serverless Application Repository
- VMware Cloud on AWS
- AWS Wavelength

### Machine learning / front-end / media

- Amazon Comprehend
- Amazon Kendra
- Amazon Lex
- Amazon Polly
- Amazon Rekognition
- Amazon SageMaker AI
- Amazon Textract
- Amazon Transcribe
- Amazon Translate
- AWS Amplify
- AWS AppSync
- AWS Device Farm
- Amazon Elastic Transcoder
- Amazon Kinesis Video Streams

## Personal priority bias

Given current hands-on experience, the first diagnostic should not spend too much time on ECS/Fargate basics. Instead it should stress:

- IAM/KMS/resource policies
- VPC endpoints and private connectivity
- Route 53/CloudFront/Global Accelerator
- S3/EFS/EBS/FSx selection
- RDS/Aurora/DynamoDB/ElastiCache selection
- DR and high availability patterns
- Cost-optimized network/storage/compute choices
