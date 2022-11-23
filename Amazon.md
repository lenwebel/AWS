## Regions And Zones

Local zones - Close to large population industry centres.

Wavelength zones - Compute, Storage services within 5g networks specifically for low latency.

Direct Connect - direct to AWS bypassing the Internet. locations worldwide

Cloudfront - Webservice like a CDN edge locations and regional edge caches speeds up content delivery regional edge caches.

## Compute Services

Develop deploy scale compute services

EC2 Compute – webservice.
EC2 auto scale uses triggers to scale.
ELB (elastic load balancing)
EC2 Container Services run on Docker Containers, managed cluster on EC2 instance or Fargate.
Fargate – serverless PAYG compute engine compatible with EKS (elastic Kubernetes service)
EKS – managed Kubernetes service which makes it to run Kubernetes run on EC2 and fargate, it manages Kubernes
Lambda - serverless computing.

# COMPUTE EC2

## Benefits of EC2

- `Elasticity`: can automatically scale up and down.  
- `Control`: same as any machine  
- `Flexibility`: choice of instance type’s operating systems, machine size etc.  
- `Integrated`: with most AWS services.  
- `Reliable`.  
- `Secure`.  
- `Cost Effective`.  
- `Easy` to get started.  

## EC2 instance types  (Hardware configuration)

1. `General Purpose` – diverse workloads
2. `Compute Optimised` – Hi performance processors
3. `Memory Optimised` like data processing in mem
4. `Accelerated Computing`: Data science operations, GPU workloads etc, hardware accelerators or co-processors
5. `Storage Optimised`: storage intensive workloads high disk IO’s

## EC2 Scaling

- Launch new instances in advance of peak periods  
- Use Monitoring to programmatically scale out  
- Automatically scale in

### EC2 Autoscaling group  

- Automatically adjusts resource capacity  
- Define which zone to scale to.  
- Specify minimum 2 subnets.  

### EC2 Autoscaling Instance Types

- Spot instance
- On demand;
- Both

**Properties that define scaling and instances.**
Minimum  
Maximum  
Desired Capacity. >= min, <= max

## Elastic Load Balancing

Automaticall distributes traffix across multiple EC2 instances.
Health checks to ensure instances are healthy.
ELB are highly available across multiple AZ’s.
ELB are scalable.
ELB can handle encryption

### Types of Elastic Load Balancers

1. Application load balancer  
2. Network load balancer  
3. Gateway forward traffic to virtual appliances in AWS marketplace.

---

## Summary of definitions

---
> `AMAZON MACHINE IMAGES` Software configuration template used for EC2 Instances.  
> found on Amazon Marketplace, User Community, AWS or custom User AMI’s  
  
> `VPC`  
> virtual private cloud  
---

# STORAGE

## Amazon Elastic Block Store (EBS)

- Replicated on creation
- Persist independently from instance.
- Used like a physsical hard drive.
- Automatically replicated
- Attached to any instance in the same AZ
- One EBS volume  to one EC2 instance
- One instance to many EBS volumes
- EBS volumes retain data after EC2 instance is terminated.
- Point in time snapshots, 1gb to 16tb allocated in 1gb increments.

## Amazon Simple Storage Service S3

- Generally used for datalakes / big data etc.
  - Backup and storage
  - Application hosting
  - Media hosting
  - Software delivery for download
- Highly scalable
- 11-9s durability, 4-9s availability

### Storage Classes

- `Amazon S3 Standard`: frequently accessed data, low latency, high throughput, multi zone
- `Amazon S3 Standard-IA:` infrequently accessed data, lower per GB storage price and lower per GB retrieval fee. multi zone 99.9% availability
- `Amazon S3 One Zone-IA`: infrequently accessed data, lower per GB storage price and lower per GB retrieval fee. single zone 99% availability, secondary backup data.
- `Amazon S3 Glacier`: archival data, low cost,  99.9% availability
  - `Amazon S3 Glacier` Instant: archival data, low cost, 1-5 minutes retrieval time
  - `Amazon S3 Glacier` Flexible: archival data, low cost
  - `Amazon S3 Glacier` Deep Archive: archival data, lowest cost
- `Amazon S3 Intelligent` Tiering: automatically moves data between S3 Standard and S3 Standard-IA based on access patterns.

### Storage Summary and definitions

> `11-9s`: 99.999999999%  
> `4-9s`: 99.99%  
> `EBS`: Amazon Elastic Block Store, persistant block storage volumes for use with EC2 instances.  
> `S3`: Simple Storage Service  
> `S3 Glacier`: Data archiving and backup service  
> `Storage Gateway`: Hybrid cloud storage service integrated cloud storage with on-site workloads.
> `EFS`: Elastic File System, File storage for EC2 instances  
> `FSx`: File System for Windows, File storage for widely used systems

