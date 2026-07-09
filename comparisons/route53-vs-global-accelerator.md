# Route 53 vs Global Accelerator

## Route 53

Use when the question emphasizes DNS, name resolution, routing policy, or DNS-level failover.

Route 53 decides what DNS answer to return.

After DNS resolution, Route 53 is no longer in the traffic path.

Common clues:

- DNS level
- latency-based routing
- weighted routing
- failover routing
- health checks

## Global Accelerator

Use when the question emphasizes static IPs, AWS global network, TCP or UDP performance, or fast regional failover for supported endpoints.

Global Accelerator stays in the traffic path after the client connects to its anycast IPs.

Common clues:

- static IP
- TCP or UDP performance
- AWS global network
- reduce internet path variability
- regional endpoints such as ALB or NLB

## Exam hook

DNS-level solution = Route 53.

Traffic-path optimization after IP selection = Global Accelerator.

CDN and cache = CloudFront.

## Related quiz

- `quizzes/saa-q8-route53.md`
