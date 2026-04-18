# Technical Writing

This file defines the writing standard every document 
in this repository is held to. It is built from Google's 
Technical Writing courses, Microsoft's Style Guide, 
The Documentation Compendium, and the Diátaxis framework.

Every principle here includes a bad example and a good 
example so the standard is clear, not just stated.

---

## 1. Know Your Reader Before You Write

Before writing a single word, answer three questions:

- What does this person already know?
- What are they trying to do right now?
- What is the one thing standing between them 
  and that goal?

Every decision about what to include and what to leave 
out comes from those three questions.

❌ Written for no one in particular:
"Amazon S3 is an object storage service offering 
industry-leading scalability, data availability, 
security, and performance."

✅ Written for someone about to create their first bucket:
"S3 is where you store the files that make up your 
website. Before CloudFront can deliver your site to 
users around the world, it needs to know where those 
files live. That place is an S3 bucket."

---

## 2. Lead With the Problem, Not the Tool

Never open a document by defining a service or concept. 
Open by describing the situation that makes it necessary.

❌ Tool first:
"IAM stands for Identity and Access Management. It is 
an AWS service that allows you to manage access to 
AWS services and resources securely."

✅ Problem first:
"When you create an AWS account, one identity is 
generated automatically. It has unrestricted access 
to everything — every service, every resource, every 
billing setting. If someone gets that password, the 
damage they can do has no ceiling. IAM exists to 
solve this."

---

## 3. Use Active Voice

Active voice puts the subject before the action. 
The reader always knows who is doing what.

Google Technical Writing One states this directly: 
active voice is clearer, shorter, and easier to 
understand than passive voice.

❌ Passive voice:
"The bucket policy must be updated."
"MFA should be enabled on the root account."
"The distribution is configured by the engineer."

✅ Active voice:
"You update the bucket policy."
"You enable MFA on the root account."
"You configure the distribution."

The test: find the verb. Ask who is doing it. 
If the answer is not in the sentence, rewrite it.

---

## 4. Use Terms Consistently

Pick one word for one concept and use it everywhere 
in that document.

Google states: if you rename a term midway through 
a document, ideas stop compiling in the reader's head.

❌ Inconsistent:
"Create a bucket. The container needs a unique name. 
Your storage resource is now ready."

✅ Consistent:
"Create a bucket. The bucket needs a unique name. 
Your bucket is now ready."

If you introduce a shortened form of a term, do it 
once, clearly, and use that form for the rest of 
the document.

✅ Introducing a shortened form:
"**Origin Access Control** (**OAC**) restricts 
direct access to your S3 bucket. OAC ensures that 
only CloudFront can retrieve your files."

---

## 5. Define Every Acronym on First Use

Spell out the full term on first appearance. Put 
the acronym in parentheses immediately after. Bold 
both. Use the acronym from that point forward.

❌ Undefined acronym:
"Enable OAC before creating the distribution."

✅ Defined on first use:
"Enable **Origin Access Control** (**OAC**) before 
creating the distribution. OAC ensures that only 
CloudFront can retrieve files from your S3 bucket."

Only introduce an acronym if the full term is long 
and the acronym appears multiple times. Do not 
introduce an acronym you use only once.

---

## 6. Eliminate Ambiguous Pronouns

Pronouns like "it," "they," "this," and "that" cause 
confusion when the reader is not certain what they 
refer to.

Google's rule: if more than five words separate a 
noun from its pronoun, repeat the noun instead.

❌ Ambiguous:
"CloudFront requests the file from S3. It caches 
it at the edge location."

What does each "it" refer to? CloudFront? The file?

✅ Clear:
"CloudFront requests the file from S3. CloudFront 
then caches the file at the edge location."

❌ Ambiguous:
"Running the process configures permissions and 
generates a user ID. This lets users authenticate."

What does "this" refer to? The permissions? The 
user ID? Both?

✅ Clear:
"Running the process configures permissions and 
generates a user ID. The user ID lets users 
authenticate to the application."

