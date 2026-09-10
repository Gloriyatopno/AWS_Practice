# AWS Compute & Storage Services

## Phase 2 — AWS Compute & Storage Services



# 1. AWS Compute Services

## Server Virtualization

Server virtualization is a technology that allows a physical server to be divided into multiple virtual servers.

Each virtual server can run its own operating system and applications.

### Benefits

- Better utilization of physical hardware.
- Reduces infrastructure costs.
- Allows multiple workloads to run on the same physical server.
- Makes it easier to create and manage virtual servers.

AWS uses virtualization technology to provide compute resources such as Amazon EC2 instances.

---

# 2. Amazon EC2

Amazon Elastic Compute Cloud (EC2) provides resizable virtual servers in the AWS Cloud.

An EC2 instance can be used to run applications, websites, backend services, and other workloads.

### Important EC2 Components

- **AMI (Amazon Machine Image)** — Template used to launch an EC2 instance.
- **Instance Type** — Defines the compute resources such as CPU and memory.
- **Key Pair** — Used for secure access to an EC2 instance.
- **Security Group** — Acts as a virtual firewall for the instance.
- **EBS Volume** — Provides persistent block storage for the instance.
- **Public IP** — Allows communication with the internet.
- **Private IP** — Used for communication within the VPC.

### EC2 Instance Types

EC2 provides different instance families for different workloads.

Examples:

- General purpose
- Compute optimized
- Memory optimized
- Storage optimized
- Accelerated computing

For basic learning and small workloads, a small general-purpose instance such as `t3.micro` can be used when eligible for the applicable Free Tier benefits.

---

# 3. Launching an EC2 Instance

Basic steps:

1. Open the AWS Management Console.
2. Search for **EC2**.
3. Open the EC2 service.
4. Choose **Launch instance**.
5. Enter an instance name.
6. Select an appropriate AMI.
7. Select an instance type.
8. Select or create a key pair.
9. Configure the network settings.
10. Configure the security group.
11. Configure storage.
12. Review the settings.
13. Launch the instance.

After launching, the instance can be monitored from the EC2 Instances page.

---

# 4. Connecting to EC2

EC2 instances can be accessed using methods such as:

- SSH
- EC2 Instance Connect
- Systems Manager Session Manager

For a Linux EC2 instance, SSH can be used to open a terminal session.

After successfully connecting, a prompt similar to the following can be displayed:

```text
[ec2-user@ip-172-31-19-65 ~]$
```

The `ec2-user` account is the default user commonly used to access Amazon Linux instances.

---

# 5. EC2 Network Verification

After connecting to an EC2 instance, network configuration can be checked using:

```bash
ifconfig
```

Example output can contain:

```text
ens5
inet 172.31.x.x
```

The `172.31.x.x` address is a private IPv4 address assigned to the EC2 instance inside the VPC.

Internet connectivity can be tested using:

```bash
ping google.com
```

A successful response indicates that the instance can resolve the domain name and communicate with the destination.

### Example

```text
16 packets transmitted, 16 received, 0% packet loss
```

This indicates that all packets in the test were successfully received.

---

# 6. EC2 User Data

EC2 User Data allows commands or scripts to be executed automatically when an EC2 instance is launched.

It is commonly used for initial instance configuration.

### Example

```bash
#!/bin/bash

dnf update -y
dnf install -y httpd
systemctl start httpd
systemctl enable httpd
```

The script can be used to:

- Install software.
- Update packages.
- Configure services.
- Start applications.
- Perform initial server setup.

### User Data Execution

User Data is generally executed during the initial launch of an instance.

It can be useful for automating server configuration instead of manually performing the same steps after connecting to the instance.

---

# 7. EC2 Instance Metadata

EC2 Instance Metadata provides information about a running EC2 instance.

It can provide information such as:

- Instance ID
- Instance type
- Private IP address
- Availability Zone
- Network information
- IAM role information

Instance metadata can be accessed from inside the EC2 instance through the instance metadata service.

For IMDSv2, a session token is required to access metadata.

---

# 8. Access Keys

AWS access keys are credentials used for programmatic access to AWS services.

An access key consists of:

- Access Key ID
- Secret Access Key

They can be used with:

- AWS CLI
- AWS SDKs
- Applications

### Security Best Practices

- Never share access keys.
- Never commit access keys to GitHub.
- Do not hard-code credentials in application code.
- Remove unused access keys.
- Prefer temporary credentials and IAM roles whenever possible.

---

# 9. IAM Roles with EC2

An IAM role allows an EC2 instance to access AWS services without storing long-term access keys on the instance.

For example, an EC2 instance can be assigned a role that allows it to access an S3 bucket.

```text
EC2 Instance
      |
      ↓
   IAM Role
      |
      ↓
   Amazon S3
```

### Benefits

- Avoids storing long-term credentials on the server.
- Provides temporary credentials.
- Makes permission management easier.
- Improves security.

### Example Use Case

An application running on EC2 needs to read files from S3.

Instead of storing an access key inside the application:

```text
EC2 → IAM Role → S3
```

The application can use the permissions provided through the role.

---

# 10. AWS Batch

