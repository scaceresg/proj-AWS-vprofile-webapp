## Deploying VProfile App on AWS Cloud: Lift & Shift Strategy

### About the Project

* Multi-tier web application stack: *VProfile*

* Host and run on AWS cloud for production

* Lift & Shift strategy is used

**Scenario**: Suppose there are many application services running on physical/virtual machines and all the workload is located in a local datacenter.

Several teams are required in this current situation: Virtualisation, data center operations team, monitoring team, system administration team, etc.

**The Problem of the Current State**:

* Managing teams and data gets complex

* Even more when you want to scale up or down

* Huge costs for procuring and maintaining these resources (Upfront CAPEX and regular OPEX)

* Most processes are manual and difficult to automate

* Time consuming processes

**The Solution**: A Cloud Computing Setup!

A Cloud Setup allows:

* Avoiding CAPEX 

* Paying as you go (Like electricity bills)

* Consuming IaaS (Infrastructure as a Service)

* Flexible 

* Elastic in nature: we can scale up or down

* Control of costs

* Automation to avoid human errors and save time

### AWS Services 

* EC2 instances: VMs used for Tomcat, RabbitMQ, Memcache, MySQL servers

* ELB (Load Balancer): Replacement for the NGinx LB server

* Autoscaling: Automation for VM scaling

* S3/EFS storage: Shared storage

* Route 53: Private DNS service

**Objective**

* Flexible infrastructure

* Use the Pay as we go model

* Modernise the app effectively

* Use Infrastructure as a Code (IaaC)

### Architecture of AWS services

The AWS sources we will be using in the project are:

* Amazon Certificate Manager: Used for https certificate

* Application Load Balancer

* Set of EC2 instances: for Tomcat, Memcache, Rabbit MQ and MySQL

* Security groups: 3

* Amazon Route 53 for DNS Private Zones

* Amazon S3 bucket to store software artifacts

![](AWS-architecture.png)

### Flow of Execution

1. Login to AWS Account

2. Create Key Pairs for our instances

3. Create Security Groups for LB, Tomcat and backend services

4. Launch instances with user data: bash scripts

5. Update IP to name mapping in route 53

6. Build application from source code

7. Upload to S3 bucket

8. Download artifact to Tomcat EC2 instance

9. Setup ELB with HTTPS (Certificate from Amazon Certificate Manager)

10. Map ELB endpoint to website name in GoDaddy's DNS

11. Verify

12. Build Auto Scaling Group for Tomcat instances