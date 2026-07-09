# AWS Organizations SCP Summary

## Core idea

SCP is an organization-level guardrail for AWS accounts.

It sets the maximum permissions available to accounts or OUs.

## What SCP is good for

- multi-account restrictions
- Region restrictions
- service restrictions
- preventive controls
- rules that member account admins should not bypass

## Important point

SCP does not grant permissions.

IAM policies are still needed to allow actions.

If SCP denies an action, IAM cannot override it.

## Exam hook

Multi-account preventive control = SCP.

Detection or audit = CloudTrail, Config, EventBridge.

Network filtering = Security Group or NACL.

## Related quiz

- `quizzes/saa-diagnostic-2026-07-07-q6.md`
