# SAA Diagnostic Status

## Current position

- Completed through: Q18
- Q19: invalid question; excluded from scoring
- Next question: Q20
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q19 - Cross-account S3 + SSE-KMS

- User answer: no final selection; reasoning narrowed to A and B and questioned whether the KMS key policy was also required
- Intended prompt: choose two
- Actual required controls: A, B, and C
- Result: Invalid question; excluded from scoring
- Risk level: None assigned

Why the question was invalid:

- The IAM role in account B needs identity permissions for `s3:GetObject` and `kms:Decrypt`.
- The S3 bucket policy in account A must allow the cross-account principal to read the object.
- The KMS key policy in account A must allow the role or account B to use the KMS key; the role's IAM policy alone cannot make an external KMS key usable.
- Therefore, the correct design requires three authorization layers, but the prompt required exactly two selections.

Reasoning quality:

- Correctly rejected D and E.
- Correctly identified that a KMS key-policy change in account A was still required.
- The statement that C removes the need for IAM-role permissions was incorrect: cross-account KMS use requires both the key-side permission and identity-side permission.

## Previous valid result

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

## Earlier result

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
- be checked so the declared number of selections matches the actual correct controls

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

- 30 valid scored questions are completed.
- Confidence-adjusted score is calculated.
- All wrong or uncertain answers have a service note or comparison note.
- High-risk misconceptions are retested.
- Current AWS SAA exam guide is checked from the official AWS source.
