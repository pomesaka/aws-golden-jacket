# SAA Q16R Invalid Again

Question status: invalid.

The prompt asked for 3 answers, but the correct required controls are 4: A, B, C, and D.

User answer: A, B, C, D.

Assessment: conceptually correct. Do not count as wrong.

Required controls:

A. Caller role needs S3 PutObject permission.
B. Target bucket policy must allow the caller role.
C. Caller role needs KMS permissions needed for encryption.
D. Target KMS key policy must allow the caller role to use the key.

Learning point:
Cross account S3 plus SSE KMS requires caller side identity permissions and resource side permissions for both S3 and KMS.

Authoring note:
Do not reuse this question pattern unless the number of correct answers is checked carefully.
