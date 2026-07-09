# Weak Point: Cross Account S3 and KMS

## Status

Needs practice.

## Trigger

Q16 revealed limited practical experience with cross account S3 access and KMS authorization.

## Key memory

Cross account S3 access needs both sides:

- caller side IAM permissions
- resource side bucket policy

SSE KMS also needs both sides:

- caller side KMS permissions
- KMS key policy allowing the caller to use the key

## Exam hook

Same account access can often be solved with IAM alone.

Cross account access usually needs IAM plus resource policy.

KMS key use needs IAM plus key policy.

## Practice focus

More hard mode questions should include:

- cross account bucket access
- SSE KMS authorization
- key policy versus IAM policy
- bucket policy conditions
- confused deputy prevention
