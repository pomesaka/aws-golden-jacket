# SAA Diagnostic Status

## Current position

- Completed through: Q24
- Q19: invalid question; excluded from scoring
- Next question: Q25
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q24 - DynamoDB capacity mode for unpredictable spikes

- User answer: B
- Correct answer: C
- Confidence: 2/5
- Result: Incorrect
- Risk level: Vocabulary and concept gap

Why:

- DynamoDB on-demand capacity mode is designed for workloads with unknown, unpredictable, or highly variable request traffic.
- It removes read/write capacity planning and charges per request, which avoids paying for large idle provisioned capacity during normal low-traffic periods.
- Provisioned capacity with Auto Scaling is more appropriate when traffic is reasonably predictable or changes gradually enough for scaling policies to react.
- A sudden event-driven spike of tens of times within minutes can arrive before target-tracking Auto Scaling has raised provisioned capacity sufficiently.
- DAX is a read cache and does not remove write-capacity requirements or solve unpredictable write spikes.

Reasoning quality:

- Correctly rejected fixed maximum provisioned capacity because it wastes money during normal low traffic.
- Correctly recognized that DAX is not the general solution to capacity variation.
- The missing concept was the DynamoDB on-demand capacity mode and when it is preferred over provisioned Auto Scaling.

## Previous results

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
- VPC Gateway Endpoint vs Interface Endpoint
- NAT Gateway vs VPC Endpoint
- Multi-response requirement reading
- SNS fan-out vs a shared SQS queue
- Lambda with SQS retry and dead-letter queue behavior
- DynamoDB on-demand vs provisioned capacity with Auto Scaling
- DynamoDB capacity behavior during sudden traffic spikes
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
