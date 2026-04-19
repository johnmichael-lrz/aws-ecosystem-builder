# The Principle of Least Privilege

> By the end of this, you will understand why AWS
> permissions are designed to give the minimum access
> needed, and why this principle explains how OAC
> is configured in the workshop.

## Contents
- What the Principle of Least Privilege Is
- Why It Exists
- What Happens When It Is Ignored
- How It Applies to CloudFront and S3
- Key Terms

## What the Principle of Least Privilege Is
The principle of least privilege is a security rule that states every identity should have access to only what it needs to do its specific job and nothing more. A user who needs to read files from one S3 bucket should not have permission to delete files from that bucket, create new buckets, or access any other service. An application that needs to write logs should not have permission to read databases or modify security settings. Access is granted based on what is necessary, not on what might be convenient.

## Why It Exists
The principle of least privilege exists because every permission that is granted is a potential risk. A user with unnecessary permissions can cause accidental damage by making changes they did not intend to make. A compromised account with broad permissions gives an attacker access to far more than a compromised account with narrow permissions. Limiting access limits the damage that can be done by either human error or a security breach.
Before cloud computing, this principle was difficult to implement precisely because managing permissions across physical systems was complex and time-consuming. IAM makes it straightforward. You can grant exactly the permissions needed and nothing else, and you can change those permissions instantly if the situation changes.

What Happens When It Is Ignored
When organizations ignore the principle of least privilege, they typically take the path of least resistance — granting broad permissions because it is faster and easier than figuring out exactly what is needed. A developer gets administrator access because it is simpler than identifying the specific services they need. An application gets full S3 access because nobody took the time to scope it to the specific bucket it uses.

The consequences range from minor to catastrophic. A developer with administrator access who makes a mistake in the wrong place can delete critical resources. An application with broad permissions that gets compromised gives an attacker the keys to the entire account. A disgruntled employee with excessive access can cause damage far beyond what their role required.

## What Happens When It Is Ignored
When organizations ignore the principle of least privilege, they typically take the path of least resistance — granting broad permissions because it is faster and easier than figuring out exactly what is needed. A developer gets administrator access because it is simpler than identifying the specific services they need. An application gets full S3 access because nobody took the time to scope it to the specific bucket it uses.

The consequences range from minor to catastrophic. A developer with administrator access who makes a mistake in the wrong place can delete critical resources. An application with broad permissions that gets compromised gives an attacker the keys to the entire account. A disgruntled employee with excessive access can cause damage far beyond what their role required.


## How It Applies to CloudFront and S3
In this workshop, the principle of least privilege explains exactly why Origin Access Control is configured the way it is. Your S3 bucket contains your website files. CloudFront needs to read those files to serve them to users. But CloudFront does not need to write files, delete files, or create new buckets. It only needs to read the specific objects in the specific bucket that stores your website.

Origin Access Control implements this precisely. The bucket policy you copy from CloudFront and paste into S3 grants CloudFront permission to perform one action on one resource: reading objects from your specific bucket. Nothing else. No other service or user can access the bucket directly. CloudFront gets exactly what it needs and nothing more.

## Key Terms
Principle of least privilege — the security rule that every identity should have access to only what it needs to perform its specific job and nothing more.

Permission — an explicit rule that grants or denies a specific action on a specific resource to a specific identity.

IAM policy — a written rule in AWS that defines what actions are allowed or denied on which resources, used to implement the principle of least privilege.

Origin Access Control — the permission configuration that grants CloudFront read access to a specific S3 bucket while denying direct access to anyone else, implementing the principle of least privilege between CloudFront and S3.
