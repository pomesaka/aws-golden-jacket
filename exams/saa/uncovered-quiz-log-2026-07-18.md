# SAA Uncovered-topic Quiz Log — 2026-07-18

## Study mode

- Difficulty target: SAA-plus, with SAP-level adjacent engineering knowledge explained after grading.
- Avoid simple service-identification questions.
- Validate the requested number of correct choices before presenting each question.

## Q6: AWS PrivateLink and cross-account service exposure

- User answer: A, B, C
- Confidence: 2/5
- Result: Correct.
- Reasoning correctly eliminated VPC Peering because broad routing and overlapping CIDRs were disallowed.
- Key architecture:
  - Provider: application targets behind an internal NLB, exposed through a VPC Endpoint Service.
  - Consumer: Interface VPC Endpoints create endpoint ENIs in selected subnets/AZs.
  - Access control: allowed principals and optional endpoint-connection acceptance.
- Durable concepts:
  - VPC Peering / Transit Gateway connect networks.
  - PrivateLink connects a specific service without exchanging VPC routes.
  - Overlapping CIDRs work because consumers connect to endpoint ENIs inside their own VPC rather than directly routing to provider IPs.
  - A Route 53 Private Hosted Zone provides name resolution only; it does not create network reachability.

## PrivateLink deep dive

- PrivateLink is best understood as an AWS-managed L4 connection broker.
- Consumer applications connect to an Interface Endpoint ENI using a private IP.
- AWS PrivateLink maps the connection to a provider-side Endpoint Service and associated NLB/GWLB.
- PrivateLink itself does not perform HTTP host/path/header routing.
- L7 processing can be added behind the NLB, for example NLB -> ALB -> application.
- Endpoint Service is not an ENI and not DNS. It is a provider-side logical control-plane resource defining:
  - associated NLB/GWLB,
  - allowed principals,
  - connection acceptance behavior,
  - supported Availability Zones,
  - optional private DNS name.
- Role separation:
  - DNS: resolves a name to the consumer endpoint ENI IP.
  - Endpoint ENI: consumer-side connection entry point.
  - Endpoint Service: maps accepted PrivateLink connections to the provider load balancer.
  - NLB/GWLB: receives and distributes the provider-side traffic.

## Q7: Lambda concurrency control for SQS

- User answer: B, C, E
- Confidence: 2/5
- Result: Question invalid because it requested three choices while only C and E were correct.
- Correct selections:
  - C: Event Source Mapping Maximum Concurrency limits concurrency from that SQS source without reserving account concurrency.
  - E: SQS DLQ and maxReceiveCount isolate poison messages after repeated receives.
- Incorrect selections and distinctions:
  - Reserved Concurrency limits the entire function and also reserves capacity away from other functions.
  - Provisioned Concurrency pre-initializes execution environments to reduce cold starts; it is not a maximum concurrency limit.
  - Visibility Timeout must not be shorter than function execution time.
- Durable distinction:
  - Reserved Concurrency = function-wide ceiling plus reserved capacity.
  - Provisioned Concurrency = pre-warmed execution environments.
  - SQS Event Source Mapping Maximum Concurrency = source-specific backpressure.

## Q8: SQS partial batch failure

- User answer: A, C
- Confidence: 2/5
- Result: Correct.
- A: Enable ReportBatchItemFailures and return only failed SQS message IDs.
- C: Maintain application-level idempotency because SQS/Lambda remains at-least-once.
- Key behavior:
  - Throwing an exception for one failed record causes the whole batch to be retried.
  - Partial batch response deletes successful messages and retries only failed messages.
  - DLQ redrive still applies to repeatedly failing messages.
  - Idempotency protects against failures after side effects succeed but before acknowledgement completes.

## Event Source Mapping deep dive

Event Source Mapping is a Lambda-managed consumer resource between a poll-based event source and a Lambda function.

### Poll-based sources

- Amazon SQS
- Kinesis Data Streams
- DynamoDB Streams
- Amazon MSK / self-managed Kafka
- Amazon MQ and other supported sources

This differs from push integrations such as S3, SNS, EventBridge, and API Gateway, where the source invokes Lambda directly.

### SQS processing flow

1. Event Source Mapping polls SQS.
2. Messages become invisible for the Visibility Timeout.
3. Records are grouped into a batch.
4. Lambda is invoked synchronously with the batch.
5. On success, Lambda service deletes successful messages.
6. On failure, messages become visible again after Visibility Timeout.
7. With ReportBatchItemFailures, only listed failed items are retried.

### Important controls

- Event source ARN: which queue/stream to consume.
- Function target: which Lambda function/version/alias to invoke.
- Batch Size: maximum records per invocation.
- Maximum Batching Window: maximum wait to accumulate a batch.
- Maximum Concurrency: maximum concurrent invocations from this mapping.
- Filter Criteria: discard nonmatching events before function invocation.
- FunctionResponseTypes / ReportBatchItemFailures: partial batch failure reporting.
- Enabled/Disabled state: pause consumption without deleting the mapping.

### Important operational distinctions

- Event Source Mapping performs ReceiveMessage/DeleteMessage behavior, while the Lambda function code processes the Records payload.
- Permissions are evaluated using the Lambda execution role even though the managed poller performs the SQS API calls.
- SQS DLQ configuration belongs primarily to the SQS redrive policy, not the Lambda asynchronous-invocation DLQ.
- One queue connected to multiple Lambda mappings creates competing consumers, not fan-out.
- For fan-out, use SNS/EventBridge to separate SQS queues, then attach one consumer per queue.
- Standard Queue processing requires idempotency because delivery is at least once.
- FIFO partial-failure handling must preserve ordering; processing should stop after a failure and return failed/unprocessed records appropriately.

## Follow-up priorities

- Retest Reserved vs Provisioned vs Maximum Concurrency with mixed invocation sources.
- Drill SQS Visibility Timeout, batching, partial failures, DLQ, and idempotency together.
- Compare Event Source Mapping behavior across SQS, Kinesis, and DynamoDB Streams.
- Continue uncovered-topic quiz at SAA-plus difficulty.
