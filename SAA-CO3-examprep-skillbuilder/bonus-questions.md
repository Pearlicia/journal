
1. A company will host a static website within an Amazon S3 bucket. The website will serve millions of users globally, and the company wants to minimize data transfer costs.

What should a solutions architect do to ensure costs are kept to a minimum?

A
Implement an AWS Auto Scaling group for the website to ensure it grows with use.

Incorrect. AWS Auto Scaling is not applicable for a static website that is hosted on Amazon S3.

For more information about how to use Amazon S3 to host a static website, see Hosting a Static Website Using Amazon S3.


B
Use Cross-Region Replication to copy the website to an additional S3 bucket in a different AWS Region.

Incorrect. The use of S3 Cross-Region Replication would increase overall costs. You can use S3 Cross-Region Replication to locate data in multiple locations, typically for regulatory or compliance reasons.

For more information about S3 Cross-Region Replication, see Replicating Objects.


C
Move the website to large compute-optimized Amazon EC2 instances with on-demand pricing.

Incorrect. The addition of EC2 instances, particularly large compute-optimized EC2 instances, would increase overall costs.

For more information about C5.large Amazon EC2 instance prices, see Amazon EC2 On-Demand Pricing.


D
Create an Amazon CloudFront distribution, with the S3 bucket as the origin server.

Correct. The use of CloudFront can be more cost-effective if your users access your objects frequently. At higher usage, the cost for CloudFront data transfer to the internet is lower than the cost for Amazon S3 data transfer to the internet. In addition, downloads are faster with CloudFront than with Amazon S3 alone because your objects are stored closer to your users.

For more information about how to use CloudFront with Amazon S3, see Using Various Origins with CloudFront Distributions.

2. A solutions architect needs to design a secure environment for AWS resources that are being deployed to Amazon EC2 instances in a VPC. The solution should support a three-tier architecture that consists of web servers, application servers, and a database cluster. The VPC needs to allow resources in the web tier to be accessible from the internet with only the HTTPS protocol.

Which combination of actions would meet these requirements? (Select TWO.)

A
Attach Amazon API Gateway to the VPC. Create private subnets for the web, application, and database tiers.

Incorrect. API Gateway is an AWS service that creates, publishes, maintains, monitors, and secures REST, HTTP, and WebSocket APIs. This solution does not meet any of the requirements.

For more information about API Gateway, see What Is Amazon API Gateway?


B
Attach an internet gateway to the VPC. Create public subnets for the web tier. Create private subnets for the application and database tiers.

Correct. Only the web tier needs to be in public subnets. The application and database tiers should be in private subnets.

For more information about public and private subnets, see How Amazon VPC Works.


C
Attach a virtual private gateway to the VPC. Create public subnets for the web and application tiers. Create private subnets for the database tier.

Incorrect. A virtual private gateway is the Amazon VPC side of a VPN connection and does not allow requests over the public internet. The application tier is not required to be directly accessible from the internet, so the application tier should use private subnets.

For more information about virtual private gateways, see Amazon VPC FAQs.

For more information about public and private subnets, see How Amazon VPC Works.


D
Create a web server security group that allows all traffic from the internet. Create an application server security group that allows requests from only the Amazon API Gateway on the application port. Create a database cluster security group that allows TCP connections from the application security group on the database port only.

Incorrect. The requirement is to limit internet traffic to HTTPS for the web tier. API Gateway is not the appropriate solution for these requirements. API Gateway is an AWS service that creates, publishes, maintains, monitors, and secures REST, HTTP, and WebSocket APIs. This solution does not meet any of the requirements.

For more information about API Gateway, see What Is Amazon API Gateway?


E
Create a web server security group that allows HTTPS requests from the internet. Create an application server security group that allows requests from the web security group only. Create a database cluster security group that allows TCP connections from the application security group on the database port only.

Correct. Making the web tier public subnets allows for greater access to the resource while protecting it from traffic on unrequired ports. Restricting traffic to the application and database tiers protects it from accidental and malicious access and ensures that each tier is accessed only through secure communication with the previous tier.

For more information about securing traffic in a VPC, see Control Traffic to Resources Using Security Groups.


3. A solutions architect notices an abnormal amount of network traffic coming from an Amazon EC2 instance. The traffic is determined to be malicious, and the destination needs to be determined.

