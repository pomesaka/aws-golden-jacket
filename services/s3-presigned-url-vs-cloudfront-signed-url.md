# S3 Pre-signed URL vs CloudFront Signed URL

## Context

The user currently uses S3 pre-signed URLs for a case where users upload or view their own files stored in private S3.

## Current judgment

For this use case, continuing with S3 pre-signed URLs is reasonable.

## S3 pre-signed URL

Best fit when:

- access is direct to S3
- the operation is temporary
- upload or download is scoped to one object
- the application already checks whether the user can access that object
- global CDN caching is not the main requirement

Typical use cases:

- user uploads a file directly from browser to S3
- user downloads their own uploaded file
- temporary access to one private object

## CloudFront signed URL or signed cookie

Best fit when:

- content should be served through CloudFront
- global low latency and caching matter
- many users may access the same content
- S3 should remain private behind CloudFront Origin Access Control
- access is needed for many files or a member-only area

## Exam memory hook

Private S3 object temporary upload/download = S3 pre-signed URL.

Private S3 static content with CDN, cache, and global delivery = CloudFront + OAC + signed URL or signed cookie.

## Important distinction

The application still performs the user authentication and authorization decision.

The signed URL or signed cookie is the delivery permission generated after that decision.
