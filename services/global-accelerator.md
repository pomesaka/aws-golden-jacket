# AWS Global Accelerator

## What problem does it solve?

Improves availability and performance for applications by routing user traffic through the AWS global network to healthy regional endpoints.

## Use when

- Users are globally distributed.
- Application traffic is TCP/UDP or HTTP/HTTPS.
- You want static anycast IP addresses.
- You need fast regional failover.
- You do not want to change the application much.

## Do not confuse with CloudFront

CloudFront:

- CDN.
- Best when edge caching matters.
- Common for static assets, images, videos, React bundles, and cacheable dynamic content.

Global Accelerator:

- Network path optimization and fast failover.
- Does not primarily solve caching.
- Useful for applications where traffic must reach ALB/NLB/EC2/EIP endpoints efficiently.

## Exam traps

- If the question emphasizes static content, CDN, signed URLs, or edge caching, think CloudFront first.
- If the question emphasizes global users, TCP/UDP, static IPs, low latency path, and regional failover, think Global Accelerator.
- Route 53 latency routing helps DNS choose endpoints but does not move traffic onto the AWS global network in the same way.

## Personal note

This was an unknown service in the initial diagnostic quiz. The architecture reasoning was fine; the missing piece was service vocabulary.
