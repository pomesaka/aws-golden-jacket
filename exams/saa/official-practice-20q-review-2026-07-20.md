# AWS Official Practice Question Set Review

Date: 2026-07-20

## Result

- Source: AWS Skill Builder official practice question set
- Questions: 20
- Correct: 11
- Incorrect: 9
- Score: 55%
- Skipped: 0
- Total time: 53m55s
- Average time per question: 2m42s

## Readiness assessment

- Do not book the SAA exam yet.
- The previous internal quiz performance overestimated readiness because many questions were narrow, sequential, or followed recent explanations.
- The official set exposed coverage gaps rather than a total lack of AWS understanding.
- Main issue: uneven topic coverage, especially storage, security-service boundaries, Windows file services, and some managed-database/serverless details.

## Incorrect-question clusters

### 1. Storage selection and performance

#### Question 3: temporary rendering storage

- Workload: disposable frame-rendering data
- Required capacity: up to 400 GB
- Required performance: about 40,000 random IOPS
- Weakness exposed: mapping EBS volume types to random IOPS, throughput, durability needs, and cost.
- Review targets:
  - gp3 vs io2
  - st1/sc1 are HDD and unsuitable for high random IOPS
  - instance store may be relevant for temporary high-performance data depending on the options and instance support

#### Question 7: long-term archive with two-hour retrieval

- Requirement: retain data at least five years
- Access frequency: almost never
- Retrieval requirement: available within two hours
- Weakness exposed: S3 Glacier retrieval times and archive-tier cost trade-offs.
- Review targets:
  - S3 Glacier Instant Retrieval
  - S3 Glacier Flexible Retrieval expedited/standard/bulk behavior
  - S3 Glacier Deep Archive retrieval windows
  - minimum storage durations and retrieval charges

#### Question 8: RDS MariaDB storage

- Existing database: 40 GiB and 1,000 IOPS
- CPU and memory instance type already selected
- Goal: most cost-effective RDS storage configuration
- Weakness exposed: RDS storage options and IOPS/capacity relationships.
- Review targets:
  - General Purpose SSD gp3/gp2
  - Provisioned IOPS io1/io2
  - when provisioned IOPS is unnecessary overprovisioning
  - RDS-specific differences from direct EBS usage

#### Question 16: Windows file servers and WorkSpaces

- Requirement: redundant storage for personal files and shared directories
- Existing Active Directory integration required
- Weakness exposed: AWS managed file-system selection.
- Review targets:
  - Amazon FSx for Windows File Server
  - SMB and Microsoft AD integration
  - Multi-AZ deployment
  - distinction from EFS, S3, FSx for Lustre, ONTAP, and OpenZFS

### 2. Security-service boundaries

#### Question 9: XSS and SQL injection behind CloudFront and ALB

- Weakness exposed: distinguishing WAF, Shield, and Firewall Manager.
- Review targets:
  - AWS WAF protects at L7 and includes SQL injection and XSS rules
  - AWS Shield addresses DDoS, especially L3/L4 and broader DDoS protection
  - AWS Firewall Manager centrally applies policies across accounts/resources; it is not the inspection engine itself
  - attach WAF web ACL at the correct edge or application integration point

#### Question 12: advanced layer-3 DDoS attack

- Workload: CloudFront in front of EC2-based website
- Requirement: AWS-managed solution, automatic detection and mitigation, minimal downtime and operational burden
- Weakness exposed: Shield Standard vs Shield Advanced and CloudFront's role.
- Review targets:
  - Shield Standard is included automatically for supported services
  - Shield Advanced adds enhanced detection, response support, cost protection, and advanced visibility
  - CloudFront helps absorb and distribute attacks
  - WAF is not the primary answer for pure layer-3 DDoS

### 3. Database authentication and latency

#### Question 11: DocumentDB and IAM-based access

- Requirement: use IAM for database access and streamline authentication
- Weakness exposed: supported IAM authentication behavior for DocumentDB and the distinction between service control-plane IAM and database authentication.
- Review targets:
  - verify current DocumentDB IAM database authentication support and connection method
  - distinguish IAM authorization for AWS APIs from database-level authentication
  - understand temporary tokens and driver/connection-string implications where supported

#### Question 20: API Gateway, Lambda, DynamoDB read latency

- Requirement: improve read latency
- Strong consistency not required
- Minimal operational burden
- Weakness exposed: eventual consistency, DAX, and when caching is appropriate.
- Review targets:
  - eventual consistency is DynamoDB's default and consumes half the read capacity of strongly consistent reads
  - DAX provides in-memory acceleration for repeated reads but requires DAX client/network integration and running a cluster
  - choose the lowest-operations option that actually addresses the presented bottleneck
  - compare Lambda memory/CPU tuning, API Gateway caching, DAX, and consistency settings when they appear as distractors

### 4. Serverless modernization

#### Question 18: intermittent EC2 workload

- Current state: large general-purpose EC2 instance in an Auto Scaling group remains running
- Workload: runs randomly a few times per day
- Max execution time: 10 minutes
- Memory: 4 GB
- Goal: reduce future cost
- Weakness exposed: recognizing event-driven Lambda migration candidates.
- Review targets:
  - Lambda supports up to 15 minutes and sufficient memory for this workload
  - EventBridge Scheduler/rules can trigger periodic or event-driven execution
  - compare Lambda with AWS Batch, Fargate, Spot, and scheduled Auto Scaling
  - constant EC2 uptime is wasteful for sparse short jobs

## Current strengths retained

- VPC endpoints, ENIs, and PrivateLink concepts
- SQS/Lambda event source mappings, maximum concurrency, partial batch failure, DLQs, and idempotency
- Cross-account IAM/S3/KMS authorization layers
- Aurora Global Database and DR fundamentals
- DynamoDB on-demand capacity basics
- ALB/NLB/GWLB architecture
- ECS/Fargate fundamentals

## Updated priority order

1. EBS and RDS storage types, IOPS, throughput, capacity, and cost
2. S3 archive classes, restore times, minimum durations, and retrieval fees
3. FSx variants, especially FSx for Windows File Server
4. WAF vs Shield Standard vs Shield Advanced vs Firewall Manager
5. DocumentDB authentication and IAM integration
6. DynamoDB consistency models, DAX, and read-latency design
7. EC2-to-Lambda/Fargate/Batch modernization decisions

## Next study action

- Stop broad service-identification quizzes for now.
- Reconstruct the nine incorrect questions with all answer choices and explanations when available.
- Build focused notes for the seven priority areas above.
- Retake the official 20-question set only after reviewing the concepts, not immediately from memory.
- Before booking the exam, complete at least one full-length official or high-quality mock and reach a stable score around 80% or higher; ideally repeat this twice.
