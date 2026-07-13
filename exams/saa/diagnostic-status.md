# SAA Diagnostic Status

## Current position

- Completed through: Q25
- Q19: invalid question; excluded from scoring
- Next question: Q26
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q25 - Organizations SCP regional guardrail

- User answer: A, B
- Correct answer: A, B
- Confidence: 2/5
- Result: Correct
- Risk level: Correct but weak confidence

Why:

- An SCP attached to the development OU centrally limits the maximum permissions available to all current and future member accounts placed in that OU.
- A deny statement using the `aws:RequestedRegion` global condition key can block regional API operations outside approved Regions.
- Global services such as IAM and AWS Organizations must be excluded from the deny statement because their API endpoints do not behave like ordinary regional services.
- SCPs do not grant permissions. IAM identity policies and resource policies must still grant the requested action.
- Replacing AdministratorAccess in every account would create per-account maintenance and would not automatically govern future accounts.
- Detective controls report noncompliance but do not prevent prohibited operations.
- Permissions boundaries are attached to individual IAM users or roles and are not inherited automatically from an Organizations OU.

Reasoning quality:

- Correctly rejected per-account IAM policy replacement because it violates centralized and future-account requirements.
- Correctly distinguished detective controls from preventive enforcement.
- Correctly rejected the claim that an SCP Allow grants permissions.
- Correctly recognized that permissions boundaries would require identity-level attachment rather than OU inheritance.
- Confidence was low because SCP and `aws:RequestedRegion` behavior were not yet familiar; retest this later with policy-evaluation scenarios.

## Previous results

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