---

## 7. One Idea Per Paragraph

The first sentence of every paragraph states the 
single point that paragraph makes. Every sentence 
after it supports, clarifies, or illustrates that 
point. When a new idea arrives, a new paragraph 
begins.

Google states: readers look to the opening sentence 
to decide whether the paragraph is relevant to them. 
If the first sentence does not announce the topic, 
readers have to read the whole paragraph to find out.

❌ Multiple ideas in one paragraph:
"CloudFront is a content delivery network that 
caches your content at edge locations around the 
world, which reduces latency for users who are far 
from your origin server, and it also integrates 
with ACM for SSL certificates so your site can 
serve traffic over HTTPS, and you can configure 
cache behaviors to control how different URL paths 
are handled."

✅ One idea per paragraph:
"CloudFront is a content delivery network. It 
stores copies of your website at locations around 
the world so users receive content from a server 
close to them.

This reduces how long it takes for a page to load. 
A user in Manila requesting a site hosted in 
Virginia receives it from Singapore, not Virginia.

Cache behaviors control how CloudFront handles 
different URL paths. You configure one behavior 
for static files and another for API requests."

---

## 8. One Sentence, One Idea

If a sentence contains more than one clause, split 
it. Long sentences hide unclear thinking.

❌ One sentence, multiple ideas:
"When a user requests a file that CloudFront has 
not yet cached at the edge location closest to them, 
it sends a request to the origin, which in this case 
is your S3 bucket, to retrieve the file, which it 
then caches at the edge location so that subsequent 
requests can be served without going back to the 
origin."

✅ One sentence, one idea:
"When a user requests a file, CloudFront checks 
the nearest edge location for a cached copy.

If the file is not there, CloudFront fetches it 
from the origin — your S3 bucket.

CloudFront caches the file at the edge location 
after retrieving it. The next user in that region 
receives it immediately."

---

## 9. Use Concrete Language

Replace every abstract word with something physical 
or measurable. Abstract language forces the reader 
to construct the meaning. Concrete language does 
that work for them.

❌ Abstract:
"IAM provides enhanced security capabilities for 
organizations implementing robust access control."

✅ Concrete:
"IAM prevents anyone from accessing your AWS 
account without explicit permission. Without it, 
anyone with your root password can delete every 
resource, access every file, and run up unlimited 
charges."

---

## 10. Use Lists and Tables Correctly

Google defines two types of lists with specific 
rules for each.

Use a **numbered list** when sequence matters — 
when doing step 3 before step 2 would cause an error.

✅ Numbered — order matters:
1. Create an S3 bucket.
2. Upload your website files.
3. Enable static website hosting.
4. Create a CloudFront distribution.

Use a **bulleted list** when sequence does not matter.

✅ Bulleted — order does not matter:
CloudFront reduces:
- Latency for global users
- Load on your origin server
- Bandwidth costs over time

Use a **table** when you are comparing multiple 
options across the same set of attributes.

✅ Table — comparing options:

| Storage Type | Best For         | Example    |
|--------------|------------------|------------|
| Object       | Files and media  | S3         |
| Block        | Operating systems| EBS        |
| File         | Shared access    | EFS        |

Never use a list for fewer than two items. Never 
use a numbered list when the steps can be done 
in any order.

---

## 11. Separate Concepts From Procedures

These are two completely different types of writing 
serving two different reader needs.

**Conceptual writing** answers: do I understand 
this well enough to use it?

**Procedural writing** answers: what do I do next?

Mixing them produces documentation that is neither 
good at explaining nor good at instructing.

❌ Mixed:
"An S3 bucket is a container for objects. To create 
one, go to the S3 console and click Create Bucket. 
Note that S3 is object storage, not a file system."

✅ Concept in the insight file:
"An S3 bucket is a container for files. Unlike a 
traditional file system, S3 does not use folders. 
Every file sits inside a bucket and is identified 
by a unique key."

