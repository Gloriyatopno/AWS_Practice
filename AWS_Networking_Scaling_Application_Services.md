# AWS Networking, Scaling & Application Services

## Phase 2 — Networking, Scaling & Application Services

## 1. Introduction to AWS Networking

AWS networking services allow resources to communicate with each other, connect to the internet, and securely access applications and data.

Important AWS networking services include:

* Amazon VPC
* Amazon Route 53
* Elastic Load Balancing
* Amazon EC2 Auto Scaling
* AWS Site-to-Site VPN
* AWS Direct Connect
* AWS Transit Gateway
* AWS NAT Gateway

These services help build secure, scalable, and reliable cloud infrastructure.

---

## 2. Amazon VPC

Amazon Virtual Private Cloud (VPC) allows users to create a logically isolated network within AWS.

Resources such as EC2 instances can be launched inside a VPC.

### Important VPC Components

* **VPC:** A logically isolated network in AWS.
* **Subnet:** A smaller network range inside a VPC.
* **Route Table:** Determines where network traffic is directed.
* **Internet Gateway (IGW):** Allows communication between a VPC and the internet when routing and security settings permit it.
* **NAT Gateway:** Allows resources in private subnets to initiate connections to external networks without accepting unsolicited inbound internet connections.
* **Security Group:** A stateful virtual firewall associated with resources such as EC2 instances.
* **Network ACL (NACL):** A stateless firewall that controls inbound and outbound traffic at the subnet level.

### Basic VPC Structure

```text
AWS Region
    |
    └── VPC
         |
         ├── Public Subnet
         |     └── Web Server (EC2)
         |
         └── Private Subnet
               └── Application Server (EC2)
```

The exact architecture depends on the application's requirements.

---

## 3. Subnets

A subnet is a range of IP addresses within a VPC.

Subnets are associated with a specific Availability Zone.

### Public Subnet

A subnet is considered public when its route table provides a route to an Internet Gateway.

A resource generally also needs a suitable public IPv4 address or another supported internet connectivity method, along with appropriate security rules, to communicate directly with the internet.

**Common uses:**

* Public web servers
* Internet-facing load balancers
* NAT Gateways

### Private Subnet

A private subnet does not have a direct route to an Internet Gateway.

Resources in private subnets can use a NAT Gateway for certain outbound IPv4 internet connections, if the required routes and security rules are configured.

**Common uses:**

* Application servers
* Databases
* Internal services

### Public vs Private Subnets

| Public Subnet                                        | Private Subnet                                      |
| ---------------------------------------------------- | --------------------------------------------------- |
| Has a route to an Internet Gateway                   | Has no direct route to an Internet Gateway          |
| Can host internet-facing resources                   | Commonly hosts internal resources                   |
| May contain a public-facing web server               | Commonly contains application servers and databases |
| Requires suitable routing and security configuration | Can use a NAT Gateway for outbound internet access  |

---

## 4. IP Addresses in AWS

IP addresses identify resources on a network.

### Private IP Address

A private IP address is used for communication within private networks, such as a VPC.

Example:

```text
172.31.19.65
```

### Public IP Address

A public IP address can allow a resource to communicate over the internet when its network routes and security rules permit it.

### Elastic IP Address

An Elastic IP address is a static public IPv4 address allocated to an AWS account.

It can be associated with supported AWS resources and reassociated when necessary.

Elastic IP addresses may incur charges, including when they are not associated with a running resource. Check current AWS pricing before allocating one.

---

## 5. Internet Gateway and NAT Gateway

### Internet Gateway

An Internet Gateway connects a VPC to the internet.

It does not automatically make every resource in the VPC publicly accessible. Route tables, IP addressing, and security controls must also be configured appropriately.

### NAT Gateway

A NAT Gateway enables resources in a private subnet to initiate connections to external networks without allowing unsolicited inbound connections initiated from the internet.

For example, a private EC2 instance may need internet access to download software updates.

### Comparison

| Internet Gateway                                                     | NAT Gateway                                                           |
| -------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Enables internet connectivity for appropriately configured resources | Enables outbound connectivity from private networks                   |
| Used by public-subnet routing                                        | Commonly used by private-subnet routing                               |
| Does not replace security groups or NACLs                            | Does not provide general inbound internet access to private instances |

