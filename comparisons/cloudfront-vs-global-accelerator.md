# CloudFront vs Global Accelerator

## CloudFront

CloudFront is primarily a content delivery network.

Use when:

- Static assets or cacheable content matter.
- You need edge caching.
- You need signed URLs or signed cookies.
- You need CDN behavior in front of S3, ALB, API Gateway, or custom origins.

Exam signals:

- CDN
- cache
- static website
- images/videos/assets
- edge locations
- signed URL

## Global Accelerator

Global Accelerator is primarily a global traffic routing and network path optimization service.

Use when:

- You need static anycast IP addresses.
- You need traffic to enter the AWS global network near users.
- You need fast endpoint failover.
- Your endpoints are ALB, NLB, EC2, or Elastic IPs.

Exam signals:

- global users
- low latency network path
- TCP/UDP
- static IP
- regional endpoint failover
- do not rely on DNS cache timing

## Fast rule

- Cache content at edge -> CloudFront.
- Optimize global network path and failover to regional endpoints -> Global Accelerator.

## Related notes

- `services/global-accelerator.md`
