# High Availability

## Purpose

Design workloads so that failures of individual components, instances, Availability Zones, or Regions do not cause unacceptable downtime.

## AWS building blocks

- Multiple Availability Zones
- Auto Scaling
- Elastic Load Balancing
- Route 53 health checks and routing policies
- RDS Multi-AZ
- Aurora replicas and global database patterns
- S3 durability and regional architecture
- Multi-Region active-passive or active-active designs

## Exam signals

Look for words such as:

- highly available
- fault tolerant
- automatic failover
- no single point of failure
- AZ failure
- regional disaster recovery

## Common traps

- Read scaling is not the same as high availability.
- Backups are not the same as failover.
- Multi-AZ improves availability but does not necessarily improve read performance.
- Multi-Region improves disaster recovery but adds complexity and cost.

## Related notes

- `services/rds-replication.md`
- `concepts/disaster-recovery.md`
- `comparisons/rds-multi-az-vs-read-replica.md`
