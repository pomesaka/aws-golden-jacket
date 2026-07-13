# SAA Diagnostic Status

## Current position

- Completed through: Q28
- Q19: invalid question; excluded from scoring
- Next question: Q29
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q28 - Lambda, RDS Proxy, and connection storms

- User answer: C
- Correct answer: C
- Confidence: 5/5
- Result: Correct
- Risk level: Low

Why:

- Rapid Lambda scale-out can create many concurrent database connections and exhaust the Aurora connection limit.
- RDS Proxy pools and reuses database connections, reducing the number of physical connections opened against Aurora.
- RDS Proxy is designed for highly concurrent and serverless applications that can produce sudden connection spikes.
- AWS Secrets Manager or IAM database authentication avoids embedding database credentials in application code.
- Increasing Lambda memory or creating larger per-runtime pools does not coordinate connections across separate Lambda execution environments.
- ElastiCache is a data cache and is not a transparent database connection proxy.
- Aurora Global Database addresses cross-Region replication and disaster recovery, not connection pooling.

Reasoning quality:

- Correctly mapped the Lambda connection-storm scenario to RDS Proxy.
- Correctly recognized that the question directly tested the concept discussed immediately beforehand.
- Confidence was appropriately high.

## Previous results

### Q27 - Aurora readers, endpoints, and failover

- User answer: A
- Correct answer: A
- Confidence: 2/5
- Result: Correct
- Risk level: Correct but weak confidence

### Q26 - S3 lifecycle and archive retrieval time

- User answer: C
- Correct answer: C
- Confidence: 1/5
- Result: Correct
- Risk level: Correct by limited familiarity; storage-class vocabulary needs reinforcement

### Q25 - Organizations SCP regional guardrail

- User answer: A, B
- Correct answer: A, B
- Confidence: 2/5
- Result: Correct
- Risk level: Correct but weak confidence

### Q24 - DynamoDB capacity mode for unpredictable spikes

- User answer: B
- Correct answer: C
- Confidence: 2/5
- Result: Incorrect
- Risk level: Vocabulary and concept gap

### Q23 - SNS fan-out, SQS, Lambda, and DLQ

- User answer: C
- Correct answer: B, C
- Confidence: 5/5
- Result: Incorrect
- Risk level: High-risk misconception

### Q22 - Shared POSIX file system across multiple AZs

- User answer: B
- Correct answer: B
- Confidence: 4/5
- Result: Correct
- Risk level: Low

### Q21 - Route 53 vs CloudFront vs Global Accelerator

- User answer: C
- Correct answer: C
- Confidence: 5/5
- Result: Correct
- Risk level: Low

### Q20 - Disaster recovery strategy

- User answer: B
- Correct answer: D
- Confidence: 2/5
- Result: Incorrect
- Risk level: Concept gap

### Q19 - Cross-account S3 + SSE-KMS

- Result: Invalid question; excluded from scoring
- Actual required controls: identity permissions, S3 bucket policy, and KMS key policy

## Operating rules

Use `diagnostic-quiz-plan.md` as the baseline distribution and `hard-mode.md` for difficulty from Q15 onward.

Questions should:

- avoid hints in the prompt
- use plausible distractors
- ask for the best answer, not merely a possible answer
- mix cost, operations, availability, security, and change size
- include multiple-response questions when useful
- grade reasoning strictly
- be checked so the declared number of selections matches the actual correct controls

## Known weak areas to retest

- IAM policy vs resource policy vs KMS key policy
- Cross-account S3 access with SSE-KMS
- Organizations SCP vs IAM policy vs permissions boundary
- SCP regional guardrails with `aws:RequestedRegion` and global-service exclusions
- VPC Gateway Endpoint vs Interface Endpoint
- NAT Gateway vs VPC Endpoint
- Multi-response requirement reading
- SNS fan-out vs a shared SQS queue
- Lambda with SQS retry and dead-letter queue behavior
- DynamoDB on-demand vs provisioned capacity with Auto Scaling
- DynamoDB capacity behavior during sudden traffic spikes
- S3 storage-class selection: Standard-IA, One Zone-IA, Glacier Instant Retrieval, Flexible Retrieval, and Deep Archive
- S3 archive restore times and minimum storage durations
- Aurora cluster endpoint vs reader endpoint vs instance endpoint
- Aurora replica promotion and writer failover
- RDS Proxy connection pooling, multiplexing, and session pinning
- Aurora Global Database vs single-Region Aurora and RDS Proxy
- DR strategy selection: backup and restore vs pilot light vs warm standby vs multi-site
- RPO vs RTO interpretation
- Route 53 routing policies
- CloudFront vs Global Accelerator
- S3 vs EFS vs EBS default service selection
- RDS/Aurora replication, failover, and read scaling

## Completion criteria before booking SAA

Do not choose an exam date until the following are true:

- 30 valid scored questions are completed.
- Confidence-adjusted score is calculated.
- All wrong or uncertain answers have a service note or comparison note.
- High-risk misconceptions are retested.
- Current AWS SAA exam guide is checked from the official AWS source.
