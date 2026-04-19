# IAM

> By the end of this, you will understand what IAM
> is, why AWS denies access by default, and how
> permissions are granted between services like
> CloudFront and S3.

## Contents
- What IAM Is
- Why AWS Denies Everything by Default
- The Root User
- IAM Users
- IAM Groups
- IAM Policies
- How Services Use Permissions
- How IAM Applies in This Workshop
- Key Terms

## What IAM Is
IAM stands for Identity and Access Management. It is the AWS service that controls who can access your AWS account and what they are allowed to do once they are inside. IAM does not store your files, run your applications, or deliver your content. Its only job is to answer two questions: who are you, and what are you allowed to do?

## Why AWS Denies Everything by Default
When you create an AWS account, nothing is accessible to anyone except the root user. Every other user, every service, and every application starts with zero permissions. They cannot read files, create resources, or make changes to anything until you explicitly write a rule granting them permission to do so.

This is intentional. It follows the principle of least privilege, which states that every identity should have access to only what it needs to do its job and nothing more. Denying everything by default means that access is always the result of a deliberate decision, not an oversight.

## The Root User
The root user is the identity created automatically when you sign up for AWS. It uses the email address and password you registered with. The root user has unrestricted access to everything in the account. It can delete all resources, close the account, change billing settings, and override any permission rule. Because of this, the root user should only be used for the initial account setup and never for everyday tasks. Every daily action should be performed through a separate IAM user with appropriate permissions.

## IAM Users
An IAM user is a separate identity created inside your AWS account for a specific person or application. Each IAM user has its own credentials and its own set of permissions. You can create as many IAM users as you need, and you can give each one a different level of access depending on what they need to do. A developer might get access to EC2 and S3. An accountant might get access only to billing. A monitoring tool might get read-only access to CloudWatch logs.

## IAM Groups
An IAM group is a collection of IAM users that share the same permissions. Instead of assigning permissions to each user individually, you assign permissions to the group and add users to it. Every user in the group inherits the group's permissions automatically. This makes managing permissions easier as teams grow. Adding a new team member means adding them to the appropriate group rather than manually assigning every permission they need.

## IAM Policies
An IAM policy is a written rule that defines what actions are allowed or denied on which resources. A policy is attached to a user, a group, or a role, and it governs what that identity can do. A policy might say: allow this user to read objects from this specific S3 bucket. Or: deny this user from deleting any resource in the account. Policies are written in a structured format and can be as broad or as specific as needed.

## IAM Roles
An IAM role is an identity that can be assumed by a person, an application, or an AWS service when it needs to perform a specific task. Unlike a user, a role does not belong to a specific person. It is assumed temporarily by whoever or whatever needs it. CloudFront uses a role when it needs to access your S3 bucket. EC2 instances use roles when they need to write logs to CloudWatch. Roles are how AWS services talk to each other securely without sharing passwords or access keys.

## How Services Use Permissions
In AWS, it is not only people who need permissions. Services also need permission to interact with other services. CloudFront cannot read from your S3 bucket just because they are both in your account. S3 cannot write logs to CloudWatch on its own. An EC2 instance cannot access a database without being explicitly granted permission to do so.

Services use IAM roles to interact with other services. A role is assigned to a service, and that role carries a policy defining exactly what the service is allowed to do. When CloudFront needs to read a file from your S3 bucket, it assumes a role that has been granted read access to that specific bucket. S3 checks the request, verifies that it carries the correct permissions, and either serves the file or denies the request.

This is why Origin Access Control works the way it does. When you create an OAC and attach it to your CloudFront distribution, you are telling CloudFront which role to assume when making requests to S3. When you paste the generated bucket policy into your S3 bucket, you are telling S3 to accept requests that come from that specific CloudFront distribution and reject everything else. The two steps together create a secure channel between CloudFront and S3 that no other service or user can use.

## How IAM Applies in This Workshop
In this workshop, IAM is involved in two specific places. The first is your own access to the console. You should be logged in as an IAM admin user, not the root account. The second is the relationship between CloudFront and S3. When you configure Origin Access Control, you are creating an IAM-based permission that allows CloudFront to read objects from your S3 bucket while preventing anyone else from accessing the bucket directly.

## Key Terms
IAM — Identity and Access Management, the AWS service that controls who can access your account and what they are allowed to do.

Root user — the primary identity created when you sign up for AWS, with unrestricted access to everything in the account. Should never be used for daily tasks.

IAM user — a separate identity created inside an AWS account for a specific person or application, with its own credentials and permissions.

IAM group — a collection of IAM users that share the same permissions, making it easier to manage access as teams grow.

IAM policy — a written rule that defines what actions are allowed or denied on which resources, attached to a user, group, or role.

IAM role — an identity that can be assumed temporarily by a person, application, or AWS service to perform a specific task without sharing credentials.

Least privilege — the principle that every identity should have access to only what it needs to do its job and nothing more.

Origin Access Control — an IAM-based permission that allows CloudFront to read objects from a private S3 bucket while preventing direct public access to the bucket.
