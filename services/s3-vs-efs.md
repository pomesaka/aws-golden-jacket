# S3 vs EFS

## Core distinction

S3 is object storage.

EFS is a managed shared file system.

## Use S3 when

- Data is object-like: images, videos, PDFs, backups, logs, static website assets.
- The app can read/write through S3 APIs or SDKs.
- You want high durability and easy integration with CloudFront, lifecycle rules, events, and access policies.
- You want EC2/ECS/Lambda to stay stateless.

## Use EFS when

- The application expects a POSIX file system.
- Multiple Linux clients need to mount the same file system.
- Code changes must be minimized for an app that writes to local paths.
- NFS semantics matter.

## Exam shortcut

- User-uploaded images with scalable web servers -> S3 first.
- Shared Linux file path, NFS, POSIX, lift-and-shift, minimal code change -> EFS first.

## Common traps

- "Multiple EC2 instances need shared access" is not enough by itself to choose EFS.
- Check whether the data is actually an object or whether the application specifically needs file-system semantics.
- EBS is normally attached to one EC2 instance in one AZ, so it is not the default answer for multi-instance shared storage.

## Personal note

Initial diagnostic answer chose EFS for uploaded images. The reasoning about shared storage was valid, but the AWS exam best-practice default for user-uploaded image objects is S3.