✅ Procedure in the project file:
"To create a bucket:
1. Open the S3 console.
2. Click Create Bucket.
3. Enter a globally unique name.
4. Choose your region.
5. Leave Block Public Access enabled."

---

## 12. Make Implicit Knowledge Explicit

The most common documentation failure is assuming 
the reader shares context the writer never stated.

After writing any section, ask: what am I assuming 
the reader already knows? If there is any doubt 
about whether that assumption is safe, add one 
sentence of explanation.

❌ Implicit assumption:
"Create an Origin Access Control and attach it 
to your distribution."

This assumes the reader knows what OAC is, what 
a distribution is, and why any of this matters.

✅ Made explicit:
"By default, your S3 bucket is publicly accessible. 
Anyone who discovers the bucket URL can access your 
files directly, bypassing CloudFront entirely.

**Origin Access Control** (**OAC**) solves this. 
It tells S3 to only accept requests that come from 
your specific CloudFront distribution. Direct access 
to the bucket returns an Access Denied error.

To set this up, create an OAC in the CloudFront 
console, attach it to your distribution, and update 
your S3 bucket policy to allow only requests signed 
by that OAC."

---

## 13. Define Jargon Where It Appears

Define technical terms the first time they appear, 
in plain language, at the exact place in the 
sentence where they live.

Do not write a glossary at the bottom of the 
document. The definition and the term must arrive 
at the same moment.

❌ Jargon without definition:
"CloudFront uses TTL values in cache behaviors 
to determine how long objects remain cached at 
edge locations before revalidation."

✅ Defined inline:
"CloudFront keeps copies of your files at edge 
locations — servers positioned around the world 
close to your users. How long CloudFront holds 
a copy before checking the origin for a newer 
version is controlled by the TTL, or Time to Live. 
A TTL of 86400 seconds means CloudFront holds the 
copy for 24 hours before checking for updates."

---

## 14. Write in Second Person

Address the reader as "you" throughout. Never 
refer to the reader in third person.

Microsoft's Style Guide requires second person 
as the default for all technical documentation.

❌ Third person:
"Users should create an IAM admin user before 
proceeding. The administrator must never use 
the root account for daily tasks."

✅ Second person:
"You create an IAM admin user before proceeding. 
You never use the root account for daily tasks."

---

## 15. State the Scope at the Start

Every document opens with one sentence telling 
the reader what they will understand or be able 
to do by the end.

This is not a summary of the content. It is a 
statement of the outcome.

✅ Scope statement for the CloudFront file:
"By the end of this, you will understand what 
CloudFront is, how it moves content from your 
S3 bucket to users around the world, and what 
breaks when it is misconfigured."

---

## 16. Add a Table of Contents to Long Files

When a file covers multiple distinct components, 
add a table of contents directly below the scope 
statement. Google Technical Writing Two requires 
this for any document a reader might need to 
navigate rather than read linearly.

✅ Table of contents example:
## Contents
- What It Is
- Why It Exists
- How It Works
  - Distributions
  - Origins
  - Edge Locations
  - Cache Behaviors
- How It Connects To Other Services
- What Happens If It Is Misconfigured

---

## 17. Caption Every Diagram

Every image or diagram must have a caption that 
explains what it shows and why it matters.

A diagram without a caption forces the reader 
to interpret it themselves. A caption tells the 
reader exactly what to take away from it.

✅ Caption example:
"This diagram shows how a user request in Manila 
travels to a CloudFront edge location in Singapore 
on cache hit, bypassing the origin server in 
Virginia entirely. On cache miss, the request 
travels to the origin once, and the response is 
cached for subsequent users."

---

## 18. Write Alt Text for Every Image

Screen readers cannot see images. Every image 
needs alt text that conveys the same information 
the image conveys visually.

Google's accessibility course requires alt text 
that describes the content and purpose of the 
image, not just its appearance.

✅ Alt text example:
---

## 19. Avoid Directional Language

Never use phrases like "click the button on the 
left" or "see the section above." Screen readers 
and different screen sizes make directional 
references meaningless.

