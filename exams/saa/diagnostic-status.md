# SAA Diagnostic Status

## Current position

- Completed through: Q18
- Next question: Q19
- Mode: hard mode from Q15 onward
- Target total: 30 questions

## Latest result

### Q18 - RDS Multi-AZ vs Read Replica

- User answer: B
- Correct answer: B
- Confidence: 4/5
- Result: Correct
- Risk level: Low

Why:

- RDS Multi-AZ is primarily for high availability and automatic failover.
- A traditional Multi-AZ standby is not used to serve read traffic.
- A Read Replica uses asynchronous replication and can offload read-heavy reporting queries.
- Keeping Multi-AZ while adding a Read Replica preserves failover capability and reduces load on the primary DB.
- The stated tolerance for data being a few seconds old makes asynchronous replication acceptable.

Reasoning quality:

- Correctly rejected disabling Multi-AZ because automatic failover must remain.
- Correctly rejected Redis because arbitrary complex reporting queries are not a good fit for caching every SELECT result.
- Correctly questioned the use of the standby for reads; that distinction should now be made explicit rather than treated as unknown.

## Previous result

### Q17 - VPC endpoints vs NAT Gateway

- User answer: F
- Correct answer: B, D
- Confidence: 4/5
- Result: Incorrect
- Risk level: High-risk misconception

Concept gap:

Do not evaluate each VPC endpoint option as a complete solution in isolation when the question asks for multiple responses. Combine the service-specific endpoint types needed to satisfy the full set of requirements.

## Operating rules

Use `diagnostic-quiz-plan.md` as the baseline distribution and `hard-mode.md` for difficulty from Q15 onward.

Questions should:

- avoid hints in the prompt
- use plausible distractors
- ask for the best answer, not merely a possible answer
- mix cost, operations, availability, security, and change size
- include multiple-response questions when useful
- grade reasoning strictly

## Known weak areas to retest

- IAM policy vs resource policy vs KMS key policy
- Cross-account S3 access with SSE-KMS
- VPC Gateway Endpoint vs Interface Endpoint
- NAT Gateway vs VPC Endpoint
- Multi-response requirement reading
- Route 53 routing policies
- CloudFront vs Global Accelerator
- S3 vs EFS vs EBS default service selection
- RDS/Aurora replication, failover, and read scaling

## Completion criteria before booking SAA

Do not choose an exam date until the following are true:

- Q30 is completed.
- Confidence-adjusted score is calculated.
- All wrong or uncertain answers have a service note or comparison note.
- High-risk misconceptions are retested.
- Current AWS SAA exam guide is checked from the official AWS source.
