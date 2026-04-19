# S3 Access Control

> By the end of this, you will understand how S3
> controls who can read your files, why buckets are
> private by default, and what a bucket policy does.

## Contents
- Why S3 Buckets Are Private by Default
- What a Bucket Policy Is
- How a Bucket Policy Works
- What Block Public Access Does
- How Access Control Applies in This Workshop
- What Breaks When It Is Misconfigured
- Key Terms

## Why S3 Buckets Are Private by Default
When you create an S3 bucket, it is completely private. No one outside your AWS account can read, write, or list its contents. No application, no service, and no user on the internet can access anything inside it unless you explicitly write a rule granting that access. This is intentional. AWS defaults to the most restrictive setting possible so that sensitive data is never accidentally exposed.

This default behavior means that even if you upload your website files to S3, nobody can view them through a browser until you configure the appropriate permissions. The files exist in the bucket but the bucket door is locked. You hold the only key until you decide to share it.

## What a Bucket Policy Is
A bucket policy is a JSON document attached directly to an S3 bucket that defines who can access the bucket and what they are allowed to do. It is a resource-based policy, meaning it is attached to the resource itself rather than to a user or role. A bucket policy can grant or deny access to specific AWS accounts, specific IAM users, specific services like CloudFront, or the general public.

A bucket policy works alongside IAM policies. If an IAM policy grants a user access to a bucket but the bucket policy denies that user, the denial wins. If an IAM policy is silent about a bucket but the bucket policy grants access, the grant applies. The two systems work together to determine who can do what.

## How a Bucket Policy Works
A bucket policy is made up of one or more statements. Each statement defines a principal, an action, a resource, and an effect.

The principal is who the statement applies to. It can be a specific AWS account, an IAM user, an IAM role, a service like CloudFront, or everyone using a wildcard.

The action is what the principal is allowed or denied to do. For S3, common actions include reading an object, writing an object, listing the contents of a bucket, and deleting an object.

The resource is which bucket or objects the statement applies to. A statement can apply to an entire bucket, a specific folder within a bucket, or a specific object.

The effect is whether the statement allows or denies the action. If the effect is Allow, the principal can perform the action on the resource. If the effect is Deny, the principal cannot, regardless of what any other policy says.

## What Block Public Access Does
Block Public Access is a set of four settings that override bucket policies and ACLs to prevent public access to a bucket regardless of what those policies say. It exists as a safeguard against accidental exposure. Even if a bucket policy grants public read access, Block Public Access can override that grant and keep the bucket private.

AWS enables all four Block Public Access settings by default on every new bucket. This means that even if you write a bucket policy granting public access, it will have no effect until you disable the relevant Block Public Access settings. 

In this workshop, you do not need to disable Block Public Access because you are using CloudFront with Origin Access Control, which keeps the bucket private while still allowing CloudFront to read from it.

## How Access Control Applies in This Workshop
In this workshop, your S3 bucket stays private. You do not make its contents publicly accessible. Instead, you configure a bucket policy that grants CloudFront and only CloudFront permission to read objects from the bucket. This bucket policy is generated automatically by CloudFront when you create the Origin Access Control. You copy it from the CloudFront console and paste it into the bucket's permissions settings.

Once the bucket policy is in place, any request that does not come from your specific CloudFront distribution is denied by S3. A user who discovers your bucket name and tries to access it directly through a browser receives an Access Denied error. Only requests that pass through CloudFront and carry the OAC signature are served.

## What Breaks When It Is Misconfigured
The most common misconfiguration in this workshop is completing Step 5 in CloudFront without completing Step 6 in S3. Creating the Origin Access Control in CloudFront tells CloudFront which signature to use when making requests to S3. But S3 does not know to accept that signature until you paste the generated bucket policy into the bucket. If you skip Step 6, S3 still has no policy granting CloudFront access, and every request from CloudFront returns an Access Denied error.

The second most common misconfiguration is having Block Public Access enabled while also trying to use a bucket policy that grants public access. If you are using CloudFront with OAC, you do not need to disable Block Public Access. But if you are trying to use S3 static website hosting without CloudFront, you must disable the relevant Block Public Access settings before your bucket policy can take effect.

## Key Terms
Bucket policy — a JSON document attached to an S3 bucket that defines who can access the bucket and what they are allowed to do.

Resource-based policy — a policy attached directly to a resource like an S3 bucket rather than to a user or role, defining who can access that specific resource.

Principal — the identity a bucket policy statement applies to, such as a specific IAM user, an AWS service, or everyone using a wildcard.

Action — the specific operation a bucket policy statement allows or denies, such as reading an object or listing bucket contents.

Effect — whether a bucket policy statement allows or denies the specified action, with Deny always taking precedence over Allow.

Block Public Access — a set of four S3 settings that override bucket policies and ACLs to prevent public access to a bucket regardless of what those policies say.

Origin Access Control — the permission configuration that allows CloudFront to read from a private S3 bucket while denying direct access to everyone else.
