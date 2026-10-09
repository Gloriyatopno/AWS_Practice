# AWS Deployment, Databases, Governance & Security

## Section 10 — Deployment and Automation

### 1. Amazon CloudFront

* A Content Delivery Network (CDN) that delivers content to users from nearby edge locations.
* Improves website loading speed and reduces latency.
* Supports caching of static and dynamic content.
* Common use: Delivering website images, videos, CSS, JavaScript, and other content globally.

### 2. AWS Global Accelerator

* Improves the availability and performance of applications for users around the world.
* Routes traffic through the AWS global network to healthy application endpoints.
* Provides static anycast IP addresses.
* Common use: Improving global access to gaming, API, and other network applications.

**CloudFront vs Global Accelerator**

* CloudFront focuses on content delivery and caching.
* Global Accelerator improves network routing and application endpoint availability.

### 3. AWS CloudFormation

* An Infrastructure as Code (IaC) service.
* Creates and manages AWS resources using templates written in JSON or YAML.
* Allows infrastructure to be repeated consistently.
* Helps automate resource creation and updates.

**Example:** Creating an EC2 instance, security group, and related resources using one template.

### 4. AWS Cloud Development Kit (CDK)

* Allows developers to define cloud infrastructure using programming languages.
* Supports languages such as TypeScript, Python, Java, and C#.
* Converts code into AWS CloudFormation templates.
* Useful for developers who prefer writing code instead of manually creating templates.

**CloudFormation vs CDK**

* CloudFormation defines infrastructure using JSON or YAML templates.
* CDK defines infrastructure using familiar programming languages and synthesizes CloudFormation templates.

### 5. AWS Elastic Beanstalk

* A service for deploying and managing web applications.
* Handles tasks such as provisioning infrastructure, deployment, load balancing, and monitoring.
* Supports platforms such as Python, Java, Node.js, and .NET.
* AWS manages much of the underlying infrastructure, while developers focus on application code.

**Example:** Deploying a Node.js web application without manually configuring every infrastructure component.

### 6. AWS Developer Tools

These tools help developers build, test, deploy, and manage application code.

* **AWS CodeBuild:** Builds and tests source code.
* **AWS CodeDeploy:** Automates application deployments.
* **AWS CodePipeline:** Automates stages of a software delivery pipeline.
* **AWS CodeArtifact:** Stores and manages software packages.
* **AWS CodeCommit:** Historically provided managed Git repositories, but it is no longer available to new customers. Existing users should check current AWS guidance.

**Example CI/CD workflow:**

Source code → Build and test → Deploy → Monitor

### 7. AWS X-Ray

* Helps developers analyze and troubleshoot distributed applications.
* Tracks requests as they travel through application components.
* Identifies performance bottlenecks, errors, and latency.
* Useful for microservices and applications that communicate with multiple services.

**Example:** Finding which service is slowing down an online shopping application.

---

## Section 11 — Databases and Analytics

### 8. Database Types

* **Relational database:** Stores structured data in tables with rows and columns.
* **Key-value database:** Stores data as key-value pairs.
* **Document database:** Stores semi-structured documents.
* **In-memory database:** Keeps frequently accessed data in memory for fast access.
* **Data warehouse:** Stores and analyzes large amounts of structured data.
* **Big data processing:** Processes very large datasets using distributed computing.

### 9. Amazon RDS

* A managed relational database service.
* Supports database engines such as PostgreSQL, MySQL, MariaDB, Oracle, and SQL Server.
* Automates many administrative tasks, including backups and maintenance.
* Suitable for applications that require relational tables and SQL queries.

**Example:** Storing customers, orders, and payments for an online store.

### 10. Amazon Aurora

* A relational database engine compatible with MySQL and PostgreSQL.
* Designed for high performance and availability.
* Managed through Amazon RDS.
* Suitable for applications that require a scalable relational database.

**RDS vs Aurora**

* RDS supports multiple database engines.
* Aurora is an AWS-designed database engine compatible with MySQL and PostgreSQL.

### 11. Amazon DynamoDB

* A fully managed NoSQL database service.
* Supports key-value and document data models.
* Provides low-latency access and automatic scaling options.
* Suitable for applications that need flexible data structures and high request volumes.

**Example:** Storing shopping cart data, gaming profiles, and application session information.

### 12. Amazon Redshift

