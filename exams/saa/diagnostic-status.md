# SAA Diagnostic Status

## Current position

- Completed through: Q27
- Q19: invalid question; excluded from scoring
- Next question: Q28
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q27 - Aurora readers, endpoints, and failover

- User answer: A
- Correct answer: A
- Confidence: 2/5
- Result: Correct
- Risk level: Correct but weak confidence

Why:

- Aurora supports multiple reader instances for read scaling.
- The reader endpoint balances new read-only connections across available Aurora Replicas, so the application does not need to manage each instance endpoint.
- If the writer fails and one Aurora Replica is promoted, the cluster endpoint continues to represent the current writer.
- Having Aurora Replicas in multiple Availability Zones improves failover readiness and is faster than creating a new writer when no replica exists.
- The reader endpoint is for distributing read connections; it is not the endpoint used for writes.
- Aurora Global Database is for cross-Region reads and disaster recovery and is unnecessary for this single-Region requirement.
- Sending all reads to the writer through RDS Proxy does not satisfy the read-scaling requirement.

Reasoning quality:

- Correctly selected the reader endpoint to avoid per-instance endpoint management.
- The missing concept was that writer failover is handled separately through Aurora replica promotion and the cluster endpoint.
- Retest cluster endpoint vs reader endpoint vs instance endpoint and failover behavior later.

## Previous results

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
