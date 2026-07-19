# Q9 DR basics

- Answer: A, B, C
- Confidence: 3/5
- Result: Correct
- Reasoning correctly eliminated hourly snapshots for failing RPO < 1 minute, same-region replicas for failing regional-disaster coverage, and active-active writes for violating the single-writer requirement.
- Important correction: the described standby application stack is closer to Warm Standby than Pilot Light.

## Concepts retained

- DR = Disaster Recovery: restoring service after a major failure.
- RPO = maximum acceptable data loss window.
- RTO = maximum acceptable recovery time.
- HA focuses on avoiding or minimizing outages, often within one region.
- DR focuses on recovery from larger failures such as a regional outage.
- Typical design here: Aurora Global Database + reduced-capacity standby application stack + Route 53 failover.