What tool can the solutions architect use to identify the destination of the malicious network traffic?

A
Turn on AWS CloudTrail and filter the logs

Incorrect. CloudTrail monitors action taken by an IAM user, an IAM role, or an AWS service through API calls. However, CloudTrail does not provide the monitoring of the destination of network communication.

For more information about API call auditing in AWS, see What Is AWS CloudTrail?


B
Turn on VPC Flow Logs and filter the logs

Correct. VPC Flow Logs is a feature that gives you the ability to capture information about the IP traffic that goes to and from network interfaces in a VPC.

For more information about VPC Flow Logs basics, see Logging IP Traffic Using VPC Flow Logs.


C
Consult the AWS Health Dashboard

Incorrect. AWS Health Dashboard provides visibility into the performance and availability of the AWS services running in your account, as well as alerts that are automatically invoked by changes in the health of those services. However, AWS Health Dashboard does not report network details like network traffic.

For more information about AWS Health Dashboard, see Getting started with your AWS Health Dashboard – Your account health.


D
Filter the logs from Amazon CloudWatch

Incorrect. CloudWatch does not provide the monitoring of the destination of network communication.

For more information about the functions of CloudWatch, see Amazon CloudWatch Features.

4. A SysOps administrator wants to automate the deployment of new SSL/TLS certificates to web servers. The administrator wants a centralized way to keep track and manage the deployed certificates.

Which AWS service can the administrator use to meet these requirements?

A
AWS Key Management Service (AWS KMS)

Incorrect. AWS KMS is a managed service that gives you the ability to create and control AWS KMS keys, the encryption keys used to encrypt your data at rest in services such as Amazon S3. AWS KMS keys are compatible for encrypting the traffic by using SSL/TLS.

For more information about AWS KMS, see AWS Key Management Service.


B
Run Command, a capability of AWS Systems Manager

Incorrect. With Run Command, you can remotely and securely manage the configuration of your managed instances. A managed instance is any Amazon EC2 instance or on-premises machine in your hybrid environment that you can configure for Systems Manager. Run Command gives you the ability to automate common administrative tasks and perform one-time configuration changes at scale. Although Run Command would help with the deployment of the certificates, Run Command does not perform ongoing management of those deployed certificates.

For more information about Run Command, see AWS Systems Manager Run Command.


C
AWS Certificate Manager (ACM)

Correct. ACM is a service that gives you the ability to provision, manage, and deploy public and private SSL/TLS certificates for use with AWS services and your internal connected resources. SSL/TLS certificates are used to secure network communications and establish the identity of websites over the internet and resources on private networks. ACM removes the time-consuming manual process of purchasing, uploading, and renewing SSL/TLS certificates.

For more information about ACM, see AWS Certificate Manager.


D
Parameter Store, a capability of AWS Systems Manager

Incorrect. Parameter Store provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data. You can reference Systems Manager parameters in your scripts, commands, SSM documents, and configuration and automation workflows by using the unique name that you specified when you created the parameter. Parameter Store cannot store certificates for SSL/TLS connections.

For more information about Parameter Store, see AWS Systems Manager Parameter Store.


5. A solution architect must create a data store location that will be able to handle different file formats of unknown sizes. The data must be highly available and protected from being accidentally deleted. 

What solution meets the requirements and is the MOST cost-effective?


A
Deploy an Amazon S3 bucket and activate Cross-Region Replication.

Incorrect. This solution would require extra cost to duplicate the bucket in a secondary Region. Amazon S3 Cross-Region Replication requires that object versioning also be activated. However, versioning itself is enough to meet the requirements.

For more information see about Amazon S3 pricing, see Amazon S3 Pricing.


B
Deploy an Amazon DynamoDB table and activate global tables.

Incorrect. The requirements include a data store that is compatible with multiple file types. DynamoDB does not support multiple file types and has a maximum item size of 400 KB.

For more information about DynamoDB compatible files, see Supported Data Types for DynamoDB Mapper for Java.


C
Deploy a database by using Amazon RDS and configure a Multi-AZ deployment for that database.

Incorrect. The requirements include a data store that is compatible with multiple unknown file types. A database on Amazon RDS is a SQL database and not a general data store.

