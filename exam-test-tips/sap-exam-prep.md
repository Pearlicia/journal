## AWS Solutions Architect Professional

### Question 1: A company has a requirement to store documents that will be accessed by a serverless application. The documents will be accessed frequently for the first 3 months, and rarely after that. The documents must be retained for 7 years. What is the MOST cost-effective solution to meet these requirements?

A. Store the documents in an encrypted EBS volume and create a cron job to delete the documents after 7 years.
B. Store the documents in Amazon EFS. Create a cron job to move the documents that are older than 3 months to Amazon S3 Glacier. Create an AWS Lambda function to delete the documents in S3 Glacier that are older than 7 years.
C. Store the documents in a secured Amazon S3 bucket with a lifecycle policy to move the documents that are older than 3 months to Amazon S3 Glacier, then expire the documents from Amazon S3 Glacier that are more than 7 years old.
D. Store the documents in a secured Amazon S3 bucket with a lifecycle policy to move the documents that are older than 3 months to Amazon S3 Glacier. Create an AWS Lambda function to delete the documents in S3 Glacier that are older than 7 years.

The correct answer is C. “Store the documents in a secured Amazon S3 bucket with a lifecycle policy to move the documents that are older than 3 months to Amazon S3 Glacier, then expire the documents from Amazon S3 Glacier that are more than 7 years old”.

### Explanation:

An S3 Lifecycle configuration is a set of rules that define actions that Amazon S3 applies to a group of objects. Actions are to either transition objects to another storage class or expire (delete) the objects.

In this case, the lifecycle policy can be created to move the objects to S3 Glacier (lower cost archival) when they are no longer frequently accessed, and then expire the objects when they no longer need to be retained.

The following image shows the waterfall model for support transitions between storage classes:

A. “Store the documents in an encrypted EBS volume and create a cron job to delete the documents after 7 years” is incorrect. Amazon EBS volumes must be mounted to EC2 instances and this is not a cost-effective solution.

B. “Store the documents in Amazon EFS. Create a cron job to move the documents that are older than 3 months to Amazon S3 Glacier. Create an AWS Lambda function to delete the documents in S3 Glacier that are older than 7 years” is incorrect. Amazon EFS filesystems must be mounted to EC2 instances and this is not a cost-effective solution.

D. “Store the documents in a secured Amazon S3 bucket with a lifecycle policy to move the documents that are older than 3 months to Amazon S3 Glacier. Create an AWS Lambda function to delete the documents in S3 Glacier that are older than 7 years” is incorrect. It is not necessary to use a Lambda function to delete the objects, a lifecycle policy can be used instead and is more cost-effective.

### Question 2: A new application that provides fitness and training advice has become extremely popular with thousands of new users from around the world. The web application is hosted on a fleet of Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer (ALB). The content consists of static media files and different resources must be loaded depending on the client operating system. Users have reported increasing latency for loading web pages and Amazon CloudWatch is showing high utilization of the EC2 instances. Which set actions should a solutions architect take to improve response times?

A. Create separate Auto Scaling groups based on client operating systems. Switch to a Network Load Balancer (NLB). Use the User-Agent HTTP header in the NLB to route to a different set of EC2 instances.
B. Create a separate ALB for each client operating system. Create one Auto Scaling group behind each ALB. Use Amazon Route 53 to route to different ALBs depending on the User-Agent HTTP header.
C. Move content to Amazon S3. Create an Amazon CloudFront distribution to serve content out of the S3 bucket. Use the User-Agent HTTP header to load different content.
D. Move content to Amazon S3. Create an Amazon CloudFront distribution to serve content out of the S3 bucket. Use Lambda@Edge to load different resources based on the User-Agent HTTP header.

The correct answer is D.  “Move content to Amazon S3. Create an Amazon CloudFront distribution to serve content out of the S3 bucket. Use Lambda@Edge to load different resources based on the User-Agent HTTP header”.

### Explanation:

The load on the EC2 instances can be reduced by serving the static contents from Amazon CloudFront. This service will cache the content at Edge locations for faster delivery to clients.

To load different content based on the client operating system Lambda@Edge can be used. Lambda@Edge lets you run Node.js and Python Lambda functions to customize the content that CloudFront delivers.

