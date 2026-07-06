# RDS Replication Patterns

## Multi-AZ

Purpose: high availability and failover.

Typical behavior:

- Primary DB in one AZ.
- Standby DB in another AZ.
- Synchronous replication.
- Automatic failover.
- Not the normal answer for read scaling.

Use when:

- You need better availability.
- You need automatic failover for an AZ or DB instance failure.

## Read Replica

Purpose: read scaling and sometimes cross-region read locality.

Typical behavior:

- Asynchronous replication.
- Application can send read queries to replicas.
- Can help when read traffic dominates.
- Can be cross-region for global read access.

Use when:

- SELECT/read load is the bottleneck.
- You can direct read traffic to replica endpoints.
- You need read locality closer to users.

## Aurora Global Database

Purpose: globally distributed Aurora architecture with low-latency global reads and disaster recovery options.

Use when:

- Aurora is acceptable or already used.
- You need global reads at large scale.
- You can accept migration/testing/operational changes.

Avoid as the first answer when:

- The current database is RDS PostgreSQL/MySQL and the question says minimal change.

## Exam traps

- Multi-AZ is not a performance scaling answer.
- Read Replica is not a high-availability substitute for all failure cases.
- Aurora Global Database may be technically best but can lose when the requirement says minimal migration or minimal application change.

## Personal note

Initial diagnostic: RDS read scaling questions were handled well. Keep sharpening the exact differences between Multi-AZ, Read Replica, Aurora Replica, and Aurora Global Database.
