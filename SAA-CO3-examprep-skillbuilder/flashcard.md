# Questions and Answers

1. How do you protect objects in your Amazon S3 buckets from deletion or overwrite?

Turn on versioning and MFA delete.

2. How do you secure sensitive data in Amazon EBS volumes?

Ensure you turn on EBS encryption when creating the volume.

3. What AWS service can you use to provide short-term access that acts as temporary security credentials for access to your AWS resources?

AWS Security Token Service

4. What permissions do IAM identities start with when you create a new user, group, or role?

No permissions, all permissions must be explicitly granted.

5. What two types of policies can be attached to an IAM role?

Trust policy and permission policy

6. What two main ways are Service Control Policies  used?

To block services by default and then allow certain services. This is known as an allow list.
Allow by default and block access to certain services known as a deny list.

7. What are some differences between network access control lists and security groups?

Network ACLs are used with subnets and are used for explicit denies and allows
Security groups are used for almost everything else and are simpler because they are stateful, so there are less rules needed to secure your environment
Security groups are used with the elastic network interfaces of your Amazon EC2 instances or resources 
Security groups have an explicit deny, meaning anything not explicitly allowed will be denied
Network ACLs are processed in order from the lowest rule number to the highest rule number
Network ACLs are stateless and security groups are stateful

8. What are the two types of endpoints that you can create inside your Amazon VPC?

Gateway Endpoints are used for AWS public services. Sometimes we want to connect to these public services like S3 or DynamoDB from a private instance or subnet that does not have access to the internet or a NAT Gateway setup. Gateway endpoints can be restricted using policies, use routing, and need an entry on the route table.
Interface Endpoints are used for everything else, and you have to pick the correct endpoint depending on the AWS services. Interface endpoints use security groups, not policies. They also use DNS with a prefix list.

9. Which AWS service do you integrate to encrypt and rotate all database credentials, API keys, and secrets?

AWS Secrets Manager

10. Which AWS service do you integrate to secure your web application and allow multiple domains to serve SSL traffic over the same IP address?

AWS Certificate Manager


11. Which AWS Directory Service do you implement to access resources both on premises and in AWS using the on premises credentials?

AWS Directory Service for Microsoft Active Directory

12. You need to limit the maximum number of requests from a single IP address for your AWS WAF rule. What do you create?

A rate-based rule and set the rate limit.


13. For your AWS WAFs, why is knowledge of the OSI model important?

Because what the firewall can read depends on what layer your firewall runs at on the OSI model. You have to know what layer our product or application operates at, and then you can determine what capabilities the firewall can have. The higher layer of the firewall, the more compute performance is needed, and the cost is also more.



14. If you need to design and implement synchronous data replication across Availability Zones for your Amazon RDS instances, what is the best solution? 

Multi-AZ deployment

15. If you need to design and implement asynchronous data replication to another Amazon RDS instance in another AWS Region, what is the best solution?

Add a read replica

16. You need to create a disaster recovery plan for your relational database with an RTO of 60 seconds and a RPO of 1 second. What Amazon RDS database would be the best choice?

Amazon Aurora Global Database because it can take a single Amazon Aurora database and span multiple AWS Regions and uses storage-based replication with typical latency of less than 1 second. In the event of a Regional degradation or outage, one of the secondary Regions can be promoted to read and write capabilities in less than 1 minute.

17. What is high availability? 

High availability is a way to design your systems to have the ability to keep your systems up and running and providing service as often as possible. If a system component fails, then that failure can be replaced or fixed as quickly as possible.

18. What is fault tolerance?

Although similar to high availability, fault tolerance is the actual ability of a system to keep operating in the event of a failure. One or more of the system's components fails, but the system is able to continue even with those faults failing. A fault-tolerant design must continue to operate.

19. What is disaster recovery?

Disaster recovery is a bit different from fault tolerance and high availability because fault tolerance and high availability are all about designing systems to operate through a disaster. Disaster recovery is all about what to plan for and also what to do in the event of a disaster. 

20. Which AWS service can you implement to create a DNS failover to a static website hosted on Amazon S3?

Amazon Route 53 with the failover routing policy

21. What Amazon S3 storage class would you choose to store cold data?

Amazon S3 Glacier

22. What storage solution would you choose if you needed a parallel file system to store frequently accessed data? 

Amazon FSx for Lustre

### Domain 3

23. Which load balancer is at Layer 7 of the OSI model?

The Application Load Balancer

24. Which load balancer do you integrate to scale and handle millions of requests per second? 

Network Load Balancer

25. What is the difference between Amazon CloudFront and AWS Global Accelerator?

CloudFront will improve content for cache content, both static and dynamic content, and content that is served from the edge locations most of the time.

 