---

## 6. Security Groups

A Security Group acts as a virtual firewall for associated resources, such as EC2 instances.

It controls inbound and outbound traffic through rules.

### Important Characteristics

* Security Groups are stateful.
* They allow traffic based on configured rules.
* Inbound traffic is denied by default when no inbound rules permit it.
* Outbound traffic is allowed by default in a newly created default-rule configuration, but this can be changed.
* Rules can specify protocols, ports, and source or destination ranges.

### Example

A web server may use rules such as:

| Protocol | Port | Purpose                     |
| -------- | ---: | --------------------------- |
| HTTP     |   80 | Web traffic                 |
| HTTPS    |  443 | Secure web traffic          |
| SSH      |   22 | Remote Linux administration |

**Security best practice:** Avoid opening SSH or other administrative ports to everyone (`0.0.0.0/0`). Restrict access to trusted IP addresses or use a suitable managed access method.

---

## 7. Network Access Control Lists (NACLs)

A Network ACL is a security layer associated with a subnet.

It controls inbound and outbound traffic at the subnet level.

### Characteristics

* NACLs are stateless.
* Inbound and outbound rules are evaluated separately.
* Rules are evaluated in numerical order, starting with the lowest rule number.
* The first matching rule determines the result.
* A custom NACL can allow or deny traffic.

### Security Group vs NACL

| Security Group                                                  | Network ACL                                            |
| --------------------------------------------------------------- | ------------------------------------------------------ |
| Associated with network interfaces/resources                    | Associated with subnets                                |
| Stateful                                                        | Stateless                                              |
| Supports allow rules                                            | Supports allow and deny rules                          |
| Return traffic is automatically allowed for tracked connections | Return traffic must be permitted by the relevant rules |

Both provide important layers of network security.

---

## 8. Amazon Route 53

Amazon Route 53 is a scalable Domain Name System (DNS) web service.

DNS translates domain names into information that computers use to locate services.

For example:

```text
www.example.com
       |
       v
   Route 53
       |
       v
Web Application
```

### Route 53 Features

* Domain registration
* DNS record management
* Health checks
* DNS-based routing policies
* Integration with other AWS services

### Common Routing Policies

* **Simple routing:** Routes queries using a basic record configuration.
* **Weighted routing:** Distributes traffic according to assigned weights.
* **Latency-based routing:** Directs users toward resources offering lower network latency.
* **Failover routing:** Supports primary and secondary resource configurations.
* **Geolocation routing:** Routes according to the user's geographic location.
* **Geoproximity routing:** Routes according to the geographic location of users and resources, with optional bias adjustments.

Route 53 can help improve application availability and direct users to appropriate endpoints.

---

## 9. Scaling in AWS

Scaling means adjusting resources to meet workload requirements.

Applications may need more resources during busy periods and fewer resources during quieter periods.

### Vertical Scaling — Scaling Up

Vertical scaling means increasing or decreasing the capacity of an existing resource.

Example:

```text
Smaller EC2 Instance
        |
        v
Larger EC2 Instance
```

It may involve changing an EC2 instance type to obtain more CPU or memory.

### Horizontal Scaling — Scaling Out

Horizontal scaling means adding or removing instances or other resource units.

Example:

```text
       Load Balancer
        /    |    \
      EC2   EC2   EC2
```

Horizontal scaling can improve capacity and resilience when the application supports multiple instances.

### Comparison

| Vertical Scaling                                   | Horizontal Scaling                                        |
| -------------------------------------------------- | --------------------------------------------------------- |
| Changes the capacity of an existing resource       | Adds or removes resource instances                        |
| May require a restart or interruption              | Can support growth without relying on one larger instance |
| Has limits based on available instance sizes       | Capacity can grow across multiple instances               |
| Useful for workloads that scale well on one server | Useful for distributed and web applications               |

---

## 10. Amazon EC2 Auto Scaling

Amazon EC2 Auto Scaling automatically adjusts the number of EC2 instances in an Auto Scaling group according to configured settings and policies.

