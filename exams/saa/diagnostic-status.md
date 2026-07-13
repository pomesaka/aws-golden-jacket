# SAA Diagnostic Status

## Current position

- Completed through: Q21
- Q19: invalid question; excluded from scoring
- Next question: Q22
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions

## Latest result

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
- Route 53 latency-based routing can choose a low-latency region, but it does not itself provide fixed IP addresses and DNS caching can delay failover.
- CloudFront is primarily an HTTP/HTTPS content delivery service and does not fit arbitrary TCP and UDP application traffic.

Reasoning quality:

- Correctly identified fixed IP plus global routing optimization as the decisive combination.
- Correctly rejected Route 53 because an additional fixed-IP mechanism would be needed and DNS caching remains relevant.
- Correctly rejected CloudFront for this TCP/UDP workload.
- The statement that weighted routing is not path optimization was also directionally correct.

## Previous result

### Q20 - Disaster recovery strategy

- User answer: B
- Correct answer: D
- Confidence: 2/5
- Result: Incorrect
- Risk level: Concept gap

Why:

- Multi-site provides the fastest recovery but has the highest steady-state cost.
- Warm standby keeps a scaled-down functional environment running continuously, so it costs more than pilot light.
- Backup and restore has the lowest steady-state cost but usually has a longer RTO.
- Pilot light keeps critical data and minimal core resources ready, then scales the stateless application tier after a disaster.

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
