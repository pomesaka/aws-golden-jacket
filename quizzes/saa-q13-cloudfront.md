# SAA Q13 CloudFront

User answer: B.

Correct answer: B.

Result: Correct.

Confidence: 5 of 5.

Key point:
Slow global static content from S3 should be improved with CloudFront.

Route 53 does not cache content.

Global Accelerator is not the main answer for S3 static content caching.

Multi Region ECS and ALB adds cost and targets the API tier, but the problem is static content.
