# SAA Diagnostic Status

## Current position

- Completed through: Q17
- Next question: Q18
- Mode: hard mode from Q15 onward
- Target total: 30 questions

## Latest result

### Q17 - VPC endpoints vs NAT Gateway

- User answer: F
- Correct answer: B, D
- Confidence: 4/5
- Result: Incorrect
- Risk level: High-risk misconception

Why:

- Amazon S3 should use a Gateway VPC Endpoint for private, no-NAT access and no additional endpoint charge.
- AWS Secrets Manager requires an Interface VPC Endpoint; enabling Private DNS allows use of the standard regional service hostname.
- A public NAT Gateway requires an internet gateway for internet-bound traffic, which violates the stated requirement.
- A single NAT Gateway in one Availability Zone also creates an availability dependency and cross-AZ data-path cost risk.
- The question explicitly required two answers; selecting only one should be treated as incorrect even if the selected option were otherwise plausible.

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