AWS Batch is a managed service used to run batch computing workloads.

It automatically provisions the required compute resources and runs batch jobs according to workload requirements.

### Use Cases

- Data processing
- Scientific calculations
- Large-scale batch jobs
- Financial calculations
- Image or video processing

---

# 11. Amazon Lightsail

Amazon Lightsail provides simplified cloud resources for applications that do not require the full complexity of configuring AWS infrastructure.

Lightsail can provide:

- Virtual servers
- Storage
- Networking
- Databases

It is useful for beginners, small applications, websites, and simple development environments.

---

# 12. Docker Containers

Docker containers package an application together with its dependencies so that it can run consistently across different environments.

### Benefits

- Portable
- Lightweight
- Fast to start
- Consistent environments
- Easier application deployment

### Virtual Machines vs Containers

| Virtual Machines | Containers |
|---|---|
| Include a full guest OS | Share the host OS kernel |
| Generally heavier | Generally lightweight |
| Slower to start | Faster to start |
| Strong isolation | Process-level isolation |

---

# 13. Microservices

Microservices architecture divides an application into smaller, independent services.

Each service can perform a specific function.

### Example

An online shopping application could have:

```text
Shopping Application
│
├── User Service
├── Product Service
├── Order Service
└── Payment Service
```

Each service can be developed, deployed, and scaled independently.

---

# 14. Amazon ECS

Amazon Elastic Container Service (ECS) is a managed container orchestration service.

ECS can be used to deploy, manage, and scale containerized applications.

ECS can run containers using:

- Amazon EC2
- AWS Fargate

### Basic Flow

```text
Docker Container
       ↓
      ECS
       ↓
EC2 / Fargate
```

---

# 15. AWS Fargate

AWS Fargate is a serverless compute engine for running containers.

With Fargate, users do not need to manage the underlying servers.

### Benefits

- No server management.
- Automatically provides compute resources for containers.
- Works with ECS.
- Useful for containerized applications.

### ECS with EC2 vs Fargate

| ECS with EC2 | ECS with Fargate |
|---|---|
| Customer manages EC2 instances | AWS manages underlying infrastructure |
| More control over servers | Less infrastructure management |
| Need to manage instance capacity | No need to manage EC2 capacity |

---

# 16. AWS Storage Services

AWS provides different types of storage for different requirements.

The three major storage types are:

- Block storage
- File storage
- Object storage

---

# 17. Block, File and Object Storage

| Storage Type | AWS Service | Main Use |
|---|---|---|
| Block Storage | Amazon EBS | EC2 disks and operating systems |
| File Storage | Amazon EFS | Shared file systems |
| Object Storage | Amazon S3 | Files, images, videos, backups |

### Block Storage

Data is stored in blocks and presented as a disk to a compute instance.

### File Storage

Data is organized as files and directories and can be shared between multiple systems.

### Object Storage

Data is stored as objects inside containers called buckets.

---

# 18. Amazon EBS

Amazon Elastic Block Store (EBS) provides persistent block storage for EC2 instances.

EBS volumes can be used for:

- Operating systems
- Applications
- Databases
- Persistent data

### Features

- Persistent storage.
- Can be attached to EC2 instances.
- Supports snapshots.
- Different volume types are available for different workloads.

---

# 19. EBS Snapshots

An EBS snapshot is a point-in-time backup of an EBS volume.

Snapshots can be used to:

- Back up data.
- Restore volumes.
- Create new EBS volumes.
- Protect against data loss.

### Basic Flow

```text
EBS Volume
     ↓
Snapshot
     ↓
Backup / Restore
```

---

# 20. Amazon EFS

Amazon Elastic File System (EFS) provides managed file storage that can be accessed by multiple compute resources.

It is useful when multiple EC2 instances need access to the same files.

### Example

```text
        EFS
       /   \
     EC2   EC2
```

Both instances can access the shared file system.

### Benefits

- Shared file storage.
- Automatically scales with usage.
- Suitable for applications requiring shared files.

---

# 21. Amazon S3

Amazon Simple Storage Service (S3) is an object storage service.

S3 stores data as objects inside buckets.

### S3 Structure

```text
S3 Bucket
│
├── image.jpg
├── document.pdf
├── video.mp4
└── backup.zip
```

### Important S3 Concepts

- Bucket
- Object
- Object key
- Storage class
- Versioning
- Lifecycle rules
- Replication

---

# 22. Creating an S3 Bucket

Basic steps:

1. Open the AWS Management Console.
2. Search for **S3**.
3. Choose **Create bucket**.
4. Enter a globally unique bucket name.
5. Select the required AWS Region.
6. Configure the required settings.
7. Keep public access blocked unless public access is specifically required.
8. Create the bucket.

---

# 23. Uploading Objects to S3

Objects such as files and images can be uploaded to an S3 bucket.

Basic steps:

1. Open the S3 bucket.
2. Choose **Upload**.
3. Add files or folders.
4. Review the upload settings.
5. Upload the objects.

The uploaded objects can then be viewed inside the bucket.

---

# 24. S3 Storage Classes

S3 provides different storage classes based on access frequency and storage requirements.

