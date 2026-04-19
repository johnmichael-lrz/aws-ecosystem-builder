# How the Internet Works

> By the end of this, you will understand what happens
> between the moment a user types a URL and the moment
> a page appears on their screen.

## Contents
- What the Internet Actually Is
- What Happens When You Visit a Website
- What a Server Is
- What a Request and Response Are
- Why This Matters for CloudFront
- Key Terms

## What the Internet Actually Is
The internet is a global network of computers connected to each other through physical cables, fiber optic lines, and wireless signals. When two computers are connected to this network, they can send information back and forth regardless of where in the world they are located. The internet is not a single machine or a single location. It is the infrastructure that makes communication between computers possible at a global scale.

## What Happens When You Visit a Website
When you type a URL into a browser and press enter, your computer does not already know where that website lives. It sends a request to a Domain Name System server, which translates the human-readable address you typed into a numerical address that computers use to find each other. Once your computer has that numerical address, it sends a request to the server at that address asking for the files that make up the webpage. The server receives the request, retrieves the files, and sends them back to your browser. Your browser then reads those files and assembles them into the page you see on your screen.

## What a Server Is
A server is a computer that waits for requests and responds to them. It is always on, always connected to the internet, and dedicated to the job of receiving requests and sending back the information those requests asked for. When you visit a website, you are communicating with a server somewhere in the world that is storing that website's files and sending them to anyone who asks for them. The word server describes what the computer does, not what it looks like. A server can be a small machine in a closet or one of thousands of machines inside a massive data center.

## What a Request and Response Are
Every interaction on the internet follows the same pattern. A client, which is any device that initiates communication, sends a request. A server receives that request, processes it, and sends back a response. When you open a webpage, your browser is the client. It sends a request for the files that make up that page. The server sends back a response containing those files. This back and forth happens every time you click a link, submit a form, load an image, or stream a video. The entire internet runs on this request and response pattern.

## Why This Matters for CloudFront
CloudFront sits between the client and the origin server. Instead of every request traveling all the way to the origin server where the files are stored, CloudFront intercepts the request at the nearest edge location and serves a cached copy of the files from there. The client still sends a request and receives a response. But the response comes from a server that is physically closer to the user, which means the files arrive faster. Understanding the request and response pattern is what makes CloudFront's role in that chain clear. It does not change how the internet works. It just makes the journey shorter.

## Key Terms

Internet — a global network of computers connected through physical cables, fiber optic lines, and wireless signals that allows them to send information to each other regardless of location.

URL — a human-readable address that identifies the location of a specific resource on the internet, such as a webpage or a file.

Domain Name System — a service that translates human-readable addresses like website names into numerical addresses that computers use to find each other on the internet.

IP address — a numerical address that identifies a specific device or server on the internet, used by computers to locate and communicate with each other.

Client — any device that initiates a request on the internet, such as a browser on a laptop or a phone loading a webpage.

Server — a computer that receives requests from clients and sends back the information or files those requests asked for.

Request — a message sent by a client to a server asking for specific information or files.

Response — the information or files a server sends back to a client after receiving and processing a request.

Cache — a temporary storage location where copies of files are kept so they can be served to future requests faster without going back to the original source.
