# SAA Diagnostic Q4

## Result

- Answer: B
- Confidence: 5/5
- Result: Correct
- Topic: ElastiCache vs RDS Read Replica

## Summary

RDS MySQL product list pages are slow. The workload has many SELECT queries, low update frequency, repeated query results, and high DB CPU. Large DB migration should be avoided, but application changes are allowed.

## Evaluation

ElastiCache for Redis is the strongest answer because the workload is cache-friendly: repeated reads, low update frequency, and a need for low response time without a large database migration.

## Follow-up comparison

If the problem were simply read capacity for varied SELECT traffic, RDS Read Replica would be strong.

In this question, Redis is stronger because the same results are repeatedly reused and cache invalidation or TTL can reduce database load.

## Trap

Read Replica still executes database queries. Cache can avoid repeated database queries when the same results are reused.

## Related notes

- `services/rds-replication.md`
- future: `comparisons/elasticache-vs-read-replica.md`
