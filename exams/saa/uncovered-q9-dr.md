# Uncovered Topic Q9 — Multi-Region DR

Date: 2026-07-19

## Scenario focus

- Primary Region: Tokyo
- Stack: EC2 Auto Scaling Group, ALB, Aurora MySQL
- Requirements: RPO under 1 minute, RTO under 15 minutes, single-Region writes during normal operation, reduced standby cost, DNS failover, minimal application redesign

## User answer

- Answer: A, B, C
- Confidence: 3/5
- Result: Correct

## Reasoning demonstrated

- Correctly rejected hourly snapshot copy because it cannot meet the sub-minute RPO.
- Correctly rejected a same-Region Aurora read replica because it does not survive a Tokyo Region outage.
- Correctly rejected active-active writes because the requirement specifies writes only in Tokyo during normal operation.
- Identified the design as a pilot-light-style DR approach.

## Correct architecture

- Aurora Global Database with a secondary cluster in the standby Region.
- A reduced-capacity application stack in the standby Region that can scale up after failover.
- Route 53 failover routing with health evaluation to direct traffic to the standby ALB.

## Important correction

The application layer described in option B is more accurately called **warm standby**, not pure pilot light, because the full application stack is already running at reduced capacity and can accept traffic after scaling. Pilot light normally keeps only the critical core, especially replicated data, running while most application infrastructure is provisioned during recovery.

## Retest focus

- Distinguish backup and restore, pilot light, warm standby, and multi-site active-active by RPO, RTO, cost, and what remains running.
- Remember that Aurora Global Database normally has one writable primary Region and read-only secondary Regions, with asynchronous cross-Region replication and failover measured in minutes / RPO commonly measured in seconds.
