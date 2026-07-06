# SAA-C03 Domains

## Domain 1: Design Secure Architectures - 30%

### Task 1.1: Design secure access to AWS resources

Knowledge areas:

- Access controls and management across multiple accounts
- Federated access and identity services such as IAM and IAM Identity Center
- AWS global infrastructure
- Security best practices such as least privilege
- Shared responsibility model

Skills:

- Apply security best practices to IAM users and root users
- Design authorization with IAM users, groups, roles, and policies
- Design role-based access control with STS, role switching, and cross-account access
- Design multi-account strategy with Control Tower and SCPs
- Choose appropriate resource policies
- Decide when directory federation is needed

### Task 1.2: Design secure workloads and applications

Knowledge areas:

- Application configuration and credential security
- AWS service endpoints
- Ports, protocols, and network traffic controls
- Secure application access
- Security services such as Cognito, GuardDuty, and Macie
- External threat vectors such as DDoS and SQL injection

Skills:

- Design VPC architectures with security groups, route tables, network ACLs, and NAT gateways
- Determine public/private subnet segmentation
- Integrate Shield, WAF, IAM Identity Center, and Secrets Manager
- Secure external network connections with VPN and Direct Connect

### Task 1.3: Determine appropriate data security controls

Knowledge areas:

- Data access and governance
- Data recovery
- Data retention and classification
- Encryption and key management

Skills:

- Align AWS services to compliance requirements
- Encrypt data at rest with KMS
- Encrypt data in transit with ACM/TLS
- Implement access policies for encryption keys
- Implement backups and replication
- Implement data access, lifecycle, and protection policies
- Rotate encryption keys and renew certificates

## Domain 2: Design Resilient Architectures - 26%

### Task 2.1: Design scalable and loosely coupled architectures

Knowledge areas:

- API Gateway and REST APIs
- Managed services such as Transfer Family, SQS, and Secrets Manager
- Caching strategies
- Microservice design principles: stateless vs stateful
- Event-driven architecture
- Horizontal and vertical scaling
- Edge accelerators such as CDN
- Container migration
- Load balancing with ALB
- Multi-tier architecture
- Queuing and messaging concepts
- Serverless technologies such as Fargate and Lambda
- Object/file/block storage characteristics
- Container orchestration with ECS and EKS
- Read replicas
- Workflow orchestration with Step Functions

Skills:

- Design event-driven, microservice, and multi-tier architectures
- Choose scaling strategies by component
- Choose services for loose coupling
- Decide when to use containers or serverless
- Select compute, storage, networking, and database technologies by requirements
- Use purpose-built AWS services

### Task 2.2: Design highly available and/or fault-tolerant architectures

Knowledge areas:

- Regions, Availability Zones, Route 53
- Networking basics such as route tables
- DR strategies: backup and restore, pilot light, warm standby, active-active, RPO, RTO
- Distributed design patterns
- Failover strategies
- Immutable infrastructure
- Load balancing with ALB
- RDS Proxy
- Service quotas and throttling
- Storage durability and replication
- Workload visibility such as X-Ray

Skills:

- Determine automation strategies for infrastructure integrity
- Select services for HA/FT across Regions and AZs
- Identify metrics to meet availability requirements
- Mitigate single points of failure
- Ensure data durability and availability
- Select DR strategy by business requirement
- Improve reliability for legacy applications when code changes are not possible

## Domain 3: Design High-Performing Architectures - 24%

### Task 3.1: Determine high-performing and/or scalable storage solutions

- Hybrid storage
- S3, EFS, EBS
- Object, file, block storage characteristics
- Storage performance and scalability configuration

### Task 3.2: Design high-performing and elastic compute solutions

- Batch, EMR, Fargate
- Global infrastructure and edge services
- Messaging and publish/subscribe
- EC2 Auto Scaling and AWS Auto Scaling
- Lambda and Fargate
- ECS and EKS
- Decouple workloads so components scale independently
- Pick instance types, Lambda memory, and resource sizes

### Task 3.3: Determine high-performing database solutions

- AZs and Regions
- Caching with ElastiCache
- Read-heavy vs write-heavy access patterns
- Capacity planning and Provisioned IOPS
- Database connections and proxies
- Homogeneous and heterogeneous migrations
- Read replicas
- Relational, non-relational, in-memory, and serverless database types
- Aurora and DynamoDB

### Task 3.4: Determine high-performing and/or scalable network architectures

- CloudFront and Global Accelerator
- Subnet tiers, routing, IP addressing
- ALB and load balancing concepts
- VPN, Direct Connect, PrivateLink
- Global, hybrid, and multi-tier network topologies
- Placement and load balancing strategies

### Task 3.5: Determine high-performing data ingestion and transformation solutions

- Athena, Lake Formation, QuickSuite
- Data ingestion frequency
- DataSync and Storage Gateway
- Glue
- Secure ingestion access points
- Kinesis
- EMR
- Data lakes, streaming, transfer, visualization, and format transformation

## Domain 4: Design Cost-Optimized Architectures - 20%

### Task 4.1: Design cost-optimized storage solutions

- S3 Requester Pays
- Cost allocation tags, multi-account billing
- Cost Explorer, Budgets, Cost and Usage Report
- FSx, EFS, S3, EBS
- Backup strategies
- HDD vs SSD volume types
- Lifecycle policies and cold tiering
- DataSync, Transfer Family, Storage Gateway
- Storage access patterns

### Task 4.2: Design cost-optimized compute solutions

- Savings Plans, Reserved Instances, Spot Instances
- Edge processing
- Outposts
- Instance families and sizes
- Containers, serverless, and microservices for utilization
- Auto scaling and hibernation
- ALB vs NLB vs Gateway Load Balancer
- Horizontal vs vertical scaling
- Lambda, EC2, and Fargate cost tradeoffs

### Task 4.3: Design cost-optimized database solutions

- Cost tools
- Caching strategies
- Data retention
- Capacity units
- Connection/proxy patterns
- Database engines and migrations
- Read replicas
- RDS, Aurora, DynamoDB
- Snapshot frequency and backup policies

### Task 4.4: Design cost-optimized network architectures

- Cost tools
- ALB concepts
- NAT gateway vs NAT instance cost
- Direct Connect vs VPN vs internet
- Transit Gateway and VPC peering
- DNS
- NAT gateway placement strategy
- Network transfer cost routing
- VPC endpoints
- CDN and edge caching decisions
- Throttling strategy
- Bandwidth allocation
