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

















