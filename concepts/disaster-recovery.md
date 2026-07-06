# Disaster Recovery

## Purpose

Prepare workloads to recover from major failures such as Region-level outages, data corruption, or accidental deletion.

## Core metrics

- RTO: Recovery Time Objective. How quickly the service must recover.
- RPO: Recovery Point Objective. How much data loss is acceptable.

## Common AWS patterns

- Backup and restore
- Pilot light
- Warm standby
- Multi-site active-active

## AWS building blocks

- AWS Backup
- S3 versioning and replication
- RDS snapshots and cross-region read replicas
- Aurora Global Database
- Route 53 failover routing
- CloudFront / Global Accelerator depending on traffic pattern
- Infrastructure as Code for reproducible environments

## Exam signals

- lowest cost DR
- fastest recovery
- minimal data loss
- cross-region failover
- active-active
- active-passive

## Common traps

- Backups alone rarely meet low RTO.
- Multi-AZ is not the same as cross-region DR.
- Cross-region replication helps data locality and recovery but does not automatically solve application failover.

## Related notes

- `concepts/high-availability.md`
- `services/rds-replication.md`
- `services/global-accelerator.md`
