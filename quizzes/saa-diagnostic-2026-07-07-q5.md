# SAA Diagnostic Q5

## Result

- Answer: B
- Confidence: 5/5
- Result: Correct
- Topic: CloudFront, S3 private origin, signed URLs/cookies

## Summary

Static content in S3 must be delivered globally with low latency. Content is cacheable. Some content is restricted to paid members. The S3 bucket should not be directly public, and no application server should be added.

## Evaluation

CloudFront in front of S3 is the strongest answer. Use Origin Access Control to prevent direct public access to the S3 bucket. Use CloudFront signed URLs or signed cookies for restricted paid content.

## User reasoning review

Strong reasoning:

- CloudFront is the first candidate because the workload is globally distributed, static/cacheable content.
- Public S3 bucket conflicts with the requirement.
- ALB does not solve edge caching and is not a useful front end for S3 static content in this scenario.

Important correction:

- Global Accelerator is not simply a weaker CDN. It is a different service for routing traffic to supported endpoints over the AWS global network.
- S3 buckets are not the standard direct endpoint type for Global Accelerator. For S3 static content distribution, CloudFront is the expected service.

## Trap

CloudFront = CDN, edge caching, S3 origin protection, signed URL/cookie access control.

Global Accelerator = global network path optimization and fast failover for supported regional endpoints such as ALB, NLB, EC2, and Elastic IP.

## Related notes

- `comparisons/cloudfront-vs-global-accelerator.md`
- `services/global-accelerator.md`
