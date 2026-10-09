# AWS Architecture, Billing, Migration & Final Revision

## Section 14 — Architecting for the Cloud

### 1. AWS Well-Architected Framework

The AWS Well-Architected Framework helps design and operate secure, reliable, efficient, and cost-effective cloud applications.

It has six pillars:

| Pillar                 | Purpose                             | Example                                     |
| ---------------------- | ----------------------------------- | ------------------------------------------- |
| Operational Excellence | Run and improve systems effectively | Automate deployments                        |
| Security               | Protect systems and data            | Use IAM and MFA                             |
| Reliability            | Recover from failures               | Use backups and multiple Availability Zones |
| Performance Efficiency | Use resources efficiently           | Select suitable EC2 instance types          |
| Cost Optimization      | Avoid unnecessary expenses          | Stop unused EC2 instances                   |
| Sustainability         | Reduce environmental impact         | Use resources efficiently                   |

### 2. Cloud Architecture Principles

**Design for failure:** Assume that individual components can fail and plan recovery mechanisms.

**Decouple components:** Keep application components independent so one failure does not affect the entire application.

**Implement elasticity:** Automatically adjust resources according to demand.

**Use automation:** Automate infrastructure creation, deployment, and routine operations.

**Think in parallel:** Process independent tasks simultaneously when appropriate.

**Use managed services:** Reduce the amount of infrastructure you need to maintain.

**Implement security at every layer:** Apply access controls, encryption, monitoring, and network security.

### 3. High Availability vs. Fault Tolerance

* **High availability:** Minimizes downtime by keeping the application available despite some failures.
* **Fault tolerance:** Allows a system to continue operating with little or no interruption when a component fails.

Example: An application running across multiple Availability Zones can remain available if one zone experiences a failure.

### 4. Scalability vs. Elasticity

* **Scalability:** The ability to handle increased workload by adding resources.
* **Elasticity:** The ability to automatically increase or decrease resources as demand changes.

Example: EC2 Auto Scaling can add instances when demand rises and remove them when demand falls.

---

## Section 15 — Accounts, Billing and Support

### 5. AWS Pricing Fundamentals

AWS pricing depends on the service, usage, region, and selected pricing model.

Common pricing approaches include:

* **Pay-as-you-go:** Pay for the resources you consume.
* **Commitment-based pricing:** Receive discounted rates in exchange for eligible usage commitments.
* **Spot pricing:** Use spare EC2 capacity at discounted rates, with the possibility of interruption.
* **Data transfer charges:** Some data transfers incur charges depending on the service and transfer direction.
* **Storage pricing:** Pay according to storage amount, storage class, requests, and other applicable factors.

Always check the current AWS pricing page and estimate costs before deploying resources.

### 6. EC2 Pricing Options

| Option              | Description                                                           | Suitable for                                     |
| ------------------- | --------------------------------------------------------------------- | ------------------------------------------------ |
| On-Demand           | Pay for compute usage without a long-term commitment                  | Short-term workloads and testing                 |
| Reserved Instances  | Discounted pricing for eligible EC2 usage with a term commitment      | Predictable, long-running workloads              |
| Savings Plans       | Lower prices in exchange for a usage commitment                       | Consistent compute usage                         |
| Spot Instances      | Use spare capacity at discounted prices; instances can be interrupted | Flexible, interruption-tolerant jobs             |
| Dedicated Hosts     | Physical servers dedicated to your use                                | Certain licensing and compliance needs           |
| Dedicated Instances | Instances running on hardware dedicated to a single customer          | Workloads requiring dedicated hardware isolation |

**Remember:** Reserved Instances and Savings Plans are commitment-based pricing options, not simply different virtual machine types.

### 7. Pricing for Other AWS Services