### Benefits

* Adds capacity when demand increases.
* Removes capacity when demand decreases.
* Helps maintain the desired number of instances.
* Supports application availability.
* Can replace unhealthy instances.

### Basic Flow

```text
Application Demand Increases
          |
          v
  Auto Scaling Policy
          |
          v
   More EC2 Instances
```

When demand decreases, an appropriate scaling policy can reduce the number of instances.

### Important Concepts

* **Minimum capacity:** The minimum number of instances allowed.
* **Desired capacity:** The intended number of instances.
* **Maximum capacity:** The maximum number of instances allowed.
* **Launch template:** Defines settings for launching instances.
* **Scaling policy:** Determines when and how capacity changes.
* **Health checks:** Help identify unhealthy instances.

---

## 11. Elastic Load Balancing (ELB)

Elastic Load Balancing distributes incoming traffic across multiple targets, such as EC2 instances.

It can help improve application availability and distribute workloads.

### Basic Flow

```text
       Users
         |
         v
   Load Balancer
      /     \
     v       v
   EC2-1   EC2-2
```

### Main Load Balancer Types

* **Application Load Balancer (ALB):** Operates at the application layer and supports HTTP/HTTPS traffic routing.
* **Network Load Balancer (NLB):** Operates at the transport layer and supports high-performance TCP, UDP, and related traffic use cases.
* **Gateway Load Balancer (GWLB):** Helps deploy and scale virtual network appliances.
* **Classic Load Balancer:** An older load balancer type for applications using the previous generation of ELB.

### Benefits

* Distributes incoming traffic.
* Supports health checks.
* Helps avoid relying on a single application instance.
* Works with Auto Scaling to support changing demand.

---

## 12. Scaling Policies

Scaling policies determine how Auto Scaling responds to changes in workload.

### Target Tracking Scaling

Adjusts capacity to maintain a target metric, such as average CPU utilization.

### Step Scaling

Adjusts capacity according to the size of a metric breach and configured thresholds.

### Scheduled Scaling

Changes capacity at known times.

Example: Increasing capacity before a predictable busy period.

### Simple Scaling

Uses a single scaling adjustment based on a CloudWatch alarm, with a cooldown period affecting subsequent scaling actions.

The appropriate policy depends on how predictable the workload is and how quickly capacity needs to change.

---

## 13. Serverless Computing

Serverless computing allows developers to run applications without directly managing the underlying servers.

AWS still uses servers, but AWS manages much of the infrastructure provisioning and maintenance.

### Benefits

* Reduced server management.
* Automatic scaling for supported services.
* Pay-for-use pricing models for many services.
* Integration with other AWS services.

### Examples

* AWS Lambda
* Amazon API Gateway
* AWS Step Functions
* Amazon EventBridge

Serverless does not mean that an application has no infrastructure or no configuration requirements.

---

## 14. AWS Lambda

AWS Lambda is a serverless compute service that runs code in response to events.

Developers upload code and configure how it is invoked.

### Common Triggers

* API Gateway requests
* S3 events
* EventBridge rules
* Queue messages from supported services

### Example

```text
S3 Object Uploaded
        |
        v
   AWS Lambda
        |
        v
Process the Object
```

### Benefits

* No need to manage servers directly.
* Supports event-driven applications.
* Scales according to incoming requests within service limits.
* Integrates with many AWS services.

### Common Use Cases

* Processing uploaded files.
* Creating APIs.
* Automating cloud operations.
* Performing scheduled tasks.
* Responding to application events.

---

## 15. Amazon API Gateway

Amazon API Gateway is a managed service for creating, publishing, securing, monitoring, and managing APIs.

It can provide an entry point for applications to invoke backend services.

### Example Architecture

```text
Client Application
        |
        v
  API Gateway
        |
        v
    Lambda
        |
        v
   Response
```

### Benefits

* Provides API endpoints.
* Supports authentication and authorization options.
* Integrates with Lambda and other supported backends.
* Provides monitoring and throttling capabilities.

### Use Cases