* A managed cloud data warehouse.
* Designed for large-scale analytics and SQL queries.
* Helps analyze data collected from multiple sources.
* Common use: Business intelligence, reporting, and sales analysis.

### 13. Amazon EMR

* A managed service for running big data frameworks.
* Supports technologies such as Apache Spark and Hadoop.
* Processes and analyzes large datasets using distributed computing.
* Common use: Log analysis, data processing, and large-scale data transformation.

### 14. Amazon ElastiCache

* Provides managed in-memory caching.
* Supports Valkey and Redis OSS-compatible options, subject to current AWS offerings.
* Reduces repeated database queries and improves response time.
* Useful for frequently accessed data and session caching.

**Example:** Caching popular product information for an online store.

### 15. Amazon Athena

* A serverless interactive query service.
* Runs SQL queries directly against supported data sources, commonly data stored in Amazon S3.
* Does not require managing database servers.
* Common use: Analyzing logs and CSV, JSON, or columnar data in S3.

### 16. AWS Glue

* A managed data integration service.
* Helps discover, prepare, transform, and move data.
* Includes a Data Catalog for storing metadata about data sources.
* Common use: Preparing data before loading it into an analytics platform.

**Athena vs Glue**

* Athena queries data using SQL.
* Glue helps discover, catalog, and transform data.

### 17. Amazon Kinesis

* A collection of services for working with streaming data.
* Supports collecting and processing data as it arrives.
* Common use: Live application logs, clickstreams, IoT events, and real-time analytics.

### 18. Other AWS Database and Analytics Services

* **Amazon DocumentDB:** Managed document database service compatible with MongoDB workloads.
* **Amazon Neptune:** Managed graph database for relationships between connected data.
* **Amazon OpenSearch Service:** Search, log analytics, and observability.
* **Amazon Timestream:** Time-series data workloads, subject to current service availability and product guidance.
* **AWS Lake Formation:** Helps set up and govern data lakes.
* **AWS Data Exchange:** Helps discover and subscribe to third-party data products.

---

## Section 12 — Management and Governance

### 19. AWS Organizations

* Centrally manages multiple AWS accounts.
* Groups accounts into organizational units (OUs).
* Supports consolidated billing.
* Service control policies (SCPs) define maximum available permissions for accounts or organizational units; they do not grant permissions by themselves.

**Example:** Separating development and production into different AWS accounts.

### 20. AWS Control Tower

* Helps set up and govern a multi-account AWS environment.
* Provides a landing zone with recommended account structures and controls.
* Helps apply governance consistently across accounts.

### 21. AWS Systems Manager

* Helps manage and operate AWS resources and supported servers.
* Supports capabilities such as Session Manager, Run Command, Patch Manager, and Parameter Store.
* Reduces the need to access servers directly through SSH or RDP for supported operations.

### 22. AWS Service Catalog

* Allows organizations to create and manage approved catalogs of IT products.
* Helps users provision pre-approved resources consistently.
* Supports governance and standardization.

### 23. AWS Config

* Records resource configurations and evaluates them against rules.
* Helps identify configuration changes and non-compliant resources.
* Supports auditing and compliance monitoring.

**Example:** Detecting whether an S3 bucket's configuration violates an organizational rule.

### 24. AWS Trusted Advisor

* Provides recommendations for improving AWS environments.
* Covers areas such as cost optimization, security, performance, fault tolerance, and service limits.
* Available checks depend on the AWS support plan and current service offering.

### 25. AWS Health Dashboard

* Provides information about AWS service events and issues that may affect resources or accounts.
* Helps users understand relevant service disruptions, maintenance events, and account-specific notifications.

**Note:** AWS Health provides service-health information; it is not a replacement for application monitoring.

---

## Section 13 — AWS Cloud Security and Identity

### 26. Identity Providers and Federation

* An **Identity Provider (IdP)** authenticates users.
* **Federation** allows users to access AWS using an identity managed by another trusted identity system.
* Reduces the need to maintain separate credentials for every service.
* Common use: Employees accessing AWS through an organization's identity provider.

### 27. Amazon Cognito

* Adds sign-up, sign-in, and access-control capabilities to web and mobile applications.
* Supports user authentication and identity federation.
* Useful when applications need customer or consumer identity management.

**Example:** Allowing customers to sign in to an online shopping application.

### 28. AWS Directory Service

