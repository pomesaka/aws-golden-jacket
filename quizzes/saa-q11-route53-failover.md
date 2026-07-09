# SAA Q11 Route 53 Failover

User answer: A.

Correct answer: A.

Result: Correct.

Confidence: 5 of 5.

Topic: Route 53 failover routing.

Key note:
Active passive DNS failover uses Route 53 failover routing policy with health checks.

Primary endpoint: Tokyo.

Secondary endpoint: Northern Virginia.

Why not weighted:
Weighted routing splits traffic by configured weights and does not mean active passive failover.

Why not latency routing:
Latency routing sends users to low latency endpoints and does not mean all users normally go to Tokyo.

Why not Global Accelerator:
Global Accelerator can do regional endpoint failover, but this question asks for DNS level switching.

Learning note:
DNS level, primary secondary, failover only on outage = Route 53 failover routing.
