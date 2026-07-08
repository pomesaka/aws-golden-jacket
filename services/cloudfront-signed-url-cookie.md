# CloudFront Signed URL and Signed Cookie

## Why this note exists

During SAA diagnostic Q5, the user selected CloudFront correctly but did not know that CloudFront can handle signed URLs and signed cookies for restricted content.

## Key idea

CloudFront can distribute private content by validating signed URLs or signed cookies at the edge.

Use cases:

- paid member content
- limited-time downloads
- subscriber-only static assets
- private video or document delivery

## Signed URL

Use a signed URL when access control is tied to a specific file or object.

Good fit:

- one paid download link
- temporary access to one object
- short-lived sharing link

## Signed Cookie

Use signed cookies when access control should apply to multiple files without changing every URL.

Good fit:

- subscriber-only area
- many restricted files under the same path
- keep existing URLs unchanged

## S3 private origin

For S3 origins, keep the bucket private and use CloudFront Origin Access Control.

Typical pattern:

1. S3 bucket is not public.
2. CloudFront distribution uses the S3 bucket as origin.
3. Origin Access Control lets CloudFront access S3.
4. Bucket policy allows access from that CloudFront distribution.
5. Viewers access content through CloudFront, not directly through S3.

## Exam memory hook

S3 static content + global low latency + cache + private bucket = CloudFront + OAC.

Paid/private content through CloudFront = signed URL or signed cookie.

## Signed URL vs signed cookie

- Signed URL: one file or explicit URL access.
- Signed cookie: multiple restricted files or a restricted area.

## Related quiz

- `quizzes/saa-diagnostic-2026-07-07-q5.md`

## Related comparison

- `comparisons/cloudfront-vs-global-accelerator.md`
