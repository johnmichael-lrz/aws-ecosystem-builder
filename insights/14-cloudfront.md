# Amazon CloudFront

> By the end of this, you will understand what
> CloudFront is, how it delivers content to users
> around the world, and what you configure when
> you create a distribution.

## Contents
- What CloudFront Is
- Why CloudFront Exists
- How CloudFront Delivers Content
  - The Request Flow
  - Cache Hit vs Cache Miss
- What a Distribution Is
- What the Default Root Object Does
- How CloudFront Connects to S3
- What Breaks When It Is Misconfigured
- Key Terms

## What CloudFront Is
Amazon CloudFront is a content delivery network that distributes your content across a global network of servers positioned close to your users. Instead of every user in the world sending requests to a single origin server, CloudFront intercepts those requests at the nearest server in its network and serves the content from there. The result is that users receive your content faster, your origin server handles less traffic, and your website performs consistently regardless of where in the world your users are located.

## Why CloudFront Exists
A single origin server, no matter how powerful, has a fixed location. Users close to that location experience fast load times. Users far from it experience slow ones. As websites grew to serve global audiences, the geographic limitation of a single server became a significant problem. Content that loaded instantly for users in one country took several seconds for users on another continent.

CloudFront exists to solve that problem by bringing content physically closer to the people requesting it. Rather than making users travel across the internet to reach a single server, CloudFront positions copies of the content in hundreds of locations around the world so users always receive it from a server nearby.

## How CloudFront Delivers Content
CloudFront delivers content through a two-tier network of edge locations and regional edge caches. When a user makes a request, CloudFront routes it to the nearest edge location. The edge location checks its cache for the requested content. If it has a copy, it serves it immediately. If it does not, it checks the regional edge cache, which covers a larger geographic area and holds content that is accessed less frequently. If neither has a copy, CloudFront fetches the content from the origin server, caches it at the edge location, and serves it to the user.

### The Request Flow
When a user types a URL into a browser, the browser sends a request to the CloudFront distribution domain. CloudFront's routing system determines which edge location is closest to the user and forwards the request there. The edge location processes the request and returns the appropriate response. The user receives the content without knowing or caring which edge location served it.

### Cache Hit vs Cache Miss
A cache hit occurs when the edge location already has a copy of the requested content in its cache. The content is served immediately from the cache without contacting the origin server. This is the fastest possible response because no network request to the origin is required.

A cache miss occurs when the edge location does not have a copy of the requested content. CloudFront must contact the origin server, retrieve the content, cache it locally, and then serve it to the user. This takes longer than a cache hit because of the additional round trip to the origin. Once cached, subsequent requests for the same content from that edge location result in cache hits.

## What a Distribution Is
A distribution is the configuration that tells CloudFront how to deliver your content. It specifies where your content is stored, how it should be cached, who can access it, and how requests should be handled. Every CloudFront setup begins with creating a distribution. You create one distribution per website or application, and that distribution governs how CloudFront behaves for all requests to your content.

When you create a distribution, you give it an origin, which is where your files are stored. You configure cache behaviors, which determine how different types of requests are handled. You can attach a custom domain and an SSL certificate. Once the distribution is created and deployed, CloudFront begins routing requests through its global network according to the settings you configured.

## What the Default Root Object Does
The default root object is the file CloudFront serves when a user visits the root URL of your distribution without specifying a particular file. When someone types your CloudFront domain into a browser and presses enter, they are not requesting a specific file. The default root object setting tells CloudFront which file to return in that situation.

In this workshop, the default root object is set to index.html. This means that when a user visits your CloudFront URL, CloudFront fetches index.html from your S3 bucket and returns it to the browser. Without this setting, visiting the root URL returns an error because CloudFront does not know which file to serve.

## How CloudFront Connects to S3
CloudFront connects to S3 through the origin configuration in your distribution. When you create the distribution, you specify your S3 bucket as the origin. CloudFront uses that configuration to know where to fetch content when it has a cache miss.

The connection is secured by Origin Access Control. OAC tells CloudFront to sign every request it makes to S3 with a specific signature. The bucket policy in S3 is configured to accept only requests that carry that signature. Any request without the correct signature is denied. This means CloudFront can read from the bucket but no one else can access it directly.

## What Breaks When It Is Misconfigured
The most common misconfiguration is visiting the CloudFront URL before the distribution has finished deploying. After you create a distribution, CloudFront propagates its configuration to all edge locations around the world. This process takes several minutes. If you visit the URL while the distribution is still deploying, you may see errors that disappear once deployment is complete. Always wait for the distribution status to show as Deployed before testing the URL.

The second most common misconfiguration is leaving the default root object blank. Without a default root object, visiting the root URL of your distribution returns an Access Denied or NoSuchKey error from S3 because CloudFront does not know which file to request.

The third is the incomplete OAC configuration. If you create the OAC in CloudFront but do not paste the generated bucket policy into S3, CloudFront cannot read your files and every request returns an Access Denied error.

## Key Terms
Amazon CloudFront — a content delivery network that distributes content across a global network of servers to serve users from the location closest to them.

Distribution — the configuration that tells CloudFront where your content is stored, how to cache it, and how to deliver it to users.

Edge location — a server in CloudFront's network positioned close to users that stores cached copies of content and serves them in response to requests.

Cache hit — when an edge location already has a cached copy of the requested content and serves it immediately without contacting the origin.

Cache miss — when an edge location does not have a cached copy of the requested content and must fetch it from the origin before serving it.

Default root object — the file CloudFront serves when a user visits the root URL of the distribution without specifying a particular file.

Origin — the source where the original files are stored, from which CloudFront fetches content on a cache miss.

Origin Access Control — the permission configuration that allows CloudFront to read from a private S3 bucket while denying direct access to everyone else.
