# SAA Diagnostic Status

## Current position

- Completed through: Q23
- Q19: invalid question; excluded from scoring
- Next question: Q24
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q23 - SNS fan-out, SQS, Lambda, and DLQ

- User answer: C
- Correct answer: B, C
- Confidence: 5/5
- Result: Incorrect
- Risk level: High-risk misconception

Why:

- SNS publishes one order event to multiple independent subscribers.
- A separate SQS queue for each downstream process lets inventory, billing, and shipping scale and fail independently.
- SQS retains messages while a Lambda consumer is temporarily unavailable.
- Lambda event source mappings consume from each queue, while an SQS redrive policy moves repeatedly failing messages to a dead-letter queue.
- A single shared SQS queue uses competing consumers; each message is normally processed by one consumer rather than broadcast to all three.
- Adding another SNS subscription and SQS queue enables a new downstream process without changing the order-ingestion Lambda.

Reasoning quality:

- Correctly selected C for queue consumption and failed-message isolation.
- Correctly rejected a shared SQS queue because it does not broadcast every order to all processors.
- Incorrectly rejected B: the SNS-to-SQS layer is what provides fan-out and buffering when a consumer is unavailable.
- The prompt explicitly required two selections; answering only C is independently incorrect.
- A is wrong mainly because synchronous sequential invocation creates coupling and failure propagation, not primarily because of cost.

## Previous results

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
