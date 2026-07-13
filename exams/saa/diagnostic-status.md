# SAA Diagnostic Status

## Current position

- Completed through: Q22
- Q19: invalid question; excluded from scoring
- Next question: Q23
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

### Q22 - Shared POSIX file system across multiple AZs

- User answer: B
- Correct answer: B
- Confidence: 4/5
- Result: Correct
- Risk level: Low

Why:

- Amazon EFS Regional provides a managed, elastic, POSIX-compliant shared file system for Linux workloads.
- Multiple EC2 instances can mount and concurrently read and write the same file system.
- Regional EFS stores data across multiple Availability Zones and fits Auto Scaling groups spanning AZs.
- Capacity scales automatically, reducing provisioning and operational overhead.
- EBS Multi-Attach is limited to specific volume types and same-AZ attachment patterns and is not the default managed multi-AZ shared file-system choice.
- Amazon S3 is object storage, not a general POSIX file system.
- FSx for Windows File Server targets Windows/SMB workloads rather than Linux POSIX requirements.

Reasoning quality:

- Correctly selected EFS based on shared access, POSIX compatibility, elasticity, and multi-AZ availability.
- Correctly rejected Windows File Server and S3 for the stated interface requirements.
- The EBS rejection was directionally correct, but should be stated more precisely: EBS Multi-Attach is not a cross-AZ shared file system and requires application-level clustered file-system coordination.

## Previous result

### Q21 - Route 53 vs CloudFront vs Global Accelerator

- User answer: C
- Correct answer: C
- Confidence: 5/5
- Result: Correct
- Risk level: Low

Why:

- AWS Global Accelerator provides static anycast IP addresses.
- It supports TCP and UDP listeners.
- It routes users onto the AWS global network toward healthy regional endpoints.
- Health checks and endpoint failover are not dependent on waiting for DNS caches to expire.

## Earlier result

### Q20 - Disaster recovery strategy

- User answer: B
- Correct answer: D
- Confidence: 2/5
- Result: Incorrect
- Risk level: Concept gap

Concept gap:

- Warm standby costs more than pilot light because it keeps a scaled-down functional environment running continuously.
- Snapshot frequency mainly affects RPO; restore and provisioning time dominate RTO.

## Invalid question

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
