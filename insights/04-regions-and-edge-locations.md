# Regions and Edge Locations

> By the end of this, you will understand where AWS
> infrastructure lives, why that geography matters
> for your workshop, and why ACM certificates must
> be created in us-east-1.

## Contents
- What a Region Is
- What an Availability Zone Is
- What an Edge Location Is
- How Regions and Edge Locations Differ
- Why Region Selection Affects Your Workshop
- The us-east-1 Requirement for ACM
- Key Terms

## What a Region Is
A region is a geographic location where AWS operates a cluster of data centers. Each region is a separate, independent area of the world with its own physical infrastructure. 

When you create a resource in AWS, you create it in a specific region, and that resource lives in that region unless you explicitly move or replicate it elsewhere. AWS currently operates regions across North America, South America, Europe, Asia Pacific, the Middle East, and Africa, giving organizations the ability to store and process data close to the people who need it.Regions exist because physical distance affects how fast data can travel. 

A server in Virginia cannot respond to a user in Manila as quickly as a server in Singapore can. By operating data centers in multiple regions around the world, AWS lets organizations choose where their resources live and how close those resources are to their users.

## What an Availability Zone Is
Each region contains multiple availability zones. An availability zone is an isolated data center within a region, physically separated from other availability zones by a meaningful distance but connected to them through high-speed private networks. The separation means that if one availability zone experiences a power outage, a flood, or a hardware failure, the other availability zones in the same region continue operating without interruption.

Availability zones exist to protect against localized failures. A single data center is a single point of failure. Multiple isolated data centers connected by fast private networks give organizations the ability to build systems that survive hardware failures and infrastructure outages without going offline.

## What an Edge Location Is
An edge location is a server positioned in a city or region specifically to serve cached content to users nearby. Edge locations are not full AWS regions. They do not host databases, run applications, or store original copies of files. Their only job is to store cached copies of content and serve those copies to users who are physically close to them.

CloudFront operates through edge locations. When a user requests a file served by CloudFront, the request goes to the nearest edge location rather than traveling all the way to the origin server where the original file is stored. If the edge location has a cached copy of the file, it serves it immediately. If it does not, it fetches the file from the origin, caches it, and serves it to the user. Every subsequent user who requests the same file from that edge location receives it from the cache without another trip to the origin.

AWS operates hundreds of edge locations around the world, significantly more than the number of full regions. This density means that most users are physically close to at least one edge location, which is what makes CloudFront able to deliver content with low latency to users anywhere in the world.

## How Regions and Edge Locations Differ
Regions are where you deploy your infrastructure. They house the full range of AWS services and store your original data. Edge locations are where CloudFront caches copies of your content to serve users faster. You choose which region your S3 bucket lives in. CloudFront automatically determines which edge locations to use based on where your users are located.

## Why Region Selection Affects Your Workshop
Every resource you create in this workshop belongs to a specific region. Your S3 bucket will be created in the region you select. The region you choose affects how fast your origin server responds to CloudFront when it needs to fetch a file that is not yet cached. Choose the region closest to where you are located.

## The us-east-1 Requirement for ACM
AWS Certificate Manager certificates used with CloudFront must be created in the us-east-1 region, which is US East in Northern Virginia, regardless of where your other resources are located. This is a specific technical requirement of how CloudFront integrates with ACM. If you create a certificate in any other region, it will not appear as an option when configuring your CloudFront distribution.

## Key Terms
Region — a geographic location where AWS operates a cluster of data centers, identified by a code such as ap-southeast-1 for Singapore or us-east-1 for Northern Virginia.

Availability zone — an isolated data center within a region, physically separated from other availability zones to protect against localized failures while remaining connected through high-speed private networks.

Edge location — a server positioned in a specific city or area to store cached copies of content and serve them to nearby users with low latency.

Caching — storing a copy of a file in a temporary location so future requests for the same file can be fulfilled faster without going back to the original source.

Latency — the time it takes for data to travel from one point to another, affected by the physical distance between the user and the server.

Origin — the source where the original files are stored, from which CloudFront fetches content when it does not have a cached copy at the edge location.
