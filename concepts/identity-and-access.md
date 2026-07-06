# Identity and Access

## Purpose

Understand how AWS decides whether a request is allowed or denied.

## AWS building blocks

- IAM users, groups, roles, and policies
- Resource-based policies
- Permission boundaries
- Service control policies
- IAM Identity Center
- STS temporary credentials
- KMS key policies
- S3 bucket policies
- VPC endpoint policies

## Evaluation mindset

When access fails, identify every policy layer involved:

- identity policy
- resource policy
- organization policy
- permission boundary
- session policy
- service-specific resource policy
- explicit deny

## Exam signals

- cross-account access
- least privilege
- temporary credentials
- centralized account management
- restrict by organization, VPC endpoint, source IP, tag, or principal

## Common traps

- An explicit deny wins.
- IAM permission alone may not be enough when a resource policy or KMS key policy is involved.
- Organization-level guardrails set the maximum available permissions; they do not grant permissions by themselves.
- For workloads on compute services, role-based temporary credentials are usually preferred.

## Related notes

- `services/kms.md`
- future: `services/security/iam.md`
- future: `services/management/organizations.md`