| Storage Class | Suitable For |
|---|---|
| S3 Standard | Frequently accessed data |
| S3 Intelligent-Tiering | Data with changing or unpredictable access |
| S3 Standard-IA | Infrequently accessed data |
| S3 One Zone-IA | Infrequently accessed data that can be stored in one Availability Zone |
| S3 Glacier Instant Retrieval | Archive data requiring fast retrieval |
| S3 Glacier Flexible Retrieval | Long-term archival with flexible retrieval |
| S3 Glacier Deep Archive | Long-term data that is rarely accessed |

Choosing an appropriate storage class can help optimize storage costs.

---

# 25. S3 Versioning

S3 Versioning keeps multiple versions of an object in a bucket.

For example:

```text
document.pdf
     │
     ├── Version 1
     ├── Version 2
     └── Version 3
```

### Benefits

- Protects against accidental deletion.
- Helps recover previous versions.
- Protects against accidental overwrites.

---

# 26. S3 Replication

S3 replication automatically copies objects from one S3 bucket to another.

Common replication options include:

- Same-Region Replication (SRR)
- Cross-Region Replication (CRR)

### Use Cases

- Disaster recovery
- Compliance requirements
- Data redundancy
- Keeping data closer to users

---

# 27. S3 Lifecycle Rules

S3 Lifecycle rules automatically manage objects based on defined conditions.

Objects can be moved between storage classes or deleted after a specified period.

### Example

```text
S3 Standard
      ↓
S3 Standard-IA
      ↓
S3 Glacier
      ↓
Delete
```

Lifecycle rules can help reduce storage costs and automate data management.

---

# 28. S3 Glacier

Amazon S3 Glacier storage classes are designed for long-term data archival.

They are suitable for data that is rarely accessed but needs to be retained.

### Use Cases

- Backups
- Archives
- Compliance records
- Historical data

Glacier storage classes generally provide lower storage costs compared with frequently accessed storage classes, with different retrieval characteristics.

---

# 29. AWS Storage Gateway

AWS Storage Gateway provides a bridge between on-premises environments and AWS cloud storage.

It allows applications running on-premises to use AWS storage services.

### Use Cases

- Hybrid cloud storage
- Backup
- Disaster recovery
- Data migration

---

# 30. Storage Comparison

| Service | Storage Type | Main Purpose |
|---|---|---|
| Amazon EBS | Block | Storage for EC2 |
| Amazon EFS | File | Shared file storage |
| Amazon S3 | Object | Scalable object storage |
| S3 Glacier | Object/Archive | Long-term archival |
| Storage Gateway | Hybrid | Connect on-premises storage with AWS |

---

# 31. Compute Service Comparison

| Service | Purpose | Server Management |
|---|---|---|
| EC2 | Virtual servers | Customer manages instance |
| Lightsail | Simplified virtual servers | Simplified management |
| AWS Batch | Batch workloads | AWS manages required infrastructure |
| ECS | Container orchestration | Depends on launch type |
| Fargate | Serverless containers | AWS manages underlying infrastructure |

---

# 32. Practical Work

## EC2 Hands-on

The following EC2 activities were practiced:

- Launched an EC2 instance.
- Connected to the EC2 instance.
- Used Amazon Linux 2023.
- Checked network configuration using `ifconfig`.
- Tested internet connectivity using `ping google.com`.

### Network Verification

Command:

```bash
ifconfig
```

The EC2 instance displayed a private IPv4 address in the VPC.

Command:

```bash
ping google.com
```

The connectivity test successfully returned responses with no packet loss.

### Evidence

Screenshots of the EC2 instance, connection, network configuration, and connectivity test are maintained as hands-on evidence.

---

## EC2 User Data

### Status

To be completed.

Planned practice:

- Launch/configure an EC2 instance using User Data.
- Use a shell script to install and configure a service.
- Verify that the script executed successfully.

---

## IAM Role with EC2

### Status

To be completed.

Planned practice:

- Create or use an appropriate IAM role.
- Attach the required permissions.
- Associate the role with an EC2 instance.
- Test access to the required AWS service.

---

## S3 Hands-on

### Status

To be completed.

Planned practice:

- Create an S3 bucket.
- Upload objects.
- Explore different S3 storage classes.
- Review versioning.
- Review lifecycle rules and replication concepts.

---

# 33. Key Takeaways

- EC2 provides virtual servers in AWS.
- EC2 User Data can automate initial server configuration.
- EC2 Metadata provides information about the running instance.
- IAM roles allow AWS resources such as EC2 to access other AWS services securely.
- Containers package applications and their dependencies together.
- ECS manages containerized applications.
- Fargate runs containers without requiring users to manage servers.
- EBS provides block storage for EC2.
- EFS provides shared file storage.
- S3 provides scalable object storage.
- S3 storage classes are designed for different access and cost requirements.
- Versioning helps protect objects from accidental deletion or overwriting.
- Lifecycle rules automate object transitions and deletion.
- Replication can provide redundancy and support disaster recovery.
- Glacier storage classes are designed for long-term archival.
- Storage Gateway connects on-premises environments with AWS storage.