## Amazon Database Services

### Database Service Types

- `Amazon Relational Database Service (RDS)`: managed relational database service, MySQL, Oracle, SQL Server, PostgreSQL, MariaDB, Aurora
- `Amazon DynamoDB`: NoSQL database service, fully managed, fast and flexible, single digit millisecond latency, 99.99% availability, 99.999999999% durability, 25TB storage, 400k read / 200k write capacity units.
- `Amazon Redshift`: Data warehouse service, fully managed, petabyte scale, 10x faster than other data warehouses, 1/10th the cost, 99.9% availability, 99.999999999% durability, 160TB storage, 500TB data transfer in/out per month.
- `Amazon ElastiCache`: Managed in-memory data store service, Memcached, Redis, 99.9% availability, 99.999999999% durability, 20TB storage, 20GB data transfer in/out per month.
- `Amazon Neptune`: Graph database service, fully managed, fast and reliable, 99.99% availability, 99.999999999% durability, 15TB storage, 1000 read / 1000 write capacity units.
- `Amazon Aurora`: MySQL and PostgreSQL compatible relational database engine, 5x faster than MySQL, 3x faster than PostgreSQL, 3 copies of data across 3 AZ’s, 6 copies across 3 regions.

### PRO's of RDS

- Easy to setup, manage and maintain.
- Push Button high availability.
- Reduce undifferentiated heavy lifting
- Scale up and down
- Automatic backups and recovery

### PRO's of databases on EC2

- Full control of OS
- More Control / flexibility
- Full control of database sofware and its additional features.

# Networking Services

- `VPC` virtual private cloud (network), logically isolated section of the AWS cloud, allows you to launch AWS resources in a virtual network that you define.
- `Security Groups` Control access to instances
- `Network Access Control Lists` Control access to subnets
- `Amazon Route 53` Domain name system (DNS) web service, highly available and scalable cloud Domain Name System (DNS) web service

## VPC

- Network layer for AWS resources resembling a traditional network.  
- `Subnet`: a range of addresses in a `VPC`  
- `NACL` Network access control lists: limit access to subnets.
- `Security groups` act as a firewall for a VPC
- `VPC`'s automatically comes with a default security group
- `Flow logs` capture network traffic for a Network interfaces, subnet or VPC and store it in CloudWatch Logs.
- `Host based firewall` operating system firewalls or third party software.

### Initialising a VPC

- Build a VPC
- Assign the VPC an IP address range
- Configure public and private  subnets within the larger network
- Secure subnets using Network ACL's
- More security at instance level using security groups

# Security

## Infrastructure Protection

- `AWS Network firewall`
- `AWS WAF` Web Application Firewall
- AWS Shield: DDoS protection
  - `AWS Shield Standard` 24/7 protection
  - `AWS Shield Advanced` 24/7 protection + 24/7 response time
- `AWS Firewall Manager` centrally manage and monitor AWS WAF rules across accounts and applications.

## identity and access management

### Manage access to AWS sevices and resources

- Create and manage users and groups
- Fine grained access control to AWS resources
- Multi-factor authentication
- Analyse access.
- Integration with coroporate directories, federated access etc.

### Services

- `AWS IAM` Identity and Access Management
- `AWS Single Sign On` SSO
- `AWS Organizations` Organise multiple AWS accounts
- `AWS Resource Access Manager` Share AWS resources across AWS accounts
- `AWS Directory Service` Managed Microsoft AD, Simple AD, AD Connector
- `AWS Cognito` User sign up, sign in, and access control

## Detection

- `Amazon GuardDuty` Detect threats and anomalies
- `Amazon Inspector` Assess applications for vulnerabilities
- `AWS CloudTrail` Record API calls
- `AWS Security Hub` Centralised view of security alerts
- `AWS Config` Record resource configurations
- `AWS IoT Device Defender` Monitor security of IoT devices

## Data Protection

- `Amazon Macie` Discover, classify, and protect sensitive data
- `AWS CloudHSM` Hardware security module
- `AWS Secrets Manager` Securely store and manage secrets
- `AWS Key Management Service` KMS
- `AWS Certificate Manager` Securely provision, manage, and deploy public and private SSL/TLS certificates

## Incident Response
- `Amazon Detective` Investigate security incidents
- `CloudEndure Disaster Recovery` DRaaS

## Compliance

Asset inventory, privileged access management, data protection, incident response, security monitoring, security posture management, vulnerability management.

AWS is Continuously audited and certified by accreddited bodies across the globe.

### Assurance Programs

Cerifications and attestations, Laws Regulations and privacy, Alignments and frameworks

### Sharing information with clients relevant to clients

- Industry certifications
- Security and control practices
- Compliance reports directly under NDA

- `AWS Artifact` Compliance reports
- `AWS Audit Manager` Automate compliance checks