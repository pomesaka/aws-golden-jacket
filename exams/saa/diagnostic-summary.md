# SAA Diagnostic Summary

## Scope and scoring

- Question numbers completed: Q1-Q30
- Invalid questions excluded from scoring: Q16 and Q19
- Valid scored questions: 28
- Correct: 23
- Incorrect: 5
- Raw score: 82.1%

## Confidence-adjusted score

Learning-only adjustment:

- Correct with confidence 3-5: 1.0 point
- Correct with confidence 1-2: 0.5 point
- Incorrect: 0 points

Result:

- Stable correct: 20
- Low-confidence correct: 3
- Adjusted points: 21.5 / 28
- Confidence-adjusted score: 76.8%

This is not AWS's official scoring method. It is a conservative readiness metric.

## Incorrect answers

| Question | Topic | Confidence | Risk |
|---|---|---:|---|
| Q8 | Route 53 latency routing vs Global Accelerator | 4/5 | High-confidence misconception |
| Q17 | VPC endpoint / NAT design | 4/5 | High-confidence misconception |
| Q20 | DR strategy selection | 2/5 | Concept gap |
| Q23 | SNS fan-out, SQS, Lambda, DLQ | 5/5 | High-confidence misconception |
| Q24 | DynamoDB capacity mode | 2/5 | Vocabulary and concept gap |

## Correct but uncertain

| Question | Topic | Confidence |
|---|---|---:|
| Q25 | Organizations SCP regional guardrail | 2/5 |
| Q26 | S3 storage classes and archive restore time | 1/5 |
| Q27 | Aurora reader endpoint and writer failover | 2/5 |

## Stronger areas observed

- S3 SSE-KMS basics and separation of S3 and KMS authorization
- ALB sticky sessions vs external session storage under minimal-change requirements
- S3 Gateway VPC Endpoint selection
- ElastiCache vs RDS Read Replica
- CloudFront for S3 content delivery and private origins
- RDS Multi-AZ vs Read Replica
- Route 53 failover and weighted routing
- Global Accelerator core use case
- EFS shared POSIX storage
- RDS Proxy for Lambda connection storms
- S3 Gateway Endpoint plus Secrets Manager Interface Endpoint
- CloudFront OAC with an S3 bucket policy

## Highest-priority weak concepts

1. SNS fan-out, per-consumer SQS queues, Lambda retry and DLQ behavior
2. Route 53 routing policies vs Global Accelerator
3. Gateway Endpoint vs Interface Endpoint vs NAT Gateway
4. DR strategy selection from RPO, RTO, cost, and standby capacity
5. DynamoDB on-demand vs provisioned capacity with Auto Scaling
6. IAM identity policy vs resource policy vs KMS key policy vs SCP
7. S3 storage class retrieval time and minimum storage duration
8. Aurora cluster endpoint vs reader endpoint vs instance endpoint

## Readiness assessment

The raw score is above 80%, but this diagnostic does not fully cover the current SAA exam scope. Three high-confidence misconceptions remain, and several important domains were lightly tested or not tested.

Do not book the exam based on this diagnostic alone. Recommended gate before booking:

- Complete targeted retests for all five incorrect answers and the three low-confidence correct answers.
- Complete a gap-coverage set for under-tested services.
- Score at least 80% on two full-length, exam-style 65-question practice exams.
- Reduce high-confidence incorrect answers to zero or near zero.

## Next study actions

1. Retest SNS + SQS + Lambda fan-out with multiple-response questions.
2. Retest Route 53 latency, weighted, failover, geolocation, geoproximity, and multivalue routing.
3. Retest Gateway and Interface VPC Endpoints, NAT Gateway, PrivateLink, and endpoint policies.
4. Drill backup and restore, pilot light, warm standby, and multi-site DR.
5. Drill DynamoDB on-demand, provisioned, Auto Scaling, GSI, DAX, Streams, and Global Tables.
6. Review cross-account S3 with SSE-KMS using identity, bucket, and key policies together.
7. Memorize S3 storage-class use cases, restore times, and minimum durations.
8. Retest Aurora endpoints, replica promotion, Global Database, and RDS Proxy.
9. Cover under-tested compute, containers, hybrid networking, observability, and cost optimization.
10. Take a full-length 65-question practice exam and record confidence for every answer.
