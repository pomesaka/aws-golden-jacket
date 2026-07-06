# RDS Multi-AZ vs Read Replica

## RDS Multi-AZ

Primary purpose: availability.

Use when:

- You need automatic failover.
- You need protection from DB instance or AZ failure.
- You want synchronous standby replication.

Exam signals:

- high availability
- automatic failover
- standby
- AZ failure

Not the default answer for:

- SELECT/read scaling
- global read locality

## Read Replica

Primary purpose: read scaling.

Use when:

- Read traffic dominates.
- SELECT workload is the bottleneck.
- You can send reads to replica endpoints.
- You need cross-region read locality.

Exam signals:

- read-heavy workload
- SELECT bottleneck
- reporting queries
- cross-region reads

Not the default answer for:

- automatic failover requirement without additional design
- synchronous standby requirement

## Fast rule

- Availability/failover -> Multi-AZ.
- Read performance/scaling -> Read Replica.

## Related notes

- `services/rds-replication.md`
- `concepts/high-availability.md`