For more information about compatible data types on Amazon RDS, see Data Types.


D
Deploy an Amazon S3 bucket and enable object versioning.

Correct. Versioning-enabled buckets can help you recover objects from accidental deletion or overwrite. For example, if you delete an object, Amazon S3 inserts a delete marker instead of removing the object permanently. The delete marker becomes the current object version. If you overwrite an object, you get a new object version in the bucket. You can restore the previous version.

For more information about object versioning in Amazon S3, see Using Versioning in S3 Buckets.

6. A company is migrating its on-premises application to AWS and refactoring the application's design. The design will consist of frontend Amazon EC2 instances that receive requests, backend EC2 instances that process the requests, and a message-queuing service that addresses decoupling the application. A solutions architect has been informed that a key aspect of the application is that requests are processed in the order in which they are received.

Which AWS service should the solutions architect use to decouple the application?

A
Amazon Simple Queue Service (Amazon SQS) FIFO queue

Correct. Amazon SQS FIFO queues process messages in the order they are received.

For more information about Amazon SQS queue types, see Amazon SQS Features. 


B
Amazon Simple Queue Service (Amazon SQS) standard queue

Incorrect. Although Amazon SQS standard queue is a valid queue type, it is based on best-effort ordering and cannot ensure messages are processed in the order they are received.

For more information about Amazon SQS queue types, see Amazon SQS Features. 


C
Amazon Simple Notification Service (Amazon SNS)

Incorrect. Amazon SNS gives you the ability to modernize your applications and decouple them into smaller independent components. However, Amazon SNS does not address the queuing of messages. Amazon SNS uses a publish and subscribe model rather than polling.

For more information about Amazon SNS, see Amazon SNS. 


D
Amazon Kinesis

Incorrect. Kinesis gives you the ability to collect, process, and analyze data. However, Kinesis is better suited for ingesting streaming real-time data.

For more information about Kinesis, see Amazon Kinesis.


7. A gaming company is experiencing exponential growth. On multiple occasions, customers have been unable to access resources. To keep up with the increased demand, management is considering deploying a cloud-based solution. The company wants a solution that can match on-premises resilience of multiple data centers and robust enough to withstand the increased growth activity.

Which configuration should a solutions architect implement to meet these requirements?

A VPC that is configured with an Elastic Load Balancing (ELB) Network Load Balancer that targets an Amazon EC2 Auto Scaling group consisting of Amazon EC2 instances that span two Availability Zones.

Correct. The ELB Network Load Balancer is capable of handling millions of requests per second while maintaining ultra-low latency. Combined with an Auto Scaling group, the network ELB can handle volatile traffic patterns. Setting the Auto Scaling group targets across multiple AZs will make this solution highly available.

For more information about Auto Scaling, see Attach a Load Balancer to Your Auto Scaling Group.

For more information about planning your network topology for high availability, see REL02-BP01 Use Highly Available Network Connectivity for Your Workload Public Endpoints.


B
A VPC that is configured with an Elastic Load Balancing (ELB) Application Load Balancer that targets an Amazon EC2 Auto Scaling group consisting of Amazon EC2 instances in one Availability Zone.

Incorrect. You can achieve high availability by deploying application resources across multiple Availability Zones. This solution includes only one Availability Zone. 

For more information about planning your network topology for high availability, see REL02-BP01 Use Highly Available Network Connectivity for Your Workload Public Endpoints.


C
Multiple Amazon EC2 instances that are configured within peered VPCs across two Availability Zones.

Incorrect. Peered VPCs provide communication between the two VPCs. However, peered VPCs do not address the requirement for high availability of the application.

For more information about planning your network topology for high availability, see REL02-BP01 Use Highly Available Network Connectivity for Your Workload Public Endpoints.

For more information about VPC peering, see What Is VPC Peering?


D
A VPC that is configured with an Elastic Load Balancing (ELB) Application Load Balancer that targets an Amazon EC2 Auto Scaling group consisting of Amazon EC2 instances that span two AWS Regions.

Incorrect. The targets for Application Load Balancers must be within a single Region.

For more information about adding AZs to a load balancer, see Add and Remove Availability Zones.

8. A company is deploying a production portal application on AWS. The database tier runs on a MySQL database. The company requires a highly available database solution that maximizes ease of management.