* Mobile application backends.
* Web application APIs.
* Serverless applications.
* APIs for accessing business services.

---

## 16. AWS Step Functions

AWS Step Functions is a workflow service that coordinates multiple tasks into a defined process.

It can integrate with Lambda and other AWS services.

### Example

```text
Start Workflow
      |
      v
Validate Order
      |
      v
Process Payment
      |
      v
Update Order
      |
      v
End Workflow
```

### Benefits

* Coordinates multiple steps.
* Supports workflow branching and error handling.
* Makes complex application processes easier to manage.
* Provides a visual representation of workflows.

### Use Cases

* Order processing.
* Approval workflows.
* Data processing pipelines.
* Multi-step application automation.

---

## 17. Amazon EventBridge

Amazon EventBridge is a serverless event bus service that routes events from AWS services, applications, and supported external sources to configured targets.

### Example

```text
AWS Event
    |
    v
EventBridge Rule
    |
    v
Lambda Function
```

### Use Cases

* Responding to changes in AWS resources.
* Triggering automated tasks.
* Connecting event-driven applications.
* Running scheduled tasks.

EventBridge helps applications react to events without requiring every component to communicate directly with every other component.

---

## 18. Event-Driven Architecture

Event-driven architecture is a design in which components communicate or trigger work through events.

An event represents something that has happened, such as a file upload or an order being created.

### Example

```text
Customer Places Order
         |
         v
     Order Event
         |
         v
   EventBridge
      /    \
     v      v
  Lambda   Notification
```

### Benefits

* Reduces direct dependencies between components.
* Supports asynchronous processing.
* Helps connect different services.
* Can make applications easier to extend.

---

## 19. VPC Peering

VPC Peering allows two VPCs to communicate privately using their private IP addresses.

The VPCs can belong to the same or different AWS accounts, subject to the applicable configuration and permissions.

### Example

```text
VPC A  <---- Peering ---->  VPC B
```

### Important Points

* VPC CIDR ranges must not overlap for standard VPC peering.
* Routes must be configured in the relevant route tables.
* Security rules must allow the intended traffic.
* VPC peering does not provide transitive routing through another peered VPC.

### Use Case

Connecting an application in one VPC to a service in another VPC.

---

## 20. AWS Site-to-Site VPN

AWS Site-to-Site VPN creates an encrypted connection between an on-premises network and an AWS network over the internet.

It is commonly used to connect an organization's local network to AWS.

### Basic Flow

```text
On-Premises Network
         |
         v
   VPN Connection
         |
         v
       AWS VPC
```

### Use Cases

* Hybrid cloud connectivity.
* Secure communication with AWS resources.
* Connecting corporate networks to cloud infrastructure.

---

## 21. AWS Direct Connect

AWS Direct Connect provides a dedicated network connection from an organization’s premises to AWS.

It can help provide more consistent network performance than internet-based connectivity, depending on the design.

### Benefits

* Dedicated network connectivity.
* Can reduce dependence on internet-based paths.
* Supports hybrid network architectures.
* Can help meet bandwidth and network-performance requirements.

### Site-to-Site VPN vs Direct Connect

| Site-to-Site VPN                                       | Direct Connect                                                        |
| ------------------------------------------------------ | --------------------------------------------------------------------- |
| Uses an encrypted connection over the internet         | Uses a dedicated network connection                                   |
| Can often be set up more quickly                       | Usually requires coordination and provisioning                        |
| Useful for many smaller or flexible connectivity needs | Useful for consistent, higher-capacity network connectivity           |
| Encryption is provided by the VPN tunnel               | Private connectivity alone does not automatically encrypt all traffic |

---

## 22. AWS Transit Gateway

AWS Transit Gateway connects multiple VPCs and on-premises networks through a central network hub.

### Example

```text
        VPC A
          |
          v
   Transit Gateway
      /       \
     v         v
   VPC B    On-Premises
```

### Benefits

* Centralizes network connectivity.
* Simplifies large multi-VPC architectures.
* Supports connections to on-premises networks.
* Reduces the need to manage many individual connections.

---

## 23. AWS Outposts

AWS Outposts extends AWS infrastructure and services to supported on-premises locations.

