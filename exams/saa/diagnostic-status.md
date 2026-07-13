# SAA Diagnostic Status

## Current position

- Completed through: Q26
- Q19: invalid question; excluded from scoring
- Next question: Q27
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q26 - S3 lifecycle and archive retrieval time

- User answer: C
- Correct answer: C
- Confidence: 1/5
- Result: Correct
- Risk level: Correct by limited familiarity; storage-class vocabulary needs reinforcement

Why:

- The first 30 days require frequent access, so objects can remain in S3 Standard.
- S3 Lifecycle can automatically transition the objects after 30 days and expire them after seven years.
- S3 Glacier Deep Archive is designed for long-lived archive data accessed less than once a year and has a 180-day minimum storage duration.
- Standard retrieval from S3 Glacier Deep Archive is typically completed within 12 hours, which satisfies the stated requirement.
- S3 Glacier Flexible Retrieval also satisfies the restore-time requirement, but it has a higher storage cost than Deep Archive and is unnecessary when 12-hour restoration is acceptable.
- S3 Standard-IA and S3 One Zone-IA provide millisecond access, which is more performance and cost than the requirement needs.
- S3 One Zone-IA is not appropriate as the primary compliance copy because it is stored in a single Availability Zone.

Reasoning quality:

- The selected answer was correct, but the reasoning depended on prior exposure to Deep Archive rather than a comparison of retrieval time, durability model, and cost.
- Retest Glacier Instant Retrieval, Flexible Retrieval, Deep Archive, Standard-IA, and One Zone-IA selection later.

## Previous results

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
