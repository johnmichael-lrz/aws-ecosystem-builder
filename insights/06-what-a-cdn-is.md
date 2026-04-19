# What a CDN Is

> By the end of this, you will understand what a
> content delivery network does, why businesses use
> one, and how CloudFront fits into that definition.

## Contents
- What a CDN Is
- Why CDNs Exist
- How a CDN Delivers Content
- What Caching Means in This Context
- How CloudFront Is AWS's CDN
- Key Terms

## What a CDN Is
A content delivery network is a globally distributed system of servers that work together to deliver content to users faster than a single origin server could. Instead of every user in the world sending requests to one central server, a CDN stores copies of content on servers positioned in cities and regions around the world. When a user requests content, the CDN routes that request to the server closest to the user and serves the content from there.

## Why CDNs Exist
The internet was not designed with global scale in mind. In its early days, websites served a small number of users in a limited geographic area, and a single server was sufficient to handle the load. As the internet grew and websites began serving users across continents, the limitations of a single origin server became apparent. Users far from the server experienced slow load times. Servers struggled to handle sudden spikes in traffic. Content that was popular in one part of the world created bottlenecks at a server located in another.

CDNs emerged as the solution to those limitations. By distributing copies of content across many servers in many locations, a CDN removes the geographic bottleneck of a single origin server and distributes the load across a global network.

## How a CDN Delivers Content
When a user requests content served by a CDN, the request is automatically routed to the server in the CDN network that is closest to the user. That server checks whether it has a cached copy of the requested content. If it does, it serves the copy immediately without contacting the origin server. If it does not, it requests the content from the origin server, stores a copy in its cache, and serves it to the user. The next user who requests the same content from that location receives it from the cache without another trip to the origin.

This process means that popular content is automatically distributed across the CDN network over time. The first user in a location triggers the fetch from the origin. Every subsequent user in that location receives the cached copy. The origin server only handles the first request from each location, rather than every request from every user everywhere in the world.

## What Caching Means in This Context
Caching is the practice of storing a copy of something in a location closer to where it will be needed. In the context of a CDN, caching means storing copies of your website files at edge locations around the world so users can receive them from a nearby server instead of from the origin.

Cached content is not stored permanently. It has a time limit called a TTL, or Time to Live, which determines how long the cached copy remains valid before the CDN checks the origin for a newer version. When the TTL expires, the next request for that content triggers a fresh fetch from the origin, and the cache is updated with the new copy.

## How CloudFront Is AWS's CDN
CloudFront is Amazon's content delivery network. It operates through hundreds of edge locations around the world and integrates directly with AWS services like S3, EC2, and API Gateway. When you create a CloudFront distribution, you tell CloudFront where your content is stored and how you want it delivered. CloudFront handles the routing, the caching, and the global distribution automatically.

Because CloudFront is part of the AWS ecosystem, it connects to S3 buckets, uses IAM for access control, and integrates with ACM for SSL certificates. This tight integration is what makes CloudFront the natural choice for delivering content stored in AWS.

## Key Terms
Content delivery network — a globally distributed system of servers that stores copies of content in multiple locations around the world to serve users from the server closest to them.

Edge location — a server in the CDN network positioned close to users that stores cached copies of content and serves them in response to user requests.

Cache — a temporary storage location where copies of files are kept so future requests can be fulfilled faster without going back to the origin server.

TTL — Time to Live, the amount of time a cached copy of content remains valid before the CDN checks the origin server for a newer version.

Origin server — the server where the original files are stored, from which the CDN fetches content when it does not have a cached copy at the nearest edge location.

Distribution — the configuration that tells CloudFront where your content is stored, how it should be cached, and how it should be delivered to users.
