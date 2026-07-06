# SAA Weak Points

Initial weak points are based on the 2026-07-06 diagnostic conversation.

## High priority

### KMS and authorization model

Status: weak

Why:

- KMS key policy behavior was unclear.
- Need to understand how IAM policy, resource policy, SCP, and KMS key policy interact.

Related:

- `services/kms.md`
- `concepts/identity-and-access.md`
- Issue #3

### Global Accelerator

Status: vocabulary gap

Why:

- Service was unknown during quiz.
- Correct reasoning eliminated some wrong choices, but the final answer required knowing the service.

Related:

- `services/global-accelerator.md`
- `comparisons/cloudfront-vs-global-accelerator.md`
- Issue #4

### VPC endpoints

Status: partial

Why:

- Gateway Endpoint cost/use case was understood.
- Need sharper distinction between Gateway Endpoint, Interface Endpoint, PrivateLink, NAT Gateway, and endpoint policies.

Related:

- `comparisons/vpc-gateway-endpoint-vs-interface-endpoint.md`

## Medium priority

### Storage selection

Status: improving

Why:

- EFS was chosen for a case where S3 was the stronger default.
- Need automatic recognition of object/file/block storage exam wording.

Related:

- `services/s3-vs-efs.md`
- `concepts/stateless-and-scaling.md`

### Route 53 routing policies

Status: not yet tested deeply

Why:

- Latency routing with one region was correctly dismissed.
- Need full coverage of failover, weighted, latency, geolocation, geoproximity, and multivalue answer routing.

### Cost optimization

Status: not yet tested deeply

Why:

- Need deliberate practice on NAT Gateway placement, VPC endpoints, Spot/RI/Savings Plans, lifecycle policies, and data transfer costs.

## Lower priority for first diagnostic

### ECS / Fargate basics

Status: comparatively strong

Why:

- Direct hands-on experience exists.
- Still needs exam-specific edge cases, but not the first bottleneck.

### CloudFront basics

Status: comparatively strong

Why:

- Direct hands-on experience with React delivery exists.
- Need comparison with Global Accelerator and signed URL/cookie behavior.