How can the company meet these requirements?

A
Deploy the database on multiple Amazon EC2 instances that are backed by Amazon Elastic Block Store (Amazon EBS) across multiple Availability Zones. Schedule periodic EBS snapshots.

Incorrect. This solution does not maximize ease of management. The deployment of databases directly on EC2 instances requires manual intervention during failover, manual database deployment and setup, and maintenance of the operating system and database engine.

For more information about database deployment, see MySQL on AWS Deployment Options.


B
Use Amazon RDS with a Single-AZ deployment. Schedule periodic database snapshots.

Incorrect. The company is building production workloads and needs a highly available architecture. A Single-AZ deployment is not highly available.

For more information about Multi-AZ deployment, see Multi-AZ Deployments for High Availability.


C
Use Amazon RDS with a Multi-AZ deployment. Schedule periodic database snapshots.

Correct. Amazon RDS with a Multi-AZ deployment provides automatic failover with minimum manual intervention and is highly available.

For more information about Multi-AZ deployment, see Multi-AZ Deployments for High Availability.


D
Use Amazon DynamoDB with a DynamoDB Accelerator (DAX) cluster. Create periodic on-demand backups.

Incorrect. This solution does not maximize ease of management. DynamoDB is a NoSQL database, and the company's existing database is running on MySQL. You can store structured data in DynamoDB, but the process would require additional planning.

For more information about DynamoDB, see What Is Amazon DynamoDB?

For more information about structured data on DynamoDB, see Best Practices for Modeling Relational Data in DynamoDB.

9. A company requires operating system permission on a relational database server.

What should a solutions architect suggest as a configuration for a highly available database architecture?

A
Multiple Amazon EC2 instances in a database replication configuration that uses two Availability Zones

Correct. EC2 instances will allow operating system access, and spanning two Availability Zones ensures high availability.

For more information on database best practices, see Web Application Hosting in the AWS Cloud.


B
A database installed on a single Amazon EC2 instance in an Availability Zone

Incorrect. If the company runs the database on a single EC2 instance, the architecture will have a single point of failure. The architecture would need a second instance to be highly available.

For more information about reliability, see Design Principles.


C
Amazon RDS in a Multi-AZ configuration with Provisioned IOPS

Incorrect. This solution meets the requirement for high availability. However, this solution does not provide access to the operating system.

For more information about when to use EC2 instances, see Amazon EC2 for Oracle. 


D
Multiple Amazon EC2 instances in a replication configuration that uses a placement group

Incorrect. The company can achieve EC2 instance redundancy by running multiple EC2 instances in a placement group. However, placement groups are in a single Availability Zone, which is not highly available.

For more information about placement groups, see Placement Groups.


10. A solutions architect must create a disaster recovery (DR) solution for a company's business-critical applications. The DR site must reside in a different AWS Region than the primary site. The solution requires a recovery point objective (RPO) in seconds and a recovery time objective (RTO) in minutes. The solution also requires the deployment of a completely functional but scaled-down version of the applications.

Which DR strategy will meet these requirements?

A
Multi-site active-active

Incorrect. Multi-site active-active has an RPO and an RTO in real time and is considered a hot standby. Although this solution will meet the RPO and RTO requirements, multi-site active-active is not a scaled-down version of the applications and will be more expensive than other options.


B
Backup and restore

Incorrect. Backup and restore is the least aggressive approach for DR. With this solution, no data and applications are on standby. This solution has an RPO and an RTO in hours, which does not meet these requirements.


C
Pilot light

Incorrect. Pilot light uses fewer running resources, keeping only critical applications and data running and available. The RPO is in minutes, and the RTO is in hours, which does not meet these requirements.


D
Warm standby

Correct. With warm standby fully working at low capacity, all components run at a low capacity. The RPO is in seconds, and the RTO is in minutes.

For more information about the various DR strategies, see Plan for Disaster Recovery (DR).

11. A financial services company is migrating its multi-tier web application to AWS. The application architecture consists of a fleet of web servers, application servers, and an Oracle database. The company must have full control over the database's underlying operating system. The database must be highly available.

Which approach should a solutions architect use for the database tier to meet these requirements?

A
Migrate the database to an Amazon RDS for Oracle DB Single-AZ DB instance.

