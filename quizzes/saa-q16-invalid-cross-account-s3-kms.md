# SAA Q16 Invalid Question

Question status: invalid.

Reason:
The question asked for 2 answers, but the scenario actually requires 3 control points.

Required controls:

1. S3 bucket policy in account B allows the application role in account A to put objects.
2. KMS key policy in account B allows the application role in account A to use the key.
3. IAM policy on the application role in account A allows S3 PutObject and the required KMS encryption actions.

User answer: C and E.

Assessment:
Do not count this as incorrect. The user selected two important required controls, but the prompt was flawed.

Corrected answer if the prompt said choose 3: A, C, and E.

Learning point:
Cross account S3 with SSE KMS needs both S3 authorization and KMS authorization. For cross account access, resource side policies and caller side identity permissions both matter.
