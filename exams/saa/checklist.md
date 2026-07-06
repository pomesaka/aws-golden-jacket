# SAA Readiness Checklist

## Before first diagnostic quiz

- [x] Create SAA workspace
- [x] Summarize official exam facts
- [x] Capture domain weights
- [x] Capture domain/task breakdown
- [x] Create in-scope service priority map
- [ ] Take 30-question diagnostic quiz

## Diagnostic quiz rules

For every question, record:

- selected answer
- confidence: 1-5
- reason
- correct answer
- wrong-answer trap
- related service notes
- official source to read

## Minimum diagnostic coverage

The first 30-question diagnostic should cover:

| Area | Target questions |
|---|---:|
| Security / IAM / KMS | 6 |
| Resilient architecture / DR / HA | 6 |
| Storage selection | 4 |
| Database selection / replication | 4 |
| Networking / edge / private connectivity | 5 |
| Compute / containers / serverless | 3 |
| Cost optimization | 2 |

## Booking threshold

Book SAA when:

- 30-question diagnostic score is at least 75%
- no critical weak area has confidence <= 2 twice in a row
- IAM/KMS and network questions are at least 70%
- storage/database selection feels automatic

## Critical weak areas to clear

- [ ] IAM policy vs resource policy vs KMS key policy
- [ ] SCP behavior
- [ ] S3 vs EFS vs EBS vs FSx
- [ ] Multi-AZ vs Read Replica vs Aurora Global Database
- [ ] CloudFront vs Global Accelerator vs Route 53
- [ ] Gateway VPC Endpoint vs Interface VPC Endpoint
- [ ] NAT gateway placement and cost tradeoffs
- [ ] ALB vs NLB vs Gateway Load Balancer
- [ ] SQS vs SNS vs EventBridge vs Step Functions
- [ ] Lambda vs ECS/Fargate vs EC2