* Provides managed directory capabilities, including Microsoft Active Directory-related options.
* Helps applications and users integrate with directory-based authentication.
* Useful for organizations that need directory services for supported AWS workloads.

### 29. AWS Secrets Manager

* Stores and manages sensitive information such as database credentials, API keys, and passwords.
* Supports controlled access and secret rotation for supported integrations.
* Reduces the need to hardcode secrets in application source code.

**Best practice:** Retrieve secrets securely at runtime instead of committing them to GitHub.

### 30. AWS Systems Manager Parameter Store

* Stores configuration values and parameters.
* Supports plain-text and encrypted parameters.
* Can integrate with AWS KMS for encryption.
* Useful for application settings, environment configuration, and some secrets-management needs.

**Secrets Manager vs Parameter Store**

* Secrets Manager is purpose-built for managing secrets and supports rotation workflows.
* Parameter Store is useful for configuration data and parameter management, with encrypted storage available.

### 31. AWS Key Management Service (KMS)

* Creates and manages cryptographic keys.
* Integrates with many AWS services to encrypt data.
* Helps control who can use keys through permissions and policies.
* Supports encryption at rest for supported services.

### 32. AWS Certificate Manager (ACM)

* Provisions and manages supported TLS/SSL certificates.
* Helps secure connections between users and supported applications.
* Integrates with services such as Elastic Load Balancing and CloudFront, subject to certificate and regional requirements.

### 33. Amazon CloudWatch Logs

* Collects, stores, and provides access to application and system logs.
* Supports log groups, log streams, retention settings, and log queries.
* Helps troubleshoot application problems and investigate system behavior.

### 34. AWS CloudTrail

* Records AWS account activity and API events.
* Helps identify who performed an action, what happened, and when.
* Supports auditing, security investigations, and compliance workflows.

**CloudWatch vs CloudTrail**

* CloudWatch focuses on metrics, logs, alarms, and operational monitoring.
* CloudTrail records AWS API and account activity.

### 35. Amazon GuardDuty

* A managed threat-detection service.
* Analyzes supported data sources to identify suspicious activity and potential threats.
* Helps detect potentially compromised credentials, malicious activity, and other security risks.

### 36. Amazon Macie

* Helps discover and protect sensitive data in Amazon S3.
* Uses machine learning and pattern matching to identify sensitive information, such as certain forms of personally identifiable information.
* Helps organizations understand potential data exposure risks.

### 37. AWS WAF

* A web application firewall.
* Helps protect supported web applications from unwanted HTTP/HTTPS requests.
* Supports rules for filtering requests, including patterns associated with common web attacks.

### 38. AWS Shield

* Helps protect applications against Distributed Denial of Service (DDoS) attacks.
* AWS Shield Standard provides automatic protection for supported AWS services.
* AWS Shield Advanced provides additional protections and features under its applicable terms.

**WAF vs Shield**

* WAF filters web requests using configured rules.
* Shield focuses on DDoS protection.

### 39. AWS Security Hub

* Helps centralize security findings and assess security posture across supported AWS environments.
* Aggregates findings from supported AWS security services and integrations.
* Helps prioritize security issues and monitor compliance with supported standards.

---

## Practical Work — Learning Checklist

Mark each item only after completing it.

* [ ] Explore Elastic Beanstalk or CloudFormation.
* [ ] Review Amazon RDS and DynamoDB use cases.
* [ ] Explore CloudWatch Logs and CloudTrail.
* [ ] Review the purpose of major AWS security services.
* [ ] Map AWS services to common application requirements.
* [ ] Prepare the AWS service comparison sheet.
* [ ] Prepare the security services summary.
* [ ] Prepare the database services comparison.
* [ ] Prepare deployment approach notes.

## Key Takeaways

* CloudFront delivers content through caching; Global Accelerator improves global network routing.
* CloudFormation and CDK automate infrastructure creation.
* Elastic Beanstalk simplifies application deployment.
* RDS and Aurora support relational workloads; DynamoDB supports NoSQL workloads.
* Redshift is designed for data warehousing, while Athena queries data in supported sources such as S3.
* Organizations and Control Tower support multi-account governance.
* Systems Manager and AWS Config help manage and evaluate resources.
* Secrets Manager, KMS, and ACM help protect secrets, encryption keys, and certificates.
* CloudTrail supports auditing; CloudWatch supports operational monitoring.
* GuardDuty, Macie, WAF, Shield, and Security Hub address different security needs.