Incorrect. Amazon RDS is a fully managed AWS relational database service, and a single Availability Zone is not highly available. This deployment does not meet full control of the database operating system nor high availability.

For more information about RDS for Oracle, see Amazon RDS for Oracle.

For more information about high availability, see Amazon EC2 for Oracle.


B
Migrate the database to an Amazon RDS for Oracle Multi-AZ DB instance.

Incorrect. Amazon RDS is a fully managed AWS relational database service. Although this option provides high availability, it does not give the company full control of the database operating system.

For more information about RDS for Oracle, see Amazon RDS for Oracle.


C
Migrate to Amazon EC2 instances in two Availability Zones. Install Oracle and configure the instances to operate as a cluster.

Correct. This solution provides the company with full control of the database operating system. The solution also provides high availability.

For more information about high availability, see Amazon EC2 for Oracle.


D
Migrate to Amazon EC2 instances in a single Availability Zone. Install Oracle and configure the instances to operate as a cluster.

Incorrect. This solution provides the company with full control of the database operating system. However, a single AZ does not provide high availability.

For more information about Amazon EC2 for Oracle and high availability, see Amazon EC2 for Oracle.


12. A company used Amazon EC2 Spot Instances for a demonstration that is now complete. A solutions architect must remove the Spot Instances to stop them from incurring cost.

What should the solutions architect do to meet this requirement?

A
Cancel the Spot request. Terminate the Spot Instances.

Correct. To remove the Spot Instances, the appropriate steps are to cancel the Spot request and then to terminate the Spot Instances.

For more information about the termination of Spot Instances, see Terminate a Spot Instance.


B
Cancel the Spot request only.

Incorrect. If the only action you take is to cancel the Spot request, the running instances will not be terminated automatically. These instances will continue to run and will incur additional cost.


C
Terminate the Spot Instances only.

Incorrect. When Spot Instances are terminated, new instances will launch until the Spot request is canceled.

D
Terminate the Spot Instances. Cancel the Spot request.

Incorrect. When Spot Instances are terminated, new instances will launch until the Spot request is canceled.


13. A company is deploying an environment for a new data processing application. The application will be frequently accessed by 20 different departments across the globe seeking to run analytics. The company plans to charge each department for the cost of that department's access.

Which solution will meet these requirements with the LEAST effort?

A
Amazon Aurora with global databases. Each department will query a database in a different Region, and the Region is tagged in the billing console.

Incorrect. Aurora is not a suitable solution for analytics because it is structured more for transactions and lookups than analytic processing. In addition, each replica in a Region will charge per instance hour, so this solution can quickly get expensive. This solution is also not scalable because there are a finite number of Regions.

For more information about Aurora, see What Is Amazon Aurora? 


B
Amazon RDS for PostgreSQL, with read replicas for each department. Each department will query the read replica tagged for their department in the billing console.

Incorrect. RDS for PostgreSQL is not a suitable solution for analytics because it is structured more for transactions and lookups than analytic processing. In addition, this is not a scalable solution because there is a maximum of 5 read replicas for each database.

For more information about RDS for PostgreSQL, see Amazon RDS for PostgreSQL.


C
Amazon Redshift, with clusters set up for each department. Each department will query the cluster tagged for their department in the billing console.

Incorrect. Although Amazon Redshift is an excellent analytic engine, Amazon Redshift requires additional cost and effort to duplicate clusters for multiple departments. The best practice would be to use data sharing across clusters for cost allocation.

For more information about data sharing, see Getting Started Accessing Data in Other Amazon Redshift Clusters.


D
Amazon Athena with workgroups set up for each department. Each department will query through the workgroup tagged for their department in the billing console.

Correct. Athena gives you the ability to make data queries in Amazon S3. Workgroups are purpose-built for cost allocation.

For more information about Athena workgroups, see Using Workgroups to Control Query Access and Costs.


14. A company's application gives users the ability to upload image files to an Amazon S3 bucket. These files are accessed frequently for the first 30 days. After 30 days, these files are rarely accessed. However, the files need to be durably stored and available immediately upon request. A solutions architect needs to configure a lifecycle policy that minimizes the overall cost while meeting the application requirements.

Which solution will meet these requirements?

A
Configure a lifecycle policy to move the files to S3 Standard-Infrequent Access (S3 Standard-IA) after 30 days.

