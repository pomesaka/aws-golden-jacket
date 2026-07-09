# EBS vs EFS and Multi-Attach

## EBS

Block storage for EC2.

Best for one instance disk use cases such as OS volume, database files, and application data.

## EFS

Managed shared file system.

Best for multiple Linux EC2 instances that need shared POSIX file access.

## EBS Multi-Attach

Multi-Attach lets multiple supported EC2 instances attach the same EBS volume, but it is not a general shared file system solution.

Normal file systems can be corrupted if multiple instances write at the same time without cluster-aware design.

Use Multi-Attach only for special cluster-aware applications or file systems.

## Exam hook

Multiple EC2 instances need shared POSIX file system = EFS.

EC2 disk or database storage = EBS.

Object storage or static content = S3.
