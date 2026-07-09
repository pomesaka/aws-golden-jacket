# SAA Targeted Remaining Quiz Q11-Q30

Purpose: finish the 30-question diagnostic while reinforcing current weak areas.

Current score after Q10: 9/10.

Main weak areas:

- Route 53 vs Global Accelerator vs CloudFront
- Route 53 routing policies
- KMS authorization details
- AWS Organizations and SCP
- Hybrid networking
- Transit Gateway, VPC Peering, Direct Connect, Site-to-Site VPN
- Storage boundary details: EBS, EFS, FSx, S3

Answer format:

```text
Answer:
Confidence:
Reason:
```

Grading rule:

- Correct answer with wrong reasoning is a weak answer.
- Wrong answer with confidence 4 or 5 is high risk.
- Unknown service name is a vocabulary gap.

## Question plan

### Q11 Route 53 failover routing
Test active-passive DNS failover with health checks.

### Q12 Global Accelerator
Test static IP, TCP/UDP, AWS global network, multi-Region ALB endpoints.

### Q13 CloudFront vs Global Accelerator
Test cacheable HTTP content vs path optimization.

### Q14 Route 53 weighted vs latency vs geolocation
Test routing policy selection.

### Q15 KMS key policy and IAM policy
Test why IAM allow is not always enough for KMS key use.

### Q16 S3 SSE-S3 vs SSE-KMS vs client-side encryption
Test encryption requirement wording.

### Q17 SCP vs IAM policy vs permission boundary
Test account-level guardrail versus principal-level control.

### Q18 CloudTrail vs Config vs GuardDuty
Test audit, config compliance, and threat detection boundaries.

### Q19 Direct Connect plus VPN backup
Test hybrid connectivity resilience.

### Q20 Transit Gateway vs VPC Peering
Test many VPCs and on-prem hub-and-spoke networking.

### Q21 PrivateLink vs VPC Peering
Test exposing a service privately across VPCs without full network connectivity.

### Q22 NAT Gateway cost and endpoints
Test Gateway Endpoint, Interface Endpoint, and NAT cost tradeoff.

### Q23 ALB vs NLB vs Gateway Load Balancer
Test L7, L4, and network appliance use cases.

### Q24 Aurora Global Database vs cross-Region read replica
Test global reads and DR requirements.

### Q25 RDS Proxy
Test connection pooling for Lambda or bursty serverless access to RDS.

### Q26 DynamoDB vs RDS
Test key-value scale and relational query requirements.

### Q27 SQS vs SNS vs EventBridge
Test decoupling, fanout, and event routing.

### Q28 Step Functions vs SQS worker pattern
Test workflow orchestration versus simple queue buffering.

### Q29 FSx for Windows vs EFS vs FSx for Lustre
Test managed file system selection.

### Q30 Cost optimization mixed scenario
Test Savings Plans, Compute Optimizer, S3 lifecycle, and NAT/data transfer traps.

## Booking guidance after Q30

Book SAA if:

- total score is 75 percent or higher
- Route 53 / Global Accelerator questions improve after Q8
- no repeated high-confidence wrong answers in IAM, KMS, networking, or HA

If score stays above 80 percent and weak-area misses are corrected quickly, booking within 1 to 2 weeks is reasonable.