Lambda@Edge can be configured to inspect the viewer request and look for the user-agent HTTP header. This header is a string that can be used to identify the application, operating system, vendor, and/or version of the requesting user agent. Based on the operating system of the client, the function can then return different media assets from the CloudFront cache.

You can use Lambda functions to change CloudFront requests and responses at the following points:

- After CloudFront receives a request from a viewer (viewer request)
- Before CloudFront forwards the request to the origin (origin request)
- After CloudFront receives the response from the origin (origin response)
- Before CloudFront forwards the response to the viewer (viewer response)

A. “Create separate Auto Scaling groups based on client operating systems. Switch to a Network Load Balancer (NLB). Use the User-Agent HTTP header in the NLB to route to a different set of EC2 instances” is incorrect. The user-agent HTTP header cannot be used by an NLB to route to a different target group (set of EC2 instances).

B. “Create a separate ALB for each client operating system. Create one Auto Scaling group behind each ALB. Use Amazon Route 53 to route to different ALBs depending on the User-Agent HTTP header” is incorrect. Route 53 cannot be used to route traffic based on the user-agent HTTP header.

C. “Move content to Amazon S3. Create an Amazon CloudFront distribution to serve content out of the S3 bucket. Use the User-Agent HTTP header to load different content” is incorrect. There is no solution here for how to process the user-agent HTTP header and load different content. This is not a native capability of CloudFront which is why the correct solution uses a Lambda function to perform this processing.

### Question 3: A company uses AWS Organizations. The company recently acquired a new business unit and invited the new unit’s existing account to the company’s organization. The organization uses a deny list SCP in the root of the organization and all accounts are members of a single OU named Production. The administrators of the new business unit discovered that they are unable to access AWS Database Migration Service (DMS) to complete an in-progress migration. Which option will temporarily allow administrators to access AWS DMS and complete the migration project?

A. Remove the organization's root SCPs that limit access to AWS DMS. Create an SCP that allows AWS DMS actions and apply the SCP to the Production OU.
B. Create a temporary OU named Staging for the new account. Apply an SCP to the Staging OU to allow AWS DMS actions. Move the new account to the Production OU when the migration project is complete.
C. Convert the organization's root SCPs from deny list SCPs to allow list SCPs to allow the required services only. Temporarily apply an SCP to the organization's root that allows AWS DMS actions for principals only in the new account.
D. Create a temporary OU named Staging for the new account. Apply an SCP to the Staging OU to allow AWS DMS actions. Move the organization's deny list SCP to the Production OU. Move the new account to the Production OU when adjustments to AWS DMS are complete.

The correct answer is D. “Create a temporary OU named Staging for the new account. Apply an SCP to the Staging OU to allow AWS DMS actions. Move the organization’s deny list SCP to the Production OU. Move the new account to the Production OU when adjustments to AWS DMS are complete”.

### Explanation:

A deny list strategy uses an implicit deny and has an SCP named AWSFullAccess applied at the root level (by default) which allows all actions. In this case the company has applied a deny list SCP at the root level which denies access to specific services.

In AWS Organizations any account has only those permissions permitted by every parent above it. If a permission is blocked at any level above the account, either implicitly (by not being included in an Allow policy statement) or explicitly (by being included in a Deny policy statement), a user or role in the affected account can’t use that permission.

Therefore, it will not be possible to allow services in an OU that have been denied at the root level. The only solution is to move the deny list from the root level to the Production OU (which means it is still effective for all other accounts) and then create a temporary OU with an SCP that allows AWS DMS (the AWSFullAccess would do this if it has not been removed).

A. “Remove the organization’s root SCPs that limit access to AWS DMS. Create an SCP that allows AWS DMS actions and apply the SCP to the Production OU” is incorrect. This would enabled AWS DMS for all member accounts which is more permissions than is required so this is not the best option.

B. “Create a temporary OU named Staging for the new account. Apply an SCP to the Staging OU to allow AWS DMS actions. Move the new account to the Production OU when the migration project is complete” is incorrect. The deny list SCP at the root level will not allow the restricted actions to be allowed at any level beneath so this will not work.

C. “Convert the organization’s root SCPs from deny list SCPs to allow list SCPs to allow the required services only. Temporarily apply an SCP to the organization’s root that allows AWS DMS actions for principals only in the new account” is incorrect. There is considerably more work involved with converting the SCPs, it would be much simpler to move the deny list SCP from the root to the Production OU to remove restrictions from higher in the hierarchy.