Correct. Using a lifecycle policy to move data to S3 Standard-IA satisfies all application requirements and provides the lowest cost option.

For more information about S3 Standard-IA, see Amazon S3 Storage Classes.


B
Configure a lifecycle policy to move the files to S3 Glacier after 30 days.

Incorrect. Although storing these files on S3 Glacier is a low-cost option, this solution does not satisfy the requirement that the files be immediately available.

For more information about S3 Glacier data retrievals, see Amazon S3 FAQs.


C
Configure a lifecycle policy to move the files to S3 Glacier Deep Archive after 30 days.

Incorrect. Although storing these files on S3 Glacier Deep Archive is a low-cost option, this solution does not satisfy the requirement that the files be immediately available.

For more information about S3 Glacier Deep Archive data retrievals, see Amazon S3 FAQs.


D
Configure a lifecycle policy to move the files to S3 One Zone-Infrequent Access (S3 One Zone-IA) after 30 days.

Incorrect. S3 One Zone-IA is intended for use cases with infrequently accessed data that can be recreated if needed. For example, you can store secondary backup copies of on-premises data. Additionally, you can store data that is already replicated in another AWS Region for compliance or disaster recovery purposes. This makes One Zone-IA an unsuitable solution for this durable storage need.

For more information about S3 One Zone-IA, see Amazon S3 Storage Classes.

15. After reviewing the cost optimization checks in AWS Trusted Advisor, a team finds that it has 10,000 Amazon Elastic Block Store (Amazon EBS) snapshots in its account that are more than 30 days old. The team has determined that it needs to implement better governance for the lifecycle of its resources.

Which actions should the team take to automate the lifecycle management of the EBS snapshots with the LEAST effort? (Select TWO.)

A
Create and schedule a backup plan with AWS Backup.

Correct. The team wants to automate the lifecycle management of EBS snapshots. AWS Backup is a centralized backup service that automates backup processes for application data across AWS services in the AWS Cloud, helping you meet business and regulatory backup compliance requirements. AWS Backup provides a central place where you can configure and audit the AWS resources you want to back up, automate backup scheduling, set retention policies, and monitor all recent backup and restore activity.

For more information about AWS Backup, see What Is AWS Backup?


B
Copy the EBS snapshots to Amazon S3, and then create lifecycle configurations in the S3 bucket.

Incorrect. Although this solution meets the technical requirement, it does not meet the requirement for the least effort. To copy EBS snapshots and set up lifecycle policies on the S3 bucket, the team would need to provide manual effort or create scripts that would need to be hosted somewhere.

For more information about how to copy EBS snapshots, see Copy an Amazon EBS Snapshot.


C
Use Amazon Data Lifecycle Manager.

Correct. With Amazon Data Lifecycle Manager, you can manage the lifecycle of your AWS resources through lifecycle policies. Lifecycle policies automate operations on specified resources. The team requires lifecycle management for EBS snapshots. Amazon Data Lifecycle Manager supports EBS volumes and snapshots.

For more information about Amazon Data Lifecycle Manager, see Amazon Data Lifecycle Manager.


D
Use a scheduled event in Amazon EventBridge and invoke AWS Step Functions to manage the snapshots.

Incorrect. Although this solution meets the technical requirement, it does not meet the requirement for the least effort. The team would need to give more effort to automate the lifecycle management by using scheduled events in EventBridge and Step Functions than by using AWS Backup or Amazon Data Lifecycle Manager.


E
Schedule and run backups in AWS Systems Manager.

Incorrect. Although this solution meets the technical requirement, it does not meet the requirement for the least effort. This solution requires more effort than the use of AWS Backup or Amazon Data Lifecycle Manager.

16. A company is using an Amazon S3 bucket to store archived data for audits. The company needs long-term storage for the data. The data is rarely accessed and must be available for retrieval the next business day.

After a quarterly review, the company wants to reduce the storage cost for the S3 bucket. A solutions architect must recommend the most cost-effective solution to store the archived data.

Which solution will meet these requirements?

A
Store the data on an Amazon EC2 instance that uses Amazon Elastic Block Store (Amazon EBS).