Global Accelerator improves the performance for applications over TCP and UDP because the packets are being proxied from the edge locations to the applications running in one or more Regions. All requests are making it to the edge, but there is no caching available. Global Accelerator is useful for HTTP use cases that need a static IP or need fast Regional failover.


26. What are the two types of replication for Amazon S3?

Cross-Region Replication and Same-Region Replication

27. What are the three storage options for AWS Storage Gateway?

File Gateway, Volume Gateway, and Tape Gateway

28. What are the storage options for Amazon EC2 instances?

Instance store (ephemeral)  and EBS volumes (persistent)

29. What is the resiliency of Amazon EBS?

EBS volumes are created in an Availability Zone. EBS is highly available and reslient because its data is replicated inside the Availability Zone. With EBS volumes, you can also create a snapshot to offer higher availability.

30. What type of instances can you use with Amazon Elastic File System (Amazon EFS)?

Linux instances

31. What is the difference between a query and a scan for your Amazon DynamoDB table?

A query is a way to retrieve data from DynamoDB. You use a partition key value to start this query. You specify a single value for your partition key, and that will return an item or items. It is more efficient to pull as much data as possible in one query, so you do not have multiple reads and waste RCUs. You can also filter this down by adding a sort key value or a range of sort key values. 
To perform more flexible operations you can use a scan; However, it is not efficient for getting your data, but it is flexible. You can choose a specific attribute or filter and those will be applied to your scan. The scan moves through your table and consumes the capacity of each item in the table. The entire table is consumed, but it will give you control on what data is selected. However, it does access every item, so the whole table is consumed. It does not return items that do not match the attributes selected and added, or the filter selected and added, but it consumes the entire capacity of that table.   

32. What can you integrate into your Amazon DynamoDB table to take action?

You can use DynamoDB streams and AWS Lambda to create triggers, and can then take action.

33. Which AWS database service can be used as a data warehouse for analytical and summarization transactions?

Amazon Redshift

34. Where does a NAT gateway sit? In a public or private subnet?

Public

35. If you use VPC peering to add access between two of your Amazon VPCs, what can you use to control the access between the Amazon VPCs?

Network ACLs and security groups

### Domain 4

36. What is an option to minimize data transfer costs between two Amazon EC2 instances?

Deploy both instances in the same Region.

37. What can you implement as a cost-effective solution to store your Amazon S3 objects that are not accessed frequently?

Create an Amazon S3 lifecycle policy to move the objects not accessed frequently to a less expensive storage class.

38. What should you turn on to use the AWS Billing and Cost Management console dashboard to track your expenses and usage?

AWS Cost Explorer

39. How can you reduce your expense of running unused Amazon EC2 instances?

Take a snapshot of the EBS volume and delete the unused Amazon EC2 instances.

40. You need to create a cost-effective solution for a web application in an Auto Scaling group of Amazon EC2 instances to ensure there is no over-provisioning or high operating costs. You also must ensure there is no degraded performance of the application. Because you are using EC2 Auto Scaling, which dynamic scaling policy will meet this requirement?

A target tracking scaling policy helps to increase or decrease the current capacity of the group of instances based on a target value for a specific metric. This scaling policy will help resolve the over-provisioning of your resources and will add or remove capacity as required to keep the metric at, or close to, the specified target value. 

41. You recently set up a dedicated network connection with AWS Direct Connect to connect from your on-premises data center to AWS to meet a requirement for consistent and dedicated access. You have another requirement to ensure that the new AWS accounts will also have the consistent and dedicated access. What can you add to your design and implement to ensure you meet these requirements in a cost-effective manner with the least amount of overhead?

Create a new Direct Connect gateway to integrate with the recently created Direct Connect connection. Then set up a Transit Gateway between the new AWS accounts and associate the transit gateway with the Direct Connect gateway. 

When you attach a transit gateway to a Direct Connect gateway (using a transit virtual interface), you can manage a single connection for multiple Amazon VPCs or VPNs that are in the same AWS Region. This solution simplifies the management of connections between an Amazon VPC and your networks over a private connection. It can also minimize the network costs, provide a more reliable network experience, and improve your bandwidth throughput.

42. You need to choose a pricing model for Amazon EC2 instances that process batch loads in your non-production environment that can withstand interruptions. Which one do you choose?

Spot Instances

43. What are On-Demand Capacity Reservations?

On-Demand Capacity Reservations reserve compute capacity for your Amazon EC2 instances in a specific Availability Zone for any duration. 

44. What are Reserved Instances? 

Reserved Instances offer a significant discount (up to 75%) compared to On-Demand instance pricing. When the Reserved Instances are assigned to a specific Availability Zone, they can provide a capacity reservation.
































