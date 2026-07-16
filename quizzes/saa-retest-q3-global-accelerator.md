# SAA Weak-Area Retest Q3 - Route 53 vs Global Accelerator

## Result

- User answer: C
- Correct answer: C
- Confidence: 5/5
- Result: Correct
- Risk level: Low

## Topic

Route 53 latency routing vs AWS Global Accelerator.

## Why

AWS Global Accelerator is the best fit because the requirements include:

- routing users to the closest healthy regional endpoint
- static anycast IP addresses for clients
- fast regional failover without waiting for DNS TTL expiration
- use of the AWS global network
- no need for HTTP content caching

Route 53 latency-based routing can return the lowest-latency healthy endpoint at the DNS layer, but clients and resolvers can cache DNS answers until TTL expiration. Route 53 also does not itself provide the pair of static global anycast IP addresses that Global Accelerator provides.

CloudFront is not the best fit because caching is not required and the question focuses on endpoint routing, static IPs, and fast failover.

## Reasoning quality

The user correctly identified all decisive clues:

- closest healthy ALB endpoint
- AWS backbone network
- no DNS TTL dependency
- fixed IP addresses

The user also correctly recognized Route 53 latency routing as a plausible distractor but rejected it because of DNS caching and the static IP requirement.

## Retest outcome

The previous Route 53 vs Global Accelerator misconception has been successfully corrected at high confidence.