It is designed for workloads that need to run close to local systems or meet specific data residency and low-latency requirements.

### Use Cases

* Hybrid cloud applications.
* Workloads that must remain on-premises.
* Applications requiring low-latency access to local systems.
* Organizations integrating on-premises systems with AWS services.

---

## 24. Networking Services Comparison

| Service                | Main Purpose                                             |
| ---------------------- | -------------------------------------------------------- |
| Amazon VPC             | Creates an isolated virtual network                      |
| Subnet                 | Divides a VPC address range                              |
| Internet Gateway       | Provides a route between a VPC and the internet          |
| NAT Gateway            | Enables outbound internet access from private subnets    |
| Security Group         | Controls traffic at the resource/network-interface level |
| Network ACL            | Controls traffic at the subnet level                     |
| Route 53               | DNS and domain routing                                   |
| Elastic Load Balancing | Distributes incoming traffic                             |
| EC2 Auto Scaling       | Adjusts EC2 instance capacity                            |
| VPC Peering            | Connects two VPCs privately                              |
| Site-to-Site VPN       | Encrypted connectivity over the internet                 |
| Direct Connect         | Dedicated network connection to AWS                      |
| Transit Gateway        | Central hub for network connectivity                     |
| Outposts               | Extends AWS infrastructure to on-premises locations      |

---

## 25. Application Services Comparison

| Service                | Main Purpose                       |
| ---------------------- | ---------------------------------- |
| AWS Lambda             | Runs code in response to events    |
| Amazon API Gateway     | Creates and manages APIs           |
| AWS Step Functions     | Coordinates multi-step workflows   |
| Amazon EventBridge     | Routes events to targets           |
| EC2 Auto Scaling       | Automatically adjusts EC2 capacity |
| Elastic Load Balancing | Distributes traffic across targets |

---

## 26. Practical Work

### VPC Exploration

**Status: Learning task**

Topics to explore in the AWS Management Console:

* Open the VPC service.
* Identify the VPC used by the EC2 instance.
* Review the VPC's CIDR range.
* Identify available subnets and their Availability Zones.
* Review the associated route tables.
* Identify routes to an Internet Gateway where configured.

### Security Groups

**Status: Learning task**

Review the Security Group associated with the EC2 instance.

Understand:

* Inbound rules.
* Outbound rules.
* Allowed protocols and ports.
* Source IP ranges.
* Why administrative ports should not be unnecessarily exposed to the internet.

### AWS Lambda

**Status: Learning task**

Review the AWS Lambda console and understand:

* Functions.
* Runtime options.
* Triggers.
* Execution roles.
* Monitoring and logs.

A simple test function can be created if the task requires practical execution. Check potential charges and permissions before creating resources.

### API Gateway

**Status: Concept reviewed**

API Gateway can expose an API endpoint and integrate with a backend such as Lambda.

Understand the request flow:

```text
Client → API Gateway → Lambda → Response
```

### Auto Scaling and Load Balancing

**Status: Concepts reviewed**

Understand how Auto Scaling changes EC2 capacity and how a load balancer distributes traffic between healthy targets.

Practical creation of these resources should only be marked completed if it was actually performed.

---

## 27. Key Takeaways

* A VPC provides an isolated virtual network in AWS.
* Subnets divide a VPC's IP address range.
* Public and private subnet behavior depends on routing and resource configuration.
* Internet Gateways and NAT Gateways have different purposes.
* Security Groups are stateful, while Network ACLs are stateless.
* Route 53 provides DNS and routing features.
* Vertical scaling increases the capacity of a resource.
* Horizontal scaling adds or removes resource instances.
* EC2 Auto Scaling adjusts the number of EC2 instances.
* Elastic Load Balancing distributes incoming traffic.
* Lambda supports serverless, event-driven computing.
* API Gateway manages API endpoints.
* Step Functions coordinates multi-step workflows.
* EventBridge routes events to configured targets.
* VPC Peering, VPN, Direct Connect, and Transit Gateway support different network connectivity needs.
* AWS Outposts extends AWS infrastructure to supported on-premises environments.

---
