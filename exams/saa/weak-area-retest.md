# SAA Weak-Area Retest

## Retest 1 - SNS fan-out, SQS, Lambda, and DLQ

- Submitted answer: A, D
- Intended answer based on reasoning: A, C
- Correct answer: A, C
- Confidence: not provided as a numeric value
- Result: Conceptually correct; selection/transcription slip
- Risk: Low concept risk, but multi-response answer verification still needs attention

### What was understood correctly

- Billing, inventory, and notification processing must be isolated.
- One order event should be fanned out to independent processing paths.
- One SNS topic with one SQS queue per consumer is the correct durable fan-out pattern.
- Repeatedly failing messages should be moved to a DLQ for investigation.

### Operational flow

1. The producer publishes one order event to an SNS topic.
2. SNS delivers a copy to each subscribed SQS queue.
3. Each Lambda event source mapping polls its own queue.
4. Failed messages become visible again after the visibility timeout.
5. The queue redrive policy moves a repeatedly failing message to that queue's DLQ after `maxReceiveCount` is exceeded.

### Distinctions

- SNS: push-based fan-out and routing to multiple subscribers.
- SQS: durable buffering, backpressure absorption, independent retry state, and consumer isolation.
- Lambda event source mapping for SQS: Lambda polls the queue and invokes the function in batches.
- SQS DLQ: configured through the source queue's redrive policy.

### Why direct SNS-to-Lambda was not the best answer

Direct SNS-to-Lambda can invoke multiple functions and supports Lambda asynchronous retry behavior, but it does not provide each consumer with its own durable SQS backlog and queue-level redrive behavior. The question explicitly required independent recovery and durable reprocessing for each processing path, so SNS plus separate SQS queues plus per-queue DLQs is the best fit.

### Exam habit

For multiple-response questions, compare the final selected letters against the written reasoning before submitting. The architecture reasoning was correct, but the selected option letter did not match it.
