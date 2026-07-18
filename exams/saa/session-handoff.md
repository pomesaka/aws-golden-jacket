# SAA Session Handoff

Last updated: 2026-07-18

## Current status

- Completed diagnostic questions: Q1-Q30
- Invalid questions excluded from scoring: Q16 and Q19
- Valid scored questions: 28
- Correct: 23
- Incorrect: 5
- Raw score: 82.1%
- Confidence-adjusted learning score: 76.8%
- Mode: uncovered-topic questions at SAA-plus difficulty, with SAP-level related knowledge explained after grading
- Recommendation: do not book the exam yet; complete uncovered-topic coverage and a full-length mixed mock first

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
- ECS/Fargate selection based on operational responsibility
- Private Fargate access to ECR, S3, CloudWatch Logs, and Secrets Manager through VPC endpoints

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
8. Build a stronger mental model of network interfaces, ENIs, MAC addresses, and endpoint ENIs

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

## Uncovered-topic quiz progress

### Q1: ALB vs NLB vs GWLB

- Answer selection slip, but reasoning identified the intended answer.
- GWLB was initially unknown.
- Follow-up covered GWLB, GWLBe, third-party virtual appliances, centralized inspection VPCs, GENEVE over UDP 6081, symmetric routing, Transit Gateway appliance mode, and why reverse traffic can hit a different stateful firewall.

### Q2: Auto Scaling health checks

- Answer: A
- Confidence: 5/5
- Correct.
- Question was judged too easy and should not be used as the target difficulty.

### Q3: Auto Scaling Instance Refresh

- User selected A, C, D with confidence 4/5 based partly on Kubernetes operational intuition.
- The question was invalid because B was also correct despite asking for three choices.
- Follow-up covered Min/Max Healthy Percentage, health-check grace period, instance warmup, lifecycle hooks, checkpoints, bake time, CloudWatch alarms, auto rollback limitations, launch-template versions, skip matching, scaling interactions, maintenance policies, Spot/Mixed Instances, AZ capacity, and deregistration delay.
- Key distinction retained:
  - Grace period: do not kill an instance while it is still initializing.
  - Warmup: do not count a newly healthy instance as fully settled yet.
  - Deregistration delay: load-balancer-side connection draining, usually combined with lifecycle hooks and application shutdown handling.

### Q4: ECS compute mode selection

- Answer: B, ECS on AWS Fargate
- Confidence: 4/5
- Correct.
- Reasoning correctly eliminated ECS on EC2 due to host management and EKS managed node groups due to higher Kubernetes operational overhead.
- ECS Anywhere was introduced as ECS control of external/on-premises hosts.
- Follow-up covered cases requiring host access: security/monitoring agents, host paths, Docker socket, special devices, low-level networking, kernel/eBPF, and node-level agents.

### Q5: Private Fargate access to AWS services

- Answer: A, B, E
- Confidence: 4/5
- Correct.
- Strong point: explicitly recognized that ECR image layers require S3 connectivity in addition to ECR API and ECR DKR endpoints.
- Follow-up covered Interface endpoints, S3 Gateway endpoint, per-AZ endpoint ENIs, Private DNS, endpoint security groups, task execution IAM roles, endpoint policies, NAT cost and availability tradeoffs, and subnet IP consumption.

## Recent networking deep dives

- A network interface is the OS-visible send/receive attachment point, such as `en0`, `eth0`, or `ens5`.
- A machine may have multiple network interfaces, and each interface normally has its own MAC address.
- In AWS, an ENI is a VPC-scoped virtual NIC carrying subnet/AZ placement, private IPs, MAC address, security groups, and other attributes.
- An AWS Interface VPC Endpoint is materially implemented by endpoint ENIs placed into selected subnets, plus PrivateLink service attachment, DNS integration, security groups, endpoint policies, and control-plane management.
- A Gateway VPC Endpoint is different: it does not place an endpoint ENI in the subnet; it uses route-table entries for supported services such as S3 and DynamoDB.

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
- ENI behavior, multi-homing, source/destination checks, and subnet IP planning

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

1. Continue uncovered-topic questions at SAA-plus difficulty, avoiding simple service-identification questions
2. Drill DR strategies with RPO/RTO scenarios
3. Drill DynamoDB on-demand vs provisioned Auto Scaling
4. Drill IAM + bucket policy + KMS key policy cross-account cases
5. Drill S3 storage-class selection
6. Drill Aurora endpoints and failover
7. Run a 65-question mixed mock under exam timing

## Exam booking gate

Do not book until all are true:

- High-confidence misconceptions are retested successfully
- Weak-area set is at least 80%
- Two full-length mixed mocks are at least 80%
- Multi-response omission errors are rare
- Current official SAA exam guide and in-scope services have been checked

## Next-session instruction

Start by reading this file and `exams/saa/diagnostic-summary.md` if present. Continue uncovered-topic questions at SAA-plus difficulty. After grading, explain SAP-level adjacent knowledge when it provides durable engineering understanding. Use plausible distractors, validate the requested number of correct choices, and grade reasoning strictly.