Incorrect. Storage of data on EBS volumes would be much more expensive than the current Amazon S3 solution. Amazon EBS is for block storage. Amazon S3 is for object storage, including data that can be accessed frequently or infrequently. In this case, the company needs object storage.

For more information about cloud storage on AWS, see Cloud Storage on AWS.

For more information about Amazon EBS, see Amazon Elastic Block Store (EBS).


B
Store the data in S3 Glacier Flexible Retrieval.

Correct. Of these options, S3 Glacier Flexible Retrieval is the most cost-effective solution. S3 Glacier Flexible Retrieval is an ideal fit for archival data that does not need to be frequently accessed or modified.

For more information about S3 Glacier Flexible Retrieval, see What Is Amazon S3 Glacier?

For more information about S3 Glacier retrieval options, see Retrieving S3 Glacier Archives.


C
Use an S3 Lifecycle configuration rule to move the data to S3 Standard-Infrequent Access (S3 Standard-IA).

Incorrect. You can transition objects to another storage class, such as S3 Standard-IA. However, this option is not the most cost-effective solution.

For more information about Amazon S3 storage classes, see Amazon S3 Storage Classes.

For more information about S3 Lifecycle configuration, see Managing Your Storage Lifecycle.


D
Store the data in another S3 bucket in a different AWS Region.

Incorrect. Storage of data in another Region can help reduce storage cost because the cost to store data varies by Region. However, this option is not the most cost-effective solution because the Amazon S3 storage class still needs to change to a less expensive option.

For more information about Amazon S3 pricing, see Amazon S3 Pricing.


17. A prediction process requires access to a trained model that is stored in an Amazon S3 bucket. The process takes a few seconds to process an image and make a prediction. The process is not overly resource-intensive, does not require any specialized hardware, and takes less than 512 MB of memory to run.

What is the MOST cost-effective compute solution for this use case?

A
Amazon Elastic Container Service (Amazon ECS)

Incorrect. With Amazon ECS, you can launch and stop your container-based applications by using simple API calls. However, this solution would be more costly than Lambda functions for this use case.

For more information about Amazon ECS, see What Is Amazon Elastic Container Service?


B
Amazon EC2 Spot Instances

Incorrect. Spot Instances are not a suitable solution as the backend of any service because you cannot ensure compute capacity will be available when you need it.

For more information about Spot Instances, see Spot Instances.


C
AWS Elastic Beanstalk

Incorrect. Elastic Beanstalk is a simple and fast way to deploy applications on AWS. However, you still would need EC2 instances to run the application. The instances would be more costly than Lambda functions for this use case.

For more information about Elastic Beanstalk, see AWS Elastic Beanstalk Documentation.


D
AWS Lambda functions

Correct. With Lambda functions, you can run code without provisioning or managing servers. You pay only for the compute time that you consume. There is no charge when your code is not running. Therefore, Lambda is the most cost-effective solution for this use case.

For more information about Lambda, see What Is AWS Lambda?

18. A hospital is migrating from another cloud provider to AWS and wants to modernize as they migrate. The hospital has containerized applications that run on tablets. During spikes caused by increases in patient visits, the communications from the applications to the central database occasionally fail. As a result, the hospital currently has the applications try to write to the central database once. If that write fails, the application writes to a dedicated application PostgreSQL database run by the hospital IT team on premises. Each of the PostgreSQL databases then sends batch information to the central database.

The hospital is asking for recommendations on migrating or refactoring the database write process to lower operational overhead.

What should the solutions architect recommend? (Select TWO.)

A
Migrate the containerized applications to AWS Fargate.

Incorrect. The container system behind the application is not the issue. Instead, communication with the central database is the issue. This solution does not address the write process.

For more information about Fargate, see AWS Fargate.


B
Migrate the local databases to Amazon Aurora Serverless PostgreSQL-Compatible Edition.

Correct. You can use PostgreSQL as a kind of messaging service (holding all of the data until the batch job runs), even though you can handle that task better with a queuing service. Moving to Aurora Serverless will lower overhead for running the database and is a valid solution.

For more information about Aurora Serverless, see Amazon Aurora Serverless.


C
Migrate the PostgreSQL databases to an Amazon RDS instance with a read replica that replaces each of the local databases.

Incorrect. Accessing the PostgreSQL databases is not an issue. In addition, read replicas are only for reads of the databases, not for writes to the databases.

