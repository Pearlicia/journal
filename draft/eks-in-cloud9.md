Curious about how to "Deploy an Amazon EKS cluster from AWS Cloud9 using an EC2 instance profile"?

This pattern describes how to use AWS Cloud9 and AWS CloudFormation to create an Amazon Elastic Kubernetes Service (Amazon EKS) cluster that can be operated without enabling programmatic access for users in your Amazon Web Services (AWS) account.

You can use this pattern if you don’t want to create AWS Identity and Access Management (IAM) users and want to use IAM roles instead. Role-based access control (RBAC) regulates access to resources based on the roles of individual users. This pattern demonstrates how to update RBAC within an Amazon EKS cluster to allow access to a specific IAM role.


Steps:
1) Create the IAM roles for the EC2 instance profile
2) Create an IAM policy and role for the Amazon EKS RBAC
3) Create the Amazon EKS cluster:
aws cloudformation create-stack --stack-name eks-cluster --template-body file://eks-cfn.yaml --region <your_AWS_Region>
4) Access the Kubernetes resources in the Amazon EKS cluster

Tools:
AWS CloudFormation – AWS CloudFormation helps you model and set up your AWS resources so that you can spend less time managing those resources and more time focusing on your applications.

AWS Cloud9 – AWS Cloud9 offers a rich code-editing experience with support for several programming languages and runtime debuggers, and a built-in terminal.

AWS CLI – AWS Command Line Interface (AWS CLI) is an open-source tool that enables you to interact with AWS services using commands in your command-line shell.

Kubectl – kubectl is a command line utility that you can use to interact with an Amazon EKS cluster.

Full documentation, steps and codes here: https://lnkd.in/ggcEaPJf
