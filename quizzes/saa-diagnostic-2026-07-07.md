# SAA Diagnostic Quiz - 2026-07-07

## Score

| Question | Result | Confidence | Topic |
|---|---:|---:|---|
| Q1 | Correct | 4/5 | S3 SSE-KMS / KMS key policy |
| Q2 | Correct | 5/5 | Session affinity vs external session store |

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

## Q2: EC2 Auto Scaling with in-memory sessions

### Question summary

A web application runs on an EC2 Auto Scaling group. The app stores session data in each EC2 instance's memory. When instances scale in/out, users are logged out or sessions are lost.

Requirements:

- Keep Auto Scaling
- Improve availability
- Minimize application changes
- Minimize operational overhead

### User answer

Answer: A

Confidence: 5/5

Reason:

- Sticky sessions are the direct match for this use case.
- B/C/D are probably implementable, but require application changes.

### Evaluation

Result: Correct for the stated requirement emphasis.

Correct answer: A.

### Why

Because the question prioritizes minimal application changes and low operational overhead, enabling ALB sticky sessions is the best fit among the options. It keeps requests from the same client directed to the same target for a configured duration and avoids immediately rewriting the application to externalize session state.

### Important caveat

Sticky sessions are not the best long-term stateless architecture. If the question emphasized best scalability, stateless design, or resilience to instance termination, an external session store such as ElastiCache for Redis would become stronger.

### Trap

Externalizing session state is architecturally cleaner, but it requires application changes. The requirement "application changes are minimal" changes the answer.

### Related notes

- `concepts/stateless-and-scaling.md`
- future: `comparisons/sticky-session-vs-external-session-store.md`

### Mistake type

No mistake. This was a high-confidence correct answer, with a useful caveat about long-term architecture.