For more information about RDS read replicas, see Amazon RDS Read Replicas.


D
Refactor the applications to use Amazon Simple Queue Service (Amazon SQS) and eliminate the local PostgreSQL databases.

Correct. The hospital can decouple the messaging aspect of the application and eliminate the databases (which are effectively a workaround messaging service).

For more information about how Amazon SQS works, see Create a Queue (Console).


E
Refactor the central database to add an Amazon ElastiCache lazy loading cache in front of the database.

Incorrect. Caching will typically speed up requests for data, not writes to the database. In a lazy load configuration, ElastiCache will not write new data to the database. A write-through strategy could potentially help this issue, depending on the reason for the communication failure.

For more information about ElastiCache strategies, see Caching Strategies.


19. A company uses Amazon EC2 instances in a test environment. The company has optimized the instances for their current workload. The company uses the instances only during business hours. The company uses Compute Savings Plans and Spot Instances. The company must retain control over the compute resources. A solutions architect must recommend a solution to reduce costs associated with the EC2 instances in the test environment.

Which solution will meet these requirements?



Question
A company uses Amazon EC2 instances in a test environment. The company has optimized the instances for their current workload. The company uses the instances only during business hours. The company uses Compute Savings Plans and Spot Instances. The company must retain control over the compute resources. A solutions architect must recommend a solution to reduce costs associated with the EC2 instances in the test environment.

Which solution will meet these requirements?

Report Content Errors

A
Use AWS Compute Optimizer and change the instance type or size based on the recommendations.

Incorrect. The company has already optimized the instances. Therefore, Compute Optimizer will not reduce costs.

B
Create a time-based Amazon CloudWatch alarm action to start and stop the instances.

Correct. A CloudWatch alarm action would give the company the ability to reduce the costs by turning off the instances during evenings and weekends.

For more information about CloudWatch alarm actions, see Create Alarms to Stop, Terminate, Reboot, or Recover an EC2 Instance.


C
Use Reserved Instances in addition to the Compute Savings Plan and Spot Instances.

Incorrect. The company uses the instances only during business hours. Reserved Instances would add unnecessary cost to the solution.

For more information about Reserved Instances, see Reserved Instances.


D
Switch from EC2 instances to AWS Lambda functions to optimize the runtime environment.

Incorrect. The company must have control over the compute resources. Lambda functions would not provide the required control over the compute resources.


20. A company is running its application in a single Region on Amazon EC2 with Amazon Elastic Block Store (Amazon EBS) and Amazon S3 as part of the storage design.

What should be done to reduce data transfer costs?

A
Create a copy of the compute environment in another AWS Region.

Incorrect. Data transfers into and out of Amazon EC2 across Availability Zones in the same Region incur a charge. Data transfers into and out of Amazon EC2 across Regions also incur a charge. A copy of the compute environment in another Region could increase data transfer costs.

For more information about Amazon EC2 data transfer pricing, see Amazon EC2 On-Demand Pricing.


B
Convert the application to run on Lambda@Edge.

Incorrect. With Lambda@Edge, you can run Lambda functions to customize content that CloudFront delivers and initiate the functions in AWS locations that are closer to the viewer. The functions run in response to CloudFront events. No provisioning or management of servers is necessary. Lambda@Edge would not be useful in this scenario. This solution would not reduce data transfer costs.

For more information about Lambda@Edge, see Using AWS Lambda with CloudFront Lambda@Edge.


C
Create an Amazon CloudFront distribution with Amazon S3 as the origin.

Correct. The charges for data transfer from CloudFront to the internet are lower than charges for data transfer from Amazon S3 to the internet. Additionally, there is no charge for data transfer from an AWS origin such as Amazon S3 to any CloudFront edge location. Therefore, this solution would reduce data transfer costs.

For more information about CloudFront pricing, see Amazon CloudFront Pricing.


D
Replicate Amazon S3 data to buckets in AWS Regions closer to the requester.

Incorrect. The distance between a requester and an S3 bucket does not affect cost. Therefore, this solution would not reduce data transfer costs. Additionally, the replication of data between S3 buckets in different Regions would incur charges. This solution would increase data transfer costs.

For more information about Amazon S3 pricing, see Amazon S3 Pricing.












































































































































































































































































































































































