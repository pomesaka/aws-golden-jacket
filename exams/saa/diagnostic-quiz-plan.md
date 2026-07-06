# SAA Diagnostic Quiz Plan

Goal: prepare a 30-question diagnostic that measures real SAA readiness without giving hints.

## Format

Each question should be multiple choice or multiple response.

User answer format:

```text
Answer: A
Confidence: 4/5
Reason: ...
```

Assistant evaluation format:

```text
Result: Correct / Incorrect
Correct answer: ...
Why: ...
Trap: ...
Related notes: ...
Official docs to read: ...
```

## Question distribution

### Security / IAM / KMS - 6 questions

Topics:

- IAM role vs access key
- Resource policy vs identity policy
- S3 bucket policy
- KMS key policy
- SCP guardrails
- Secrets Manager / ACM / WAF / Shield selection

### Resilience / HA / DR - 6 questions

Topics:

- Multi-AZ vs Read Replica
- RTO/RPO strategy selection
- Route 53 failover
- Backup and restore vs pilot light vs warm standby
- ALB + Auto Scaling across AZs
- Legacy app reliability with minimal change

### Storage - 4 questions

Topics:

- S3 vs EFS vs EBS vs FSx
- S3 lifecycle and Glacier
- Backup strategies
- Storage Gateway / DataSync use cases

### Database - 4 questions

Topics:

- RDS vs Aurora vs DynamoDB
- Read replicas and caching
- RDS Proxy
- DynamoDB capacity/access pattern design

### Networking / edge / private connectivity - 5 questions

Topics:

- CloudFront vs Global Accelerator
- Route 53 routing policies
- Gateway Endpoint vs Interface Endpoint
- NAT Gateway vs VPC Endpoint
- Direct Connect vs VPN vs Transit Gateway

### Compute / containers / serverless - 3 questions

Topics:

- EC2 Auto Scaling
- Lambda vs Fargate vs EC2
- ECS/EKS high-level service selection

### Cost optimization - 2 questions

Topics:

- Savings Plans / Reserved Instances / Spot
- Network/storage cost tradeoffs

## Anti-hint rule

Do not include follow-up hints in the question prompt. Ask extra questions only after the user answers.

## Scoring

- Correct and confident: full credit
- Correct but confidence <= 2: mark as weak
- Wrong but reasoning close: mark as concept gap
- Wrong and confident: mark as high-risk misconception
- Unknown: mark as vocabulary gap

## Output after 30 questions

Produce:

- score
- confidence-adjusted score
- top 5 weak services
- top 5 weak concepts
- recommended exam date range
- next 10 study actions
