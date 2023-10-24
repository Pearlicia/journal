Want to "Automatically build CI/CD pipelines and Amazon ECS clusters for microservices using AWS CDK"?
Flow:
1) An application developer commits code to a CodeCommit repository.
2) A pipeline is initiated.
3) CodeBuild builds and pushes the Docker image to an Amazon ECR repository
4) CodePipeline deploys a new image to an existing Fargate service in a non-production Amazon ECS cluster.
5) Amazon ECS pulls the image from the Amazon ECR repository into a non-production Fargate service.
6) Testing is performed using a non-production URL.
7) The release manager approves the production deployment.
8) CodePipeline deploys the new image to an existing Fargate service in a production Amazon ECS cluster
9) Amazon ECS pulls the image from the Amazon ECR repository into the production Fargate service.
10) Production users access your feature by using a production URL.

Tools:
AWS CDK – AWS Cloud Development Kit (AWS CDK) is a software development framework for defining cloud infrastructure in code and provisioning it through AWS CloudFormation.

AWS CodeBuild – AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy.

AWS CodeCommit – AWS CodeCommit is a version control service that enables you to privately store and manage Git repositories in the AWS Cloud. CodeCommit eliminates the need for you to manage your own source control system or worry about scaling its infrastructure.

AWS CodePipeline – AWS CodePipeline is a continuous delivery service you can use to model, visualize, and automate the steps required to release your software. You can quickly model and configure the different stages of a software release process. CodePipeline automates the steps required to release your software changes continuously.

Amazon ECS – Amazon Elastic Container Service (Amazon ECS) is a highly scalable, fast container management service that is used for running, stopping, and managing containers on a cluster. You can run your tasks and services on a serverless infrastructure that is managed by AWS Fargate. Alternatively, for more control over your infrastructure, you can run your tasks and services on a cluster of Amazon Elastic Compute Cloud (Amazon EC2) instances that you manage.

Docker – Docker helps developers to pack, ship, and run any application as a lightweight, portable, and self-sufficient container

For codes and full instructions check: https://lnkd.in/gTj9NsXJ
