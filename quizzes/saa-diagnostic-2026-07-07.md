# SAA Diagnostic Quiz - 2026-07-07

## Score

| Question | Result | Confidence | Topic |
|---|---:|---:|---|
| Q1 | Correct | 4/5 | S3 SSE-KMS / KMS key policy |

## Q1: S3 invoice PDFs with company-managed encryption key

### Question summary

A company stores customer-uploaded invoice PDFs in S3. Requirements:

- Encrypt at rest
- Company manages the encryption key
- Application runs on EC2 with an IAM role
- EC2 must read S3 objects
- Security team wants explicit control over key usage permissions

### User answer

Answer: C

Confidence: 4/5

Reason:

- A: SSE-S3 is unknown.
- B: AWS managed key does not satisfy the company-managed key requirement.
- C: Use customer managed KMS key, S3 permission, KMS decrypt permission, and KMS key policy.
- D: Client-side custom implementation with key in EC2 environment variable is not appropriate.

### Evaluation

Result: Correct.

Correct answer: C.

### Why

The requirements point to SSE-KMS with a customer managed KMS key. Reading an SSE-KMS encrypted S3 object requires both access to the S3 object and authorization to use the KMS key for decryption. Because the requirement says the security team wants explicit control over key usage permissions, the KMS key policy must also be considered.

### Trap

S3 permissions and KMS permissions are separate authorization layers. `s3:GetObject` alone is not enough if the object is encrypted with a KMS key that the principal cannot use.

### Follow-up learning

SSE-S3 means server-side encryption with Amazon S3 managed keys. It is simpler operationally, but it does not satisfy requirements where the company/security team must manage and explicitly control key usage.

### Related notes

- `services/kms.md`
- `concepts/identity-and-access.md`
- `exams/saa/weak-points.md`

### Mistake type

No mistake. Minor vocabulary gap: SSE-S3.
