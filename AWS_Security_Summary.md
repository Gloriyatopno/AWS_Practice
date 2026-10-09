# AWS Cloud Security Services Summary

## 1. Identity and Access Management

| Service                           | Purpose                                                                           |
| --------------------------------- | --------------------------------------------------------------------------------- |
| AWS IAM                           | Controls who can access AWS resources and what actions they can perform.          |
| Identity Providers and Federation | Allow users to authenticate through a trusted external identity system.           |
| Amazon Cognito                    | Adds sign-up, sign-in, and authentication to web and mobile applications.         |
| AWS Directory Service             | Provides managed directory capabilities for supported applications and workloads. |

**Key point:** Use least-privilege permissions and MFA wherever appropriate.

## 2. Secrets, Encryption and Certificates

| Service                         | Purpose                                                                   |
| ------------------------------- | ------------------------------------------------------------------------- |
| AWS Secrets Manager             | Stores secrets such as database credentials and supports secret rotation. |
| Systems Manager Parameter Store | Stores configuration parameters and can store encrypted values.           |
| AWS KMS                         | Creates and manages cryptographic keys used to protect data.              |
| AWS Certificate Manager (ACM)   | Manages supported TLS/SSL certificates for secure connections.            |

**Remember:**

* Secrets Manager → secrets and rotation.
* Parameter Store → configuration and parameters.
* KMS → encryption keys.
* ACM → certificates for encrypted connections.

Never commit passwords, API keys, or other secrets to GitHub.

## 3. Logging, Monitoring and Auditing

| Service                | Purpose                                                          |
| ---------------------- | ---------------------------------------------------------------- |
| Amazon CloudWatch Logs | Collects and analyzes application and system logs.               |
| AWS CloudTrail         | Records AWS API activity and account events.                     |
| AWS Config             | Tracks resource configurations and evaluates them against rules. |
| AWS Health Dashboard   | Shows relevant AWS service events and account-specific issues.   |

**CloudWatch vs CloudTrail**

* CloudWatch helps monitor application and infrastructure behavior.
* CloudTrail helps investigate actions performed in an AWS account.

**AWS Config vs CloudTrail**

* Config focuses on resource configuration and compliance.
* CloudTrail focuses on recorded account activity and API events.

## 4. Threat Detection and Data Protection

| Service          | Purpose                                                                           |
| ---------------- | --------------------------------------------------------------------------------- |
| Amazon GuardDuty | Detects suspicious activity and potential threats using supported data sources.   |
| Amazon Macie     | Helps discover sensitive data in Amazon S3 and identify potential exposure risks. |
| AWS Security Hub | Centralizes supported security findings and helps assess security posture.        |

**Remember:**

* GuardDuty → potential threats.
* Macie → sensitive data in S3.
* Security Hub → centralized security findings.

## 5. Network and Application Protection

| Service              | Purpose                                                                          |
| -------------------- | -------------------------------------------------------------------------------- |
| Security Groups      | Stateful virtual firewalls for supported network interfaces and resources.       |
| Network ACLs (NACLs) | Stateless traffic filters at the subnet level in a VPC.                          |
| AWS WAF              | Filters web requests using configured rules.                                     |
| AWS Shield           | Helps protect applications against Distributed Denial of Service (DDoS) attacks. |

**WAF vs Shield**

* WAF filters and controls web requests.
* Shield focuses on DDoS protection.

**Security Groups vs NACLs**

* Security Groups are stateful.
* NACLs are stateless and operate at the subnet level.

## 6. Governance and Account Security

| Service                         | Purpose                                                                                                |
| ------------------------------- | ------------------------------------------------------------------------------------------------------ |
| AWS Organizations               | Centrally manages multiple AWS accounts.                                                               |
| AWS Control Tower               | Helps establish and govern a multi-account AWS environment.                                            |
| Service Control Policies (SCPs) | Set maximum available permissions for accounts or organizational units; they do not grant permissions. |
| AWS Trusted Advisor             | Provides recommendations across supported areas such as security and cost optimization.                |

## 7. Essential AWS Security Best Practices

1. Enable MFA for privileged accounts.
2. Apply least-privilege access.
3. Prefer IAM roles and temporary credentials over long-term access keys when suitable.
4. Never publish AWS credentials in source code or public repositories.
5. Encrypt sensitive data using supported encryption features.
6. Keep operating systems, dependencies, and applications updated.
7. Restrict network access using appropriate security groups and network controls.
8. Enable and review relevant logs and audit trails.
9. Monitor security findings and investigate suspicious activity.
10. Review resource permissions and configurations regularly.
11. Protect the AWS root account and avoid using it for routine work.
12. Check current AWS pricing before enabling paid services or advanced features.

## 8. Practical Security Review Checklist

Mark an item only after you have completed the corresponding activity.

* [ ] Review IAM users, roles, policies, and MFA concepts.
* [ ] Understand Secrets Manager, Parameter Store, KMS, and ACM.
* [ ] Compare CloudWatch Logs with CloudTrail.
* [ ] Review GuardDuty, Macie, and Security Hub.
* [ ] Understand the difference between WAF and Shield.
* [ ] Review Security Groups and NACLs.
* [ ] Review least privilege and credential protection.

## Key Takeaway

AWS security uses multiple layers: identity and access control, encryption, logging, monitoring, threat detection, network protection, and governance. No single service provides complete security for every workload. Security responsibilities are shared between AWS and the customer, depending on the service being used.
