# AWS Deployment Approach Notes

## 1. What Is Deployment?

Deployment is the process of making an application available for users by setting up the required code, infrastructure, configuration, and services.

## 2. Common AWS Deployment Approaches

### A. Manual Deployment

* Resources are created and configured manually through the AWS Console or CLI.
* Suitable for learning and small experiments.
* Can be time-consuming and prone to configuration errors.

### B. Infrastructure as Code (IaC)

* Infrastructure is defined in reusable code or templates.
* AWS CloudFormation uses JSON or YAML templates.
* AWS CDK allows infrastructure to be defined using programming languages.
* Makes infrastructure easier to reproduce and maintain.

### C. Managed Application Deployment

* AWS Elastic Beanstalk simplifies application deployment and infrastructure management.
* Developers focus mainly on application code and configuration.
* AWS manages much of the underlying environment, depending on the chosen configuration.

### D. CI/CD Deployment

* Continuous Integration (CI) automates building and testing code changes.
* Continuous Delivery or Deployment (CD) automates preparing or releasing application changes.
* AWS CodePipeline can coordinate a delivery workflow with supported source, build, test, and deployment services.

## 3. Choosing a Deployment Approach

| Requirement                                                               | Possible Approach     |
| ------------------------------------------------------------------------- | --------------------- |
| Learning AWS through the Console                                          | Manual deployment     |
| Repeatable infrastructure                                                 | CloudFormation or CDK |
| Deploying a supported web application with less infrastructure management | Elastic Beanstalk     |
| Automating builds and releases                                            | CI/CD pipeline        |
| Delivering website content globally                                       | CloudFront            |
| Investigating application latency                                         | AWS X-Ray             |

## 4. Example Web Application Deployment

A typical web application may use the following architecture:

1. Developers write and store application code.
2. A CI/CD pipeline builds and tests the code.
3. CloudFormation or CDK creates the required infrastructure when appropriate.
4. The application is deployed to a suitable service, such as Elastic Beanstalk or EC2.
5. Amazon RDS or DynamoDB stores application data, depending on the requirements.
6. Security Groups and IAM permissions restrict access.
7. CloudWatch collects logs and metrics.
8. CloudTrail records AWS account activity.
9. CloudFront can deliver website content globally when needed.

Not every application needs every service. Select services based on requirements, complexity, security, and cost.

## 5. Deployment Best Practices

* Use repeatable deployment procedures.
* Test changes before releasing them to production.
* Apply least-privilege IAM permissions.
* Avoid storing credentials in source code.
* Monitor application health after deployment.
* Configure backups and recovery options where needed.
* Plan how to roll back unsuccessful releases.
* Review expected costs before creating resources.
* Clean up unused resources to avoid unnecessary charges.

## 6. Learning Checklist

* [ ] Understand manual deployment.
* [ ] Review Infrastructure as Code.
* [ ] Compare CloudFormation and CDK.
* [ ] Understand Elastic Beanstalk.
* [ ] Review the purpose of CI/CD.
* [ ] Map deployment services to application requirements.

## Key Takeaway

Choose an AWS deployment approach based on how much control, automation, and infrastructure management the application requires. Combine deployment tools with suitable database, security, and monitoring services to build a reliable solution.
