# The AWS Console

> By the end of this, you will understand what the AWS
> Management Console is, how it is organized, how to
> navigate it, and what mistakes to avoid before you
> start the workshop.

## Contents
- What It Is
- How It Is Organized
- How to Navigate It
- Common Mistakes When Starting Out
- How It Applies in This Workshop
- Key Terms

## What It Is
The AWS Management Console is a web-based interface that lets you access, configure, and manage AWS services through a browser without writing a single line of code. It is the starting point for anyone building on AWS, giving you a visual way to create resources, adjust settings, monitor usage, and control who has access to what.

## How It Is Organized
The console is organized around services. At the top of the screen is a search bar where you can type the name of any AWS service and navigate directly to it. Below that is a navigation bar with shortcuts to recently visited services, your account settings, and the region selector. The main body of the page changes depending on which service you are working in, but the search bar and navigation bar remain consistent across every service.

Services in the console are grouped into categories that match the four categories you already know. Compute services like EC2 live in one group. Storage services like S3 live in another. Networking services like CloudFront and Route 53 live in a third. Security services like IAM live in a fourth. Knowing which category a service belongs to helps you find it faster when you are navigating the console for the first time.

## How to Navigate It
The fastest way to navigate the console is through the search bar at the top of the screen. Type the name of the service you need and it appears immediately in the results. Click it and you are taken directly to that service's dashboard.

Every service has its own dashboard with its own layout, but most follow a similar pattern. There is a list of resources you have already created on the left or in the center of the screen, and a button to create a new resource in the top right. When you click into a specific resource, you see its settings, its current status, and options to edit or delete it.

## Common Mistakes When Starting Out
The most common mistake beginners make in the console is working in the wrong region. Every resource you create in AWS belongs to a specific region, and the console only shows you the resources in the region you currently have selected. If you create an S3 bucket in Singapore and then switch to US East, that bucket will not appear in the list because you are now looking at a different region's resources. Always check the region selector in the top right corner of the screen before creating or looking for a resource.

The second most common mistake is using the root account for daily work. The root account is the email and password you used to sign up for AWS. It has unrestricted access to everything and should never be used for everyday tasks. Always log in as an IAM admin user instead.

## How It Applies in This Workshop
You will use the AWS Management Console for every step of the workshop. You will navigate to the S3 service to create a bucket and upload your website files. You will navigate to the CloudFront service to create a distribution and configure Origin Access Control. You will use the search bar at the top to move between services quickly. Before you start, confirm that your region selector shows the region closest to you, and that you are logged in as an IAM admin user and not the root account.

## Key Terms

##AWS Management Console## — the web-based interface where you access and manage AWS services through a browser.

##Region## — a geographic location where AWS operates data centers. Resources created in one region are only visible when that region is selected in the console.

##Region selector## — the dropdown in the top right corner of the console that shows which region you are currently working in and lets you switch between regions.

##Service dashboard## — the page that appears when you navigate to a specific AWS service, showing the resources you have created and options to create new ones.

##Root account## — the primary account created when you first sign up for AWS, identified by your email address. It has unrestricted access to everything and should never be used for daily tasks.

##IAM admin user## — a separate user account created through IAM with administrative permissions, used for everyday work instead of the root account.

##Search bar## — the input field at the top of the AWS console that lets you find and navigate to any service by name.
