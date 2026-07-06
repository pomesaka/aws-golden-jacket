# Gateway VPC Endpoint vs Interface VPC Endpoint

## Gateway VPC Endpoint

Use for:

- Amazon S3
- DynamoDB

Characteristics:

- Route-table based.
- No hourly charge for the endpoint itself.
- Common answer for private subnet access to S3 or DynamoDB without internet path.

Exam signals:

- private subnet to S3
- private subnet to DynamoDB
- cost-effective
- no NAT gateway
- no internet gateway path

## Interface VPC Endpoint

Use for:

- Many AWS services through AWS PrivateLink.

Characteristics:

- Creates elastic network interfaces in subnets.
- Uses private IP addresses.
- Usually has hourly and data processing charges.
- Security groups can control access to endpoint ENIs.

Exam signals:

- private connectivity to AWS service other than S3/DynamoDB
- AWS PrivateLink
- service endpoint with private IP
- endpoint security group

## Fast rule

- S3 or DynamoDB + lowest cost private access -> Gateway Endpoint.
- Most other AWS services over PrivateLink -> Interface Endpoint.

## Related notes

- `services/kms.md`
