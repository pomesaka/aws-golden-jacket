# Stateless and Scaling

## Purpose

Design applications so compute capacity can scale horizontally without tying user data or state to individual instances or tasks.

## AWS building blocks

- Auto Scaling groups
- ECS services and Fargate tasks
- Lambda concurrency
- ALB target groups
- S3 for object storage
- DynamoDB or RDS for durable state
- ElastiCache for cache/session patterns when appropriate
- EFS only when shared file-system semantics are required

## Exam signals

- Auto Scaling
- horizontal scaling
- replacement instances
- uploaded files missing on new instances
- session stickiness vs external session store
- stateless web tier

## Common traps

- Local instance storage is not durable application state.
- Sticky sessions may be a workaround but often lose to externalizing state.
- EFS is not automatically the best answer just because multiple instances need access.
- S3 is usually preferred for user-uploaded object data.

## Related notes

- `services/s3-vs-efs.md`