* **Amazon S3:** Storage, requests, data retrieval, and applicable data transfer.
* **Amazon RDS:** Database instance usage, storage, backups, and data transfer where applicable.
* **AWS Lambda:** Requests and execution duration, subject to applicable pricing and free allowances.
* **Amazon CloudFront:** Data transfer, requests, and other applicable features.
* **Amazon DynamoDB:** Depending on configuration, on-demand requests or provisioned capacity, plus storage and other features.
* **Amazon EBS:** Provisioned storage and certain additional capabilities.

### 8. AWS Support Plans

AWS offers different levels of technical support and operational guidance. Available plans and their features can change.

* **Basic Support:** Included at no additional cost; provides account, billing, and service-related resources with limited technical support.
* **Developer Support:** Aimed at development and testing workloads; availability and features depend on the current plan.
* **Business Support:** Designed for production workloads requiring broader technical support.
* **Enterprise-level Support:** Offers more comprehensive guidance and support for organizations with significant operational needs.

Check the current AWS Support Plans page for exact plan names, eligibility, response times, and prices.

### 9. Consolidated Billing and AWS Organizations

AWS Organizations lets businesses manage multiple AWS accounts centrally.

**Consolidated billing** combines charges from organization accounts into a single bill and can help eligible accounts share certain volume-based pricing benefits.

Benefits:

* Centralized billing management.
* Separate accounts for teams or environments.
* Policies to help control account usage.
* Better organization-wide cost visibility.

**Important:** Consolidated billing does not automatically make every account's resources free. Charges still depend on usage and applicable pricing rules.

### 10. AWS Cost Management Tools

| Tool                      | Purpose                                                     |
| ------------------------- | ----------------------------------------------------------- |
| AWS Pricing Calculator    | Estimate the cost of a planned architecture                 |
| AWS Cost Explorer         | Analyze historical spending and usage trends                |
| AWS Budgets               | Set budget and usage thresholds and configure alerts        |
| AWS Cost and Usage Report | Obtain detailed billing and usage data                      |
| AWS Billing Dashboard     | Review billing information and charges                      |
| AWS Trusted Advisor       | Receive recommendations, including cost optimization checks |

**Best practice:** Create a budget, configure alerts, review Cost Explorer regularly, and delete resources you no longer need.

---

## Section 16 — Migration, Machine Learning and More

### 11. AWS Migration and Transfer Services

| Service                              | Purpose                                                                 |
| ------------------------------------ | ----------------------------------------------------------------------- |
| AWS Application Migration Service    | Move eligible servers into AWS with minimal changes                     |
| AWS Database Migration Service (DMS) | Migrate databases and support ongoing data replication                  |
| AWS Migration Hub                    | Track migration progress across supported tools                         |
| AWS DataSync                         | Transfer data between supported storage systems                         |
| AWS Transfer Family                  | Transfer files using supported protocols such as SFTP                   |
| AWS Snow Family                      | Use physical devices for certain edge computing and data transfer needs |

**Example:** A company moving a database to AWS may use AWS DMS, while a company migrating servers may use AWS Application Migration Service.

### 12. AWS Migration Strategies

Common migration strategies are often summarized as the **7 Rs**:

1. **Retire:** Remove applications that are no longer needed.
2. **Retain:** Keep applications where they are for now.
3. **Rehost:** Move an application with minimal changes.
4. **Relocate:** Move supported infrastructure with minimal architectural changes.
5. **Repurchase:** Replace the application with a different product, often a SaaS solution.
6. **Replatform:** Make limited changes to benefit from cloud services.
7. **Refactor or Re-architect:** Redesign the application to take greater advantage of cloud capabilities.

Example: Moving a virtual machine to EC2 with minimal changes is rehosting. Moving an application to a managed database with limited changes may be replatforming.

### 13. AWS Machine Learning Services