Reference sections by name instead.

❌ Directional:
"As shown above, the bucket policy controls access."

✅ Named:
"As shown in the S3 Access Control section, the 
bucket policy controls access."

---

## 20. Use Inclusive Language

Avoid terms that exclude or carry unintended meaning. 
This includes technical terms that have been 
deprecated across the industry.

Google's accessibility course requires inclusive 
language as a non-negotiable standard.

❌ Exclusive terms:
- master/slave → use primary/replica
- whitelist/blacklist → use allowlist/denylist
- sanity check → use consistency check

Never use color as the only way to communicate 
meaning in a diagram. Someone with color blindness 
must be able to read it.

---

## 21. End With Consequences, Not Summaries

Do not end a section by restating what it just said. 
End by telling the reader what happens if they 
ignore or misapply what they just read.

❌ Summary ending:
"In summary, Origin Access Control restricts access 
to your S3 bucket so that only CloudFront can 
retrieve files from it."

✅ Consequence ending:
"If you skip Origin Access Control, your S3 bucket 
is publicly accessible regardless of your CloudFront 
configuration. Anyone who discovers the bucket URL 
bypasses your CDN, your caching, and any security 
rules you have set up. Every file in that bucket 
is exposed."

---

## 22. Write the Friction Honestly

When you document something you built, describe 
what you expected to happen, what actually happened, 
and what that difference revealed about how the 
system works.

This principle comes from the Diátaxis framework 
and the open source documentation movement. It 
is the most useful thing you can give a reader 
because it is the one thing official documentation 
never provides.

✅ Friction written honestly:
"After enabling Origin Access Control, I loaded 
the website and received an Access Denied error. 
I expected it to work immediately.

The issue was that enabling OAC in CloudFront 
does not automatically update the S3 bucket 
policy. CloudFront generates the correct policy 
and displays it in the console, but you have to 
copy it and apply it to the bucket yourself.

What this revealed: CloudFront and S3 are 
separate services with separate permission 
systems. Connecting them requires explicit 
configuration on both sides."

---

## 23. Self-Edit Before Publishing

Google Technical Writing Two recommends reading 
your draft with fresh eyes before publishing. 
Use this checklist:

- [ ] Every sentence uses active voice
- [ ] Every term is used consistently throughout
- [ ] Every acronym is defined on first use
- [ ] No pronoun is ambiguous
- [ ] Every paragraph opens with its main point
- [ ] No sentence contains more than one idea
- [ ] Every image has a caption and alt text
- [ ] No directional language appears
- [ ] The scope is stated at the top
- [ ] The ending states consequences, not a summary

Read the document aloud as the final check. 
Every sentence that causes you to stumble needs 
to be rewritten. Every sentence that requires 
more than one breath needs to be split.

---

## 24. Keep Documentation Accurate Over Time

Outdated documentation with confident wrong 
information is worse than no documentation at all.

Every file that references the AWS console should 
include a note at the top stating when it was 
last verified. AWS updates its console frequently, 
and steps that were accurate six months ago may 
no longer match what the reader sees.

✅ Accuracy note at the top of a file:
"Last verified: April 2026. If console steps 
no longer match, check the official AWS 
documentation for the current flow."

---

## The Standard This Repository Holds

Every file in this repository is written for 
one specific reader at one specific moment. 
It leads with the problem. It uses active voice. 
It keeps one idea per paragraph and one idea per 
sentence. It uses consistent terminology. It 
defines every acronym and every piece of jargon 
where it appears. It separates concepts from 
procedures. It makes implicit knowledge explicit. 
It uses concrete language and concrete examples. 
It captions every diagram. It writes alt text 
for every image. It avoids directional language. 
It uses inclusive language. It ends with 
consequences. It documents friction honestly. 
It stays accurate over time.

These are not stylistic preferences. They are 
decisions made in service of the reader. A reader 
who understands something because of what you 
wrote is the only measure of whether the writing 
worked.
