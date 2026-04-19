# Latency

> By the end of this, you will understand what latency
> is, why physical distance causes it, and why reducing
> it is the primary reason CloudFront exists.

## Contents
- What Latency Is
- What Causes It
- How Distance Affects It
- Why It Matters for Website Delivery
- How CloudFront Addresses It
- Key Terms

## What Latency Is
Latency is the time it takes for data to travel from one point to another. When a user sends a request to a server, latency is the delay between the moment the request leaves the user's device and the moment the response arrives back. It is measured in milliseconds. A response that takes 20 milliseconds feels instant. A response that takes 3,000 milliseconds feels painfully slow.

## What Causes It
Latency is caused primarily by physical distance. Data travels through fiber optic cables at close to the speed of light, but even at that speed, distance creates measurable delay. A request traveling from Manila to a server in Virginia covers roughly 14,000 kilometers. That distance alone introduces hundreds of milliseconds of delay before the server has even begun processing the request.

Distance is not the only cause. Every device a request passes through on its way to the server adds a small amount of delay. Routers, switches, and network hops each contribute. Congestion on shared network infrastructure adds more. But physical distance remains the largest and most consistent factor.

## How Distance Affects It
The relationship between distance and latency is direct. The further the data has to travel, the longer it takes to arrive. A user in Singapore requesting content from a server also in Singapore might experience 5 to 10 milliseconds of latency. The same user requesting content from a server in Virginia might experience 200 to 300 milliseconds of latency. That difference is imperceptible for a single request but becomes significant when a webpage requires dozens of separate requests to load all of its files.

## Why It Matters for Website Delivery
Every file that makes up a webpage requires its own request and response. A page with 50 images, stylesheets, and scripts requires 50 separate round trips between the user's browser and the server. If each round trip takes 200 milliseconds because the server is far away, loading that page takes 10 seconds. If each round trip takes 20 milliseconds because the server is nearby, the same page loads in one second.

High latency frustrates users and drives them away. Studies consistently show that users abandon pages that take more than a few seconds to load. For businesses, high latency directly translates to lost users, lost sales, and lost revenue.

## How CloudFront Addresses It
CloudFront reduces latency by positioning cached copies of content at edge locations around the world. Instead of every request traveling to the origin server where the original files are stored, the request goes to the nearest edge location. If that edge location has a cached copy of the requested file, it responds immediately from its local cache. The data travels a fraction of the distance, and the user receives the response in a fraction of the time.

## Key Terms
Latency — the time it takes for data to travel from a user's device to a server and back, measured in milliseconds.

Round trip — the complete journey of a request from a user's device to a server and the response back to the user.

Edge location — a server positioned close to users that stores cached copies of content to reduce the distance data has to travel.

Cache — a temporary storage location where copies of files are kept so future requests can be fulfilled faster without going back to the original source.

Origin server — the server where the original files are stored, from which content is fetched when it is not available at a nearby edge location.
