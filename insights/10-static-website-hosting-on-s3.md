# Static Website Hosting on S3

> By the end of this, you will understand how S3 serves
> website files, what the index document setting does,
> and why CloudFront with OAC is the preferred approach
> over making a bucket fully public.

## Contents
- What Static Website Hosting on S3 Is
- Why It Exists
- How It Works
- The Index Document Setting
- The Two Ways to Host a Static Website on S3
- Why CloudFront With OAC Is Preferred
- What Happens If the Bucket Is Made Public Instead
- Key Terms

## What Static Website Hosting on S3 Is
Static website hosting is a feature of S3 that configures a bucket to serve its contents as a website. When you enable it, S3 generates a public URL for your bucket that serves your files as web pages when a browser requests them. A user who visits that URL receives your index.html file in their browser, and the browser renders it as a webpage.

## Why It Exists
Hosting a website traditionally required a web server — a dedicated computer running server software that listened for incoming requests and responded with the appropriate files. Setting up, configuring, and maintaining a web server required technical expertise and ongoing effort. Static website hosting on S3 removes all of that. Your files are already stored in S3. Enabling static website hosting turns those files into a publicly accessible website without any server configuration.

## How It Works
When you enable static website hosting on a bucket, you specify an index document. The index document is the file S3 serves when someone visits the root URL of your website. In most cases this is index.html. When a user types your website's URL into a browser, S3 returns the index document and the browser renders it as a webpage.

You can also specify an error document. The error document is the file S3 serves when a user requests a page that does not exist. Without an error document, S3 returns a generic XML error message that is not useful to a visitor. With an error document, you can serve a custom page that guides the user back to working content.

## The Index Document Setting
The index document is the file S3 returns when a user visits the root URL of your website without specifying a particular file. When someone types your website address into a browser and presses enter, they are not asking for a specific file by name. They are asking for whatever should appear at the root of the site. The index document setting tells S3 which file to serve in that situation.

In almost every case the index document is index.html. This is a web convention that browsers and servers have followed for decades. When S3 receives a request for the root URL, it looks for the file named in the index document setting and returns it. If that file does not exist in the bucket, S3 returns an error instead of a webpage.

Setting the index document correctly is one of the first configuration steps when enabling static website hosting. If it is set to the wrong filename or left blank, visitors to your site will see an error instead of your homepage even if all 
your files are correctly uploaded to the bucket.

## The Two Ways to Host a Static Website on S3
There are two ways to host a static website using S3, and they behave differently in important ways.

The first is enabling static website hosting on the bucket and making the objects publicly accessible. This gives the bucket a website endpoint URL that serves your files over HTTP. Anyone who knows the URL can access your files directly from S3. This approach is simpler to configure but less secure because the bucket and its contents are publicly exposed.

The second is keeping the bucket private and using CloudFront with Origin Access Control to deliver the content. The bucket has no public access. Only CloudFront can read the files, and it does so using a signed request that S3 verifies before serving the content. Users access the website through the CloudFront URL, not directly from S3. This approach is more secure, adds HTTPS, and delivers content faster through CloudFront's global edge network.

## Why CloudFront With OAC Is Preferred
Keeping your S3 bucket private and using CloudFront with Origin Access Control is the approach AWS recommends for several reasons. The bucket contents are never directly exposed to the public internet. CloudFront adds HTTPS automatically when you attach a certificate. Content is delivered from edge locations around the world instead of from a single S3 region. And because CloudFront caches your files at edge locations, repeated requests are served without touching S3 at all, which reduces both latency and the cost of S3 data transfer.

## What Happens If the Bucket Is Made Public Instead
If you make your S3 bucket publicly accessible instead of using CloudFront with OAC, anyone who discovers the bucket URL can access your files directly, bypassing CloudFront entirely. This means your content is delivered without caching, without HTTPS, and from a single region rather than from the nearest edge location. It also means your bucket is exposed to the public internet, making it vulnerable to unauthorized access, hotlinking, and potentially significant data transfer costs if traffic is high.

## Key Terms
Static website hosting — an S3 feature that configures a bucket to serve its contents as a website, generating a public URL that returns files in response to browser requests.

Index document — the file S3 serves when a user visits the root URL of the website, typically index.html.

Error document — the file S3 serves when a user requests a resource that does not exist, used to display a custom error page instead of a generic XML error message.

Website endpoint — the public URL generated by S3 when static website hosting is enabled, through which the bucket's contents are accessible as a website.

Origin Access Control — the permission configuration that allows CloudFront to read from a private S3 bucket while preventing direct public access to the bucket.

HTTPS — a secure version of the HTTP protocol that encrypts data in transit between a user's browser and the server, protecting against interception and tampering.
