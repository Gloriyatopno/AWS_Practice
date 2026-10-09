# AWS Service Comparison Sheet

## 1. Deployment and Networking Services

| Service                | Main Purpose                                      | Common Use Case                                  |
| ---------------------- | ------------------------------------------------- | ------------------------------------------------ |
| Amazon CloudFront      | Content delivery network (CDN)                    | Deliver website content globally                 |
| AWS Global Accelerator | Improves global network routing                   | Improve application availability and performance |
| AWS CloudFormation     | Infrastructure as Code using JSON/YAML            | Create repeatable AWS infrastructure             |
| AWS CDK                | Define infrastructure using programming languages | Automate infrastructure using code               |
| AWS Elastic Beanstalk  | Simplifies application deployment                 | Deploy web applications                          |
| AWS CodeBuild          | Builds and tests code                             | Automate software builds                         |
| AWS CodeDeploy         | Automates application deployments                 | Deploy application updates                       |
| AWS CodePipeline       | Automates delivery workflows                      | Build CI/CD pipelines                            |
| AWS X-Ray              | Traces application requests                       | Find errors and performance bottlenecks          |

## 2. Database and Analytics Services

| Service                   | Type                            | Common Use Case                              |
| ------------------------- | ------------------------------- | -------------------------------------------- |
| Amazon RDS                | Relational database             | Applications using SQL tables                |
| Amazon Aurora             | Relational database engine      | High-performance relational workloads        |
| Amazon DynamoDB           | NoSQL database                  | High-scale, low-latency applications         |
| Amazon Redshift           | Data warehouse                  | Business intelligence and analytics          |
| Amazon EMR                | Big data processing             | Process large datasets using Spark or Hadoop |
| Amazon ElastiCache        | In-memory caching               | Speed up frequently accessed data            |
| Amazon Athena             | Serverless SQL query service    | Query supported data sources such as S3      |
| AWS Glue                  | Data integration and cataloging | Prepare and transform data                   |
| Amazon Kinesis            | Streaming data services         | Process real-time data streams               |
| Amazon DocumentDB         | Document database               | Document-oriented application workloads      |
| Amazon Neptune            | Graph database                  | Analyze connected data and relationships     |
| Amazon OpenSearch Service | Search and analytics            | Search, log analysis, and observability      |
| AWS Lake Formation        | Data lake governance            | Manage access to data lakes                  |

## 3. Management and Governance Services

| Service              | Main Purpose                           | Common Use Case                              |
| -------------------- | -------------------------------------- | -------------------------------------------- |
| AWS Organizations    | Manage multiple AWS accounts           | Separate development and production accounts |
| AWS Control Tower    | Establish multi-account governance     | Set up a governed AWS environment            |
| AWS Systems Manager  | Operate and manage resources           | Run commands and manage supported servers    |
| AWS Service Catalog  | Manage approved IT products            | Provide standardized resources               |
| AWS Config           | Track resource configurations          | Check compliance with configuration rules    |
| AWS Trusted Advisor  | Recommendations for AWS environments   | Identify optimization opportunities          |
| AWS Health Dashboard | Service and account health information | Check relevant AWS events and issues         |

## 4. Security and Identity Services

| Service                         | Main Purpose                          | Common Use Case                                  |
| ------------------------------- | ------------------------------------- | ------------------------------------------------ |
| AWS IAM                         | Manage AWS identities and permissions | Control access to AWS resources                  |
| Amazon Cognito                  | Application user authentication       | Add sign-in to web and mobile apps               |
| AWS Directory Service           | Managed directory capabilities        | Integrate with directory-based authentication    |
| AWS Secrets Manager             | Manage secrets                        | Store and rotate database credentials            |
| Systems Manager Parameter Store | Store parameters and configuration    | Manage application settings                      |
| AWS KMS                         | Manage cryptographic keys             | Encrypt supported data and control key use       |
| AWS Certificate Manager         | Manage TLS/SSL certificates           | Secure supported application connections         |
| Amazon CloudWatch Logs          | Collect and analyze logs              | Troubleshoot applications                        |
| AWS CloudTrail                  | Record AWS account/API activity       | Audit who did what and when                      |
| Amazon GuardDuty                | Threat detection                      | Identify suspicious activity                     |
| Amazon Macie                    | Discover sensitive data in S3         | Identify potential sensitive-data exposure       |
| AWS WAF                         | Filter web requests                   | Protect web applications from common web attacks |
| AWS Shield                      | DDoS protection                       | Help protect applications from DDoS attacks      |
| AWS Security Hub                | Centralize security findings          | Review security posture and findings             |

## 5. Architecting, Migration and Other Services

| Service                              | Main Purpose                                      | Common Use Case                             |
| ------------------------------------ | ------------------------------------------------- | ------------------------------------------- |
| AWS Well-Architected Framework       | Architecture best practices                       | Review cloud workloads                      |
| AWS Cost Explorer                    | Analyze AWS costs and usage                       | Understand spending trends                  |
| AWS Budgets                          | Set cost and usage alerts                         | Monitor spending against a budget           |
| AWS Migration Hub                    | Track supported migration activities              | Coordinate migration progress               |
| AWS Application Migration Service    | Migrate supported servers to AWS                  | Lift-and-shift server migration             |
| AWS Database Migration Service (DMS) | Migrate databases                                 | Move data between supported databases       |
| AWS Snow Family                      | Physical data transfer and edge computing options | Transfer large datasets or work at the edge |
| Amazon SageMaker AI                  | Build, train, and deploy machine learning models  | Develop machine learning applications       |
| Amazon WorkSpaces                    | Managed virtual desktops                          | Provide remote desktop environments         |
| AWS IoT Core                         | Connect and manage IoT devices                    | Collect data from connected devices         |

## 6. Quick Service Selection Guide

* **Deliver website content worldwide:** CloudFront
* **Improve global application routing:** Global Accelerator
* **Create infrastructure repeatedly:** CloudFormation or CDK
* **Deploy a web application with less infrastructure management:** Elastic Beanstalk
* **Store structured relational data:** RDS or Aurora
* **Store flexible NoSQL data:** DynamoDB
* **Analyze large datasets using a warehouse:** Redshift
* **Query data in S3 with SQL:** Athena
* **Transform and catalog data:** AWS Glue
* **Manage multiple AWS accounts:** Organizations
* **Evaluate resource configuration compliance:** AWS Config
* **Store application secrets:** Secrets Manager
* **Manage encryption keys:** KMS
* **Audit AWS API activity:** CloudTrail
* **Collect application logs:** CloudWatch Logs
* **Detect potential threats:** GuardDuty
* **Discover sensitive data in S3:** Macie
* **Filter web requests:** WAF
* **Protect against DDoS attacks:** Shield

## Key Takeaway

Choose an AWS service based on the requirement, such as deployment, data storage, analytics, governance, security, or cost management. Several services can work together to build a complete application.
