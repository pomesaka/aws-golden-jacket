# SAA Diagnostic Status

## Current position

- Completed through: Q30
- Q19: invalid question; excluded from scoring
- Next step: calculate score, confidence-adjusted score, and retest priorities
- Mode: hard mode from Q15 onward
- Target total: 30 valid scored questions reached

## Latest result

### Q30 - CloudFront OAC and private S3 origin

- User answer: A, B
- Correct answer: A, B
- Confidence: 4/5
- Result: Correct
- Risk level: Low; one infrastructure-model detail needed clarification

Why:

- Origin Access Control (OAC) is the recommended method for authenticated CloudFront requests to a regular S3 bucket origin.
- With the recommended `always` signing behavior, CloudFront signs origin requests with SigV4.
- The S3 bucket policy should allow the CloudFront service principal and restrict it with `AWS:SourceArn` to the intended distribution ARN.
- This lets the bucket remain private and prevents direct unauthenticated S3 URL access.
- An S3 website endpoint is a custom origin and cannot use OAC or OAI.
- Public-read access violates the private-origin requirement.
- CloudFront distributions do not have security groups that can be referenced by an S3 bucket policy. Security groups apply to network interfaces/resources inside a VPC, while CloudFront is a global edge service and S3 access is authorized through IAM-style resource policies and OAC signing.

Reasoning quality:

- Correctly selected OAC and the distribution-restricted bucket policy.
- Correctly rejected public S3 and website-endpoint designs.
- The only uncertainty was why a CloudFront security group cannot be used; this is now clarified.

## Previous results

### Q29 - VPC endpoints for S3 and Secrets Manager

- User answer: B
- Correct answer: B
- Confidence: 5/5
- Result: Correct
- Risk level: Low

### Q28 - Lambda, RDS Proxy, and connection storms

- User answer: C
- Correct answer: C
- Confidence: 5/5
- Result: Correct
- Risk level: Low

### Q27 - Aurora readers, endpoints, and failover

- User answer: A
- Correct answer: A
- Confidence: 2/5
- Result: Correct
- Risk level: Correct but weak confidence

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
- RDS Proxy connection pooling, multiplexing, and session pinning
- Aurora Global Database vs single-Region Aurora and RDS Proxy
- CloudFront OAC, OAI, S3 bucket policies, and website endpoints
- CloudFront as a global service vs VPC security-group-controlled resources
- DR strategy selection: backup and restore vs pilot light vs warm standby vs multi-site
- RPO vs RTO interpretation
- Route 53 routing policies
- CloudFront vs Global Accelerator
- S3 vs EFS vs EBS default service selection
- RDS/Aurora replication, failover, and read scaling

## Completion criteria before booking SAA

- 30 valid scored questions are completed. Done.
- Confidence-adjusted score is calculated. Pending.
- All wrong or uncertain answers have a service note or comparison note. Partially complete.
- High-risk misconceptions are retested. Pending.
- Current AWS SAA exam guide is checked from the official AWS source. Pending.