| Service             | Purpose                                                |
| ------------------- | ------------------------------------------------------ |
| Amazon SageMaker AI | Build, train, and deploy machine learning models       |
| Amazon Rekognition  | Analyze images and videos                              |
| Amazon Comprehend   | Analyze text using natural language processing         |
| Amazon Transcribe   | Convert speech into text                               |
| Amazon Polly        | Convert text into speech                               |
| Amazon Translate    | Translate text between languages                       |
| Amazon Lex          | Build conversational interfaces and chatbots           |
| Amazon Textract     | Extract text and structured information from documents |

**Example:** An application that converts recorded speech into text can use Amazon Transcribe.

### 14. End User Computing

AWS end-user computing services provide users with access to desktops and applications hosted in the cloud.

* **Amazon WorkSpaces:** Provides managed virtual desktops.
* **Amazon AppStream 2.0:** Streams desktop applications to users through a web browser.

Example: A company can provide employees with virtual desktops without requiring all applications and data to be stored on their personal computers.

### 15. AWS IoT Core

AWS IoT Core lets connected devices securely communicate with AWS and other devices.

Common uses:

* Smart home devices.
* Industrial sensors.
* Connected vehicles.
* Remote equipment monitoring.
* Collecting data from internet-connected devices.

Example: A temperature sensor can send readings to AWS IoT Core so an application can monitor conditions remotely.

---

## 17. Final AWS Service Selection Guide

| Requirement                        | AWS service or feature            |
| ---------------------------------- | --------------------------------- |
| Virtual servers                    | Amazon EC2                        |
| Object storage                     | Amazon S3                         |
| Block storage for EC2              | Amazon EBS                        |
| Shared file storage                | Amazon EFS                        |
| Managed relational database        | Amazon RDS                        |
| Serverless NoSQL database          | Amazon DynamoDB                   |
| Data warehouse                     | Amazon Redshift                   |
| Content delivery                   | Amazon CloudFront                 |
| Global traffic performance         | AWS Global Accelerator            |
| Infrastructure as code             | AWS CloudFormation                |
| Application deployment platform    | AWS Elastic Beanstalk             |
| Serverless functions               | AWS Lambda                        |
| API management                     | Amazon API Gateway                |
| Monitoring and metrics             | Amazon CloudWatch                 |
| API and account activity auditing  | AWS CloudTrail                    |
| User access permissions            | AWS IAM                           |
| Threat detection                   | Amazon GuardDuty                  |
| Web application protection         | AWS WAF                           |
| DDoS protection                    | AWS Shield                        |
| Encryption key management          | AWS KMS                           |
| Cost estimation                    | AWS Pricing Calculator            |
| Cost analysis                      | AWS Cost Explorer                 |
| Budget alerts                      | AWS Budgets                       |
| Server migration                   | AWS Application Migration Service |
| Database migration                 | AWS DMS                           |
| Machine learning model development | Amazon SageMaker AI               |

---

## 18. Final Revision Checklist

### Architecture

* [ ] Review the six Well-Architected pillars.
* [ ] Understand high availability, fault tolerance, scalability, and elasticity.
* [ ] Review cloud architecture best practices.

### Billing and Support

* [ ] Compare EC2 pricing options.
* [ ] Review the AWS Support Plans.
* [ ] Understand AWS Organizations and consolidated billing.
* [ ] Review Pricing Calculator, Cost Explorer, and Budgets.

### Migration and Other Services

* [ ] Compare migration and data transfer services.
* [ ] Review the seven migration strategies.
* [ ] Revise machine learning service use cases.
* [ ] Understand WorkSpaces, AppStream 2.0, and IoT Core.

### Learning Evidence

* [ ] Complete the remaining course quizzes.
* [ ] Review incorrect quiz answers.
* [ ] Record practical activities actually completed.
* [ ] Commit the final revision notes to GitHub.
* [ ] Update the GitHub progress notes.
* [ ] Post the daily Slack update.

## Key Takeaway

AWS architecture focuses on building secure, reliable, efficient, and cost-effective systems. Billing tools help estimate and control spending, while migration and specialized services help organizations move workloads to AWS and build new cloud-based solutions.
