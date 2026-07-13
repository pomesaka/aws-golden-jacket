# SAA Session Handoff

Last updated: 2026-07-13

## Current status

- Completed diagnostic questions: Q1-Q30
- Invalid questions excluded from scoring: Q16 and Q19
- Valid scored questions: 28
- Correct: 23
- Incorrect: 5
- Raw score: 82.1%
- Confidence-adjusted learning score: 76.8%
- Mode: hard mode from Q15 onward
- Recommendation: do not book the exam yet; complete weak-area retests and a full-length mixed mock first

## Important scoring note

The diagnostic was designed to measure readiness, not to fully cover every SAA topic. Some later questions followed immediately after detailed explanations, so the raw score should not be treated as a direct exam-pass probability.

## Incorrect answers

| Question | Topic | Confidence | Main issue |
|---|---|---:|---|
| Q8 | Route 53 latency routing vs Global Accelerator | 4/5 | Missed the explicit DNS-level requirement |
| Q17 | VPC Endpoint / NAT design | 4/5 | Endpoint type and private path misconception |
| Q20 | DR strategy selection | 2/5 | Pilot light vs warm standby / RPO-RTO mapping |
| Q23 | SNS fan-out, SQS, Lambda, DLQ | 5/5 | High-risk multi-response and architecture misconception |
| Q24 | DynamoDB capacity mode | 2/5 | On-demand vs provisioned Auto Scaling vocabulary and spike behavior |

## Correct but low-confidence answers

| Question | Topic | Confidence | Retest focus |
|---|---|---:|---|
| Q25 | Organizations SCP regional guardrail | 2/5 | SCP vs IAM policy vs permissions boundary; aws:RequestedRegion |
| Q26 | S3 storage classes and lifecycle | 1/5 | Standard-IA, One Zone-IA, Glacier tiers, restore times, minimum durations |
| Q27 | Aurora reader endpoint and failover | 2/5 | Cluster endpoint vs reader endpoint vs instance endpoint; reader promotion |

## High-confidence strengths demonstrated

- S3 Gateway VPC Endpoint and NAT cost avoidance
- RDS Proxy for Lambda / serverless connection storms
- CloudFront with private S3 origin, OAC, bucket policy, signed access
- RDS Multi-AZ vs Read Replica
- ElastiCache vs Read Replica for repeated cacheable reads
- Route 53 failover and weighted routing
- Global Accelerator basics and static IP use case
- EFS for shared POSIX access
- Basic KMS and S3 SSE-KMS permission layering
- Basic SCP preventive guardrail concept

## Weak services to prioritize

1. Amazon SNS, Amazon SQS, Lambda event source mappings, retries, DLQs
2. IAM, S3 bucket policies, KMS key policies, SCPs, permissions boundaries
3. DynamoDB capacity modes and access-pattern features
4. Route 53 routing policies and Global Accelerator comparison
5. S3 storage classes and archive behavior
6. Aurora endpoints, replicas, failover, Global Database
7. Disaster recovery strategies and RPO/RTO

## Weak concepts to prioritize

1. Multi-response questions: verify every requirement is covered before answering
2. Separate network reachability from authorization
3. Separate identity policy, resource policy, and KMS key policy evaluation
4. Translate RPO/RTO and cost requirements into DR strategy
5. Distinguish connection pooling, caching, read scaling, and database HA
6. Prefer the best-fit solution, not merely a technically possible solution
7. Watch for wording such as DNS-level, private path, minimal changes, global static IP, or immediate retrieval

## Topics covered in the diagnostic

- S3 SSE-KMS and customer-managed KMS keys
- ALB sticky sessions vs external session state
- S3 Gateway VPC Endpoint
- ElastiCache vs RDS Read Replica
- CloudFront with private S3 content
- AWS Organizations SCP
- Direct Connect vs VPN / Peering / Transit Gateway basics
- Route 53 latency, failover, and weighted routing
- EFS vs EBS
- RDS Multi-AZ and read replicas
- Global Accelerator
- CloudFront static-content acceleration
- Cross-account S3 and KMS concepts
- DR strategy selection
- SNS / SQS / Lambda messaging design
- DynamoDB capacity modes
- S3 lifecycle and Glacier Deep Archive
- Aurora reader endpoint and failover
- RDS Proxy
- Gateway vs Interface VPC Endpoints
- CloudFront OAC and private S3 origin

## Important topics not yet covered well enough

### Compute and load balancing

- ALB vs NLB vs GWLB
- Auto Scaling policies, lifecycle hooks, health checks, cooldowns / warmup
- EC2 purchase options: On-Demand, Reserved Instances, Savings Plans, Spot
- Placement groups
- AMIs, launch templates, instance store

### Containers and serverless

- ECS vs EKS vs Fargate vs EC2
- API Gateway REST vs HTTP vs WebSocket APIs
- Lambda concurrency, reserved concurrency, provisioned concurrency
- Lambda destinations, asynchronous retries, event source mappings
- Step Functions vs SQS vs EventBridge

### Networking and hybrid connectivity

- Direct Connect resiliency models and VPN backup
- Transit Gateway routing and multi-account patterns
- VPC peering limitations and non-transitive routing
- PrivateLink architecture
- NAT Gateway per-AZ design and cross-AZ cost
- Network Firewall, security groups, NACLs

### Security and governance

- WAF vs Shield Standard vs Shield Advanced
- ACM certificate placement and service integration
- CloudTrail vs Config vs CloudWatch vs EventBridge
- Organizations vs Control Tower
- IAM Identity Center
- Secrets Manager vs SSM Parameter Store
- Cognito user pools vs identity pools

### Storage and migration

- EBS volume types and performance
- FSx variants
- AWS Backup
- DataSync vs Storage Gateway vs Snow Family vs Transfer Family
- S3 replication, versioning, Object Lock, multipart upload

### Database and analytics

- DynamoDB GSI vs LSI, DAX, Streams, Global Tables, TTL, transactions
- Aurora Serverless
- Aurora Global Database switchover vs failover
- ElastiCache Redis vs Memcached
- Redshift, Athena, Glue, OpenSearch, EMR high-level selection

### Reliability and operations

- CloudWatch metrics, alarms, logs, dashboards
- Systems Manager capabilities
- Backup and restore design across services
- Multi-Region active-active vs active-passive architectures
- Route 53 geolocation, geoproximity, multivalue answer routing

## Recommended next sequence

1. Retest Q23 topic: SNS fan-out, one SQS queue per consumer, Lambda retry and DLQ behavior
2. Retest Q17 topic: Gateway Endpoint, Interface Endpoint, NAT Gateway, route tables, private DNS
3. Retest Q8 topic: Route 53 latency routing vs Global Accelerator
4. Drill DR strategies with RPO/RTO scenarios
5. Drill DynamoDB on-demand vs provisioned Auto Scaling
6. Drill IAM + bucket policy + KMS key policy cross-account cases
7. Drill S3 storage-class selection
8. Drill Aurora endpoints and failover
9. Run an uncovered-topic set of 20-30 questions
10. Run a 65-question mixed mock under exam timing

## Exam booking gate

Do not book until all are true:

- High-confidence misconceptions are retested successfully
- Weak-area set is at least 80%
- Two full-length mixed mocks are at least 80%
- Multi-response omission errors are rare
- Current official SAA exam guide and in-scope services have been checked

## Next-session instruction

Start by reading this file and `exams/saa/diagnostic-summary.md` if present. Then continue with a targeted weak-area quiz, beginning with SNS/SQS/Lambda and VPC endpoint/NAT scenarios. Keep questions exam-like, use plausible distractors, and grade reasoning strictly.