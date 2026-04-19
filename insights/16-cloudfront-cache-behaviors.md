# CloudFront Cache Behaviors

> By the end of this, you will understand what cache
> behaviors are, how they control how CloudFront
> handles requests, and what you configure during
> the workshop.

## Contents
- What a Cache Behavior Is
- Why Cache Behaviors Exist
- How a Cache Behavior Controls a Request
- The Default Cache Behavior
- What TTL Controls
- How Cache Behaviors Apply in This Workshop
- Key Terms

## What a Cache Behavior Is
A cache behavior is a rule that tells CloudFront how to handle requests that match a specific URL path pattern. Every request that arrives at a CloudFront distribution is matched against the cache behaviors configured for that distribution. The matching behavior determines how CloudFront processes the request, including how long to cache the response, which HTTP methods to allow, and whether to forward headers or cookies to the origin.

## Why Cache Behaviors Exist
Different types of content have different caching requirements. Static files like images, stylesheets, and JavaScript files rarely change and can be cached for long periods without causing problems. Dynamic content like API responses or user-specific data should not be cached at all or should be cached for very short periods. Cache behaviors let you apply different caching rules to different parts of your website based on the URL path.

Without cache behaviors, CloudFront would have to apply a single caching rule to every request regardless of whether the content was a static image that changes once a year or a real-time API response that changes every second. Cache behaviors give you the granularity to handle each type of content appropriately.

## How a Cache Behavior Controls a Request
When a request arrives at CloudFront, the distribution checks the URL path against the path patterns defined in its cache behaviors. The most specific matching pattern wins. If a request matches a cache behavior, CloudFront applies all the settings of that behavior to the request, including the cache duration, the allowed HTTP methods, and whether to compress the response.

If the behavior specifies that responses should be cached, CloudFront checks its cache for a copy of the requested content. If it finds one and it has not expired, it serves it immediately. If it does not find one or the cached copy has expired, it fetches fresh content from the origin, caches it according to the behavior's settings, and serves it to the user.

## The Default Cache Behavior
Every CloudFront distribution has at least one cache behavior, called the default cache behavior. The default cache behavior matches all requests that do not match any other more specific path pattern. It uses an asterisk as its path pattern, which means it applies to everything.

In this workshop, you only configure the default cache behavior because your website is a simple static site with one type of content. The default behavior tells CloudFront to cache your website files and serve them from the nearest edge location.

## What TTL Controls
TTL stands for Time to Live. It is the amount of time a cached copy of content remains valid before CloudFront considers it stale and checks the origin for a newer version. A longer TTL means content stays in the cache longer, which reduces the number of requests CloudFront makes to the origin and speeds up delivery for users. A shorter TTL means CloudFront checks the origin more frequently, which ensures users always receive fresh content but increases the load on the origin.

TTL is set in seconds. A TTL of 86400 means content is cached for 24 hours. A TTL of 0 means content is never cached and every request goes to the origin. CloudFront uses the TTL value specified in the cache behavior unless the origin sends a Cache-Control header that overrides it.

## How Cache Behaviors Apply in This Workshop
In this workshop, the default cache behavior handles all requests to your CloudFront distribution. It is configured when you create the distribution and tells CloudFront to fetch content from your S3 bucket and cache it at edge locations. You do not need to create additional cache behaviors because your website consists entirely of static files that can all be handled with the same caching rules.

## Key Terms
Cache behavior — a rule that tells CloudFront how to handle requests matching a specific URL path pattern, including how long to cache responses and which HTTP methods to allow.

Path pattern — the URL pattern used to match incoming requests to a specific cache behavior, such as a wildcard that matches everything or a specific path like images.

Default cache behavior — the cache behavior that matches all requests not matched by a more specific path pattern, using an asterisk as its path pattern.

TTL — Time to Live, the number of seconds a cached copy of content remains valid before CloudFront checks the origin for a newer version.

Cache-Control header — an instruction sent by the origin server that tells CloudFront how long to cache a response, which overrides the TTL set in the cache behavior.

Stale content — a cached copy of content whose TTL has expired, triggering CloudFront to fetch a fresh copy from the origin on the next request.
