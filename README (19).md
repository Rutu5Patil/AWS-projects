<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Website Delivery with CloudFront

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-cloudfront)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Website Delivery with CloudFront

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_1dddddwe)

---

## Introducing Today's Project!

🪣 Create a storage space in S3 for your website's files.

🌐 Set up CloudFront to distribute your website globally.

🔑 Manage permissions for both S3 and CloudFront.

💎 Compare different methods for hosting your website and analyze their performance.

### Tools and concepts

🪣 Create and manage S3 buckets.

⬆️ Upload files to S3.

🌐 Set up a CloudFront distribution for lightning-fast content delivery.

🔑 Secure your S3 bucket using Origin Access Identities.

💎 Compare S3 static website hosting with CloudFront.

### Project reflection

This project took me approximately one hour as the concept was easy and walkable.

I chose to do this project today because i wanted to know how cloud front works.

---

## Set Up S3 and Website Files

While the star AWS service in this project is CloudFront, CloudFront is not a storage solution. CloudFront is a content delivery network that simply hosts content that is stored somewhere else, like Amazon S3.

index.html is the main file for a website. It's where you organise the text, pictures, and everything that makes up your webpage.

style.css is where you write down the visual appearance of your website's HTML elements. It controls everything from font sizes and colors to layout designs, helping you keep a consistent style across your website.

script.js refers to a JavaScript file that adds interaction to your website. It's where you would write the instructions for making things on your website move or change when you click a button or submit a form.

I validated that my website files work by
Right-click on index.html.
Select Open With > select your preferred browser.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_qgo7wcd3)

---

## Exploring Amazon CloudFront

Amazon CloudFront is a Content Delivery Network (CDN), which means it speeds up the distribution of your static and dynamic web content, such as .html, .css, .js, and image files.

Caching is the process of storing copies of files in a cache, i.e. a temporary storage location, so that they can be accessed more quickly.

CloudFront caches your website content in multiple servers around the world. When a user requests content that you're serving with CloudFront, the request is routed to the edge location that provides the lowest latency (time delay), so content is delivered with the best possible performance.

A CloudFront distribution is a set of instructions that tells CloudFront how to deliver your content.

It specifies where your website's files are stored (called the origin), how they should be cached, and other delivery settings like security standards.

CloudFront settings help you control how your files are delivered from your storage (like S3) to users around the world. These settings include how CloudFront connects to your storage, who can access your files, and how quickly updates show up for users.

Most beginners use the recommended settings, which balance speed, security, and simplicity.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_qgo7wcdt)

---

## Handling Access Issues

We haven't given CloudFront permission to access our S3 bucket yet.

By default, S3 buckets are private. CloudFront needs explicit permission to access the files in your bucket.

My distribution's origin access settings were origin access settings(recommended).
This caused the access denied error because access is denied to CloudFront.

An origin access control (OAC) is a special user for CloudFront that prevents this. An OAC lets you keep your S3 bucket and objects not publicly accessible, while still making sure they can be accessed through CloudFront.

OAC also gives you granular control over how CloudFront accesses the content. For example, you can add other authentication or security settings to make sure only legitimate users can access your content.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_egrhntyu)

---

## Updating S3 Permissions

S3 blocks access by default — S3 buckets deny all public access unless explicitly allowed. CloudFront needs permission to read your objects — When a user requests content, 

CloudFront fetches it from your S3 bucket (the origin). Without the right bucket policy, CloudFront gets an Access Denied error and can't serve anything.

Origin Access Control (OAC) — CloudFront uses an Origin Access Control identity to authenticate requests to S3. The bucket policy must explicitly grant this OAC permission to perform s3:GetObject on your bucket's objects. By updating the bucket policy to only allow access from your CloudFront distribution, you ensure users can't bypass CloudFront and access S3 directly. 

The bucket policy is the "handshake" that tells S3, "Trust requests coming from this specific CloudFront distribution." Without it, the two services can't work together.

Creating an OAC automatically gives me a policy I could copy, which grants permission to access the bucket.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_eg98ntyu)

---

## S3 vs CloudFront for Hosting

For my project extension, I'm comparing Compare S3 vs CloudFront based on the hosted website's URLs, permission settings and performance.
I initially had an error with static website hosting because it was not enabled also public access is also denied.

Unchecking "Block all public access" doesn't actively grant permission to access the objects; it simply stops blocking all public access attempts.

By default, all objects in an S3 bucket are private, and simply removing the block doesn't change their access permissions.

The bucket policy, on the other hand, is needed to explicitly grant permissions. This policy specifies who is allowed (or denied) what actions.

When you added the bucket policy that allows public read access (s3:GetObject), you explicitly told AWS to allow anyone on the internet to read the files in the bucket.

I could finally see my S3-hosted website when I added the bucket policy to allow access. 

AccessObjects must be set to public — anyone on the internet can access them directly via the S3 URLObjects stay private — only CloudFront can access them via OACAccess ControlControlled via bucket policy that allows public read (s3:GetObject for everyone)

Controlled via bucket policy that only allows the CloudFront service principal with a specific distribution ARNBlock Public AccessMust be disabled to allow public accessCan stay enabled — 
CloudFront bypasses this through OACDirect S3 AccessAnyone can access files directly using the S3 website URLBlocked — users can only access content through the CloudFront URLSecurity RiskHigher — public bucket means anyone can download your files directlyLower — content is only served through CloudFront, giving you a single controlled entry point

In short:

S3 hosting = You open the front door to everyone 🚪

CloudFront + OAC = You lock the front door and give CloudFront a private key 🔐. Users can only get content through CloudFront, never d

---

## S3 vs CloudFront Load Times

On subsequent requests, CloudFront gets faster
After the first request, CloudFront has the file cached at the edge location. Now it can serve the content instantly without going back to S3. If you refreshed the CloudFront page multiple times, you might have noticed it getting faster after the first load.

When users are far from your S3 bucket's region — e.g., a user in the US accessing your Mumbai bucket. S3 would be slow, but CloudFront would serve from a nearby US edge location.

On repeat visits — cached content is served instantly from the edge.

At scale — when thousands of users worldwide are accessing your site simultaneously, CloudFront distributes the load across its global network instead of hammering a single S3 bucket.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-networks-cloudfront_12verpuh)

---

---
