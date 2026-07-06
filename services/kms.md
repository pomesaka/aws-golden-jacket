# AWS KMS

## What problem does it solve?

Managed key creation, storage, policy control, encryption, and decryption for AWS services and applications.

## Key exam idea

Access to encrypted data often requires two layers:

1. Permission to access the resource, such as `s3:GetObject`.
2. Permission to use the KMS key, such as `kms:Decrypt`.

If S3 access is allowed but KMS denies decrypt, the request fails.

## IAM policy vs key policy

IAM policy:

- Grants permissions to a principal.
- Useful, but not always sufficient alone for KMS.

KMS key policy:

- Resource policy attached to the KMS key.
- Defines who can administer or use the key.
- For customer-managed keys, always check the key policy when debugging access.

## Common pattern: S3 + SSE-KMS

For an EC2 role to read SSE-KMS encrypted objects from S3:

- The IAM role needs S3 read permissions.
- The IAM role needs KMS decrypt permissions.
- The KMS key policy must allow the principal or allow IAM policies to grant access.
- Bucket policy may also restrict access to a VPC endpoint, organization, account, or role.

## Exam traps

- "S3 access is allowed" does not mean "KMS decrypt is allowed".
- AWS managed keys and customer-managed keys have different control surfaces.
- Cross-account KMS usage requires careful key policy and IAM policy alignment.

## Personal note

Initial diagnostic gap: KMS key policy behavior was unclear. This needs repeated practice with S3, CloudTrail, EBS, RDS, Lambda environment variables, and cross-account access scenarios.
