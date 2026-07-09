# SAA Diagnostic Q6

## Result

- Answer: B
- Confidence: 4/5
- Result: Correct
- Topic: AWS Organizations SCP, region restriction, preventive guardrail

## Summary

A company manages multiple AWS accounts with AWS Organizations. Security wants to prevent EC2 instance launches outside approved Regions across existing and future member accounts. Local account admins must not be able to bypass the restriction with IAM policies.

## Evaluation

Service Control Policy attached to the target OU is the best answer. SCPs set permission guardrails for accounts in an organization. An explicit deny in an SCP cannot be overridden by IAM policies in member accounts.

## User reasoning review

Strong reasoning:

- A is operationally weak and does not scale cleanly to new accounts.
- C only detects or notifies; it does not prevent the action.
- B matches the need for a centrally enforced preventive control.

Correction / learning point:

- D is wrong because NACLs are subnet-level network controls. They do not control whether an IAM principal is allowed to call EC2 RunInstances in a Region.

## Exam memory hook

Multi-account preventive guardrail that account admins cannot bypass = AWS Organizations SCP.

Detect after the fact = CloudTrail / EventBridge / Config.

Network traffic filtering = Security Group or NACL, not account-level API permission control.

## Mistake type

No mistake. Moderate vocabulary gap around Organizations/SCP and NACL role.

## Related notes

- future: `services/aws-organizations-scp.md`
- future: `comparisons/scp-vs-iam-policy-vs-permission-boundary.md`
- future: `comparisons/security-group-vs-nacl.md`
