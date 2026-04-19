# What AWS Is

> By the end of this, you will understand what AWS is,
> why it exists, and how it relates to everything you
> will build in this workshop.

## Contents
- What It Is
- Why It Exists
- How It Works
- The Four Categories You Need to Know
- Key Terms

## What It Is
AWS is a global network of millions of physical data centers, each housing servers, storage devices, and networking equipment that runs software, stores data, and delivers content to users anywhere in the world.

AWS gives users on-demand access to servers, storage, and networks over the Internet, without buying, building, or maintaining any physical hardware themselves.

Think of AWS like how customers order at a coffee shop. You tell the barista what you need, and the barista makes your order without you owning any of the machines or tools they use. In AWS, this illustrates the client-server model, where a user sends a request to the server, and the server fulfills the request made by the user.

Similarly, think about how you use water in your own home. You turn on the tap, and the water flows instantly. But you do not own the reservoir and pipes, nor build any of the underlying infrastructure by yourself. Instead, you pay only for the water you used, and when you need more, you just turn on the tap more. In AWS, you connect over the Internet where resources flow immediately, only requiring you to pay for what you actually use and request, eliminating your need to own and build the servers, storage, networks, and infrastructure by yourself.

## Why It Exists
Before AWS existed, running software, storing large data, processing information, and sending content across the Internet to users in different locations all relied on the same thing first, which was physical hardware that had to be purchased, installed, maintained, and paid for whether it was used or not.

This placed enormous physical, financial, and operational burdens on everyone who needed to carry out any of those operations, including individuals, companies, organizations, and governments.

Purchasing hardware equipment meant spending thousands or millions of dollars before knowing if all of it would be fully used. Paying for electricity and cooling bills for machines remained the same price, even if three machines were running at full capacity, or if eight sat completely idle. Buying or leasing dedicated physical spaces to house the servers for computing, storage for data, and networking for connectivity, along with industrial air conditioners to prevent the hardware infrastructure from overheating, and backup power generators to keep servers running during power outages and prevent catastrophic data loss, added another layer of cost before a single user could be served.

Once the hardware arrived, workers physically carried it into dedicated server rooms, lifted it into floor-to-ceiling metal racks, bolted it in place, and connected hundreds of power and network cables by hand. These rooms required industrial cooling systems running continuously to prevent the hardware from overheating, raised floors hiding thick bundles of cables underneath, and large battery systems to keep everything running during power outages until a diesel generator outside could take over. When a component failed — a fan, a hard drive, a power supply — a technician had to physically travel to the location, open the machine, and replace the broken part by hand.

Beyond the physical demands, the people responsible for maintaining all of that infrastructure spent most of their time on maintenance instead of building the products and services their organizations actually existed to create. Predicting how much capacity would be needed months or years in advance was guesswork — organizations that underestimated demand watched their systems crash when traffic spiked, while those that overestimated paid for hardware that sat idle consuming electricity without serving a single user. And when demand suddenly surged, there was no way to respond quickly — new hardware took weeks to arrive and days to install, by which point the moment had already passed.

AWS eliminated all of that by moving the hardware, the maintenance, the cooling, the power, and the capacity planning into its own global network of data centers — giving anyone access to the same resources over the internet, instantly, and only for as long as they needed them.

## How It Works
When a user opens a browser and types a URL, that request travels over the internet to the nearest AWS data center. The data center processes the request by retrieving a file, running a calculation, or serving a webpage, and sends the response back to the user in milliseconds. This is possible because AWS operates a global network of data centers connected to the internet, allowing anyone anywhere to access computing power, storage, and networking remotely without owning any of the physical infrastructure themselves. You request what you need, AWS fulfills it, and you pay only for what you used.

## The Four Categories You Need to Know
AWS organizes its services into four categories. Compute refers to the processing power that runs software and handles requests. Storage is where files and data live, holding everything from website files to databases and backups. Networking is how content moves from AWS data centers to the people requesting it, getting files, pages, and data to users anywhere in the world as fast as possible. Security controls who is allowed to access what, determining which users and services can read, write, or modify resources and under what conditions.

## Key Terms
Data center — a large building that houses servers, storage devices, and networking equipment used to store and process data for organizations and individuals around the world.

Server — a computer that receives requests from users and sends back the information or response they asked for.

Client-server model — the relationship between a user who sends a request and a server that fulfills it, the same way a customer orders from a barista who then makes the drink.

On-demand — available immediately when needed, used only for as long as needed, and paid for only based on what was actually consumed.

Content delivery network — a global network of servers that store copies of files close to users so content loads faster regardless of where the user is located.

Edge location — a server positioned in a specific geographic location that stores cached copies of content to reduce the distance data has to travel to reach the user.

Origin — the source where the original files are stored, from which a content delivery network retrieves content when it does not have a cached copy.

Caching — storing a copy of a file in a temporary location so future requests for the same file can be fulfilled faster without going back to the original source.
