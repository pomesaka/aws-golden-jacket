# SAA Q12 Global Accelerator

User answer: B.

Correct answer: B.

Result: Correct.

Confidence: 5 of 5.

Key point:
Static IP plus AWS global network plus healthy regional ALB endpoints equals Global Accelerator.

Route 53 gives DNS answers only.

CloudFront is for HTTP or HTTPS content delivery and caching, not generic TCP caching.

Weighted routing does not optimize the network path.
