## VProfile Web Application on AWS

### About VProfile

VProfile is a multi-tier web application written in Java by [hkhcoder](https://github.com/hkhcoder/vprofile-project.git). 

The architecture of the project services is shown below:

![](https://miro.medium.com/v2/resize:fit:1189/1*cP0KJ_UOjHhUHCdxSDIsCw.png)

#### About the Project

* Host and run the application on AWS cloud for production

* Deployment strategies:

  - Lift & Shift:
 
### AWS Services

* EC2 instances: VMs used for Tomcat, RabbitMQ, Memcache, MySQL servers

* ELB (Load Balancer): Replacement for the NGinx LB server

* Autoscaling: Automation for VM scaling

* S3/EFS storage: Shared storage

* Route 53: Private DNS service

### Architecture of AWS services

The AWS services used in the project:

* Application Load Balancer

* Set of EC2 instances: for Tomcat, Memcache, Rabbit MQ and MySQL

* EC2 security groups

* Amazon S3 bucket to store software artifacts

* DNS Private Zones and Amazon Certificate Manager were NOT included this time

![](AWS-architecture.png)


### Flow of Execution

1. Get into AWS Account

2. Create Key Pairs for our instances

3. Create Security Groups for LB, Tomcat and backend services

4. Launch instances with user data: bash scripts

5. Update IP to name mapping in route 53

6. Build application from source code

7. Upload to S3 bucket

8. Download artifact to Tomcat EC2 instance

9. Setup ELB with HTTPS (Certificate from Amazon Certificate Manager)

10. Map ELB endpoint to website name in GoDaddy's DNS

