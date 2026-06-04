<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-secretsmanager)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

In 🔎 Step #1, we'll take a look at a simple web app that lists S3 buckets, clone it to our computer, and set it up to hardcode AWS credentials.

In 🍴 Step #2, we'll see what happens when we share this code (with the credentials hardcoded!) publicly on GitHub.

In 🔒 Step #3, we'll secure the credentials using AWS Secrets Manager.

In 📝 Step #4, we'll update the web app code to use the credentials from Secrets Manager.

In ⬆️ Step #5, we'll try share the code on GitHub again, and see how you can wipe your repository clean of all the hardcoded credentials!

### Tools and concepts

💡 Apply security best practices for managing credentials in code

🔍 Understand GitHub's secret scanning feature and why it's important

🔑 Use AWS Secrets Manager to securely store and manage AWS credentials



🔄 Retrieve secrets programmatically in Python using the AWS SDK (boto3)

🧹 Clean up sensitive data from Git commit history by rebasing and handling merge conflicts

### Project reflection

This project took me a while as it took time for the configurations and the different errors i was facing.

I chose to do this project today because I wanted to know more about AWS KMS and secrets manager. Bonus was getting to work with git hub fork and rebase.

---

## Hardcoding credentials

Exposing your AWS credentials publicly is a major security risk and is extremely unsafe for production applications. Once someone else gets access to your credentials, they can use them to access your AWS account, delete resources, steal data, and cause damage.

It's not just AWS credentials; database passwords, API keys for other services, and any kind of secret should never be directly embedded in your code.

These are example access keys for AWS - we're going to imagine that these are real AWS credentials that would give someone access to your AWS account!

We're using these test credentials as it's easier and safer to use than real credentials that would expose your account to security risks. Because these credentials are fake, putting them in config.py won't actually let your web app work (you won't see this web app display your S3 buckets' names).

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

This command uses pip, the Python package installer, to install all the libraries listed in requirements.txt. In our case, this will install boto3, FastAPI, and other necessary packages.

When I first ran the app, I ran into an error {"error":"An error occurred (InvalidAccessKeyId) when calling the ListBuckets operation: The AWS Access Key Id you provided does not exist in our records."}

This error means the AWS Access Key ID provided for the web app is not valid. Our app is running, but it can't access your AWS account because it doesn't have valid credentials!

This is because we are using the placeholder credentials in config.py, which are not real AWS credentials.



To resolve the 'InvalidAccessKeyId' error, I updated the app's configuration with real credentials, from the IAM user security credentials for the access key.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

In this project, the whole point of forking was to simulate making your code public — so we could see what happens when you try to push code containing AWS credentials to a public repository. This is what triggered GitHub's secret scanning to block the push! 🛡️

git init - initialize Git in your local project directory.
git remote add origin <your-forked-repo-url> - to connect your local repository to your forked repository on GitHub:

trying to push to a repository that already has a remote named "origin". When we cloned the original repository, Git automatically set up a remote named "origin" for us that points to the original repository.
Let's change the existing remote "origin" to the new forked repository.

git remote set-url origin <your-forked-repo-url>
git remote -v - verify that the remote "origin" was set up correctly
git add . - Stage all the changes you've made in your local project 
git commit -m "Updated config.py with hardcoded credentials" - Committing in Git saves a snapshot of your changes.
git push -u origin main = This command uploads your code to the "main" branch of your "origin" remote.




GitHub detected that you are trying to push code that contains an AWS Access Key ID and Secret Access Key in config.py. This is a great security feature from GitHub to prevent accidental exposure of secrets!

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

AWS Secrets Manager is a service that helps you securely store and manage secrets, such as database credentials, API keys, and other sensitive information. Think of it as a digital vault for your secrets.

Secrets Manager encrypts your secrets and allows you to retrieve them programmatically in your applications, without hardcoding them in your code. It also offers features like secret rotation and auditing to further enhance security.

Secrets Manager can store various types of secrets, including:

Database credentials: Usernames and passwords for databases like MySQL, PostgreSQL, SQL Server, etc.

API keys: API keys for accessing third-party services.

OAuth tokens: Tokens for authentication and authorization.

Any other sensitive information: You can store any text-based secret in Secrets Manager.

Secret rotation is the process of automatically changing your secrets on a regular schedule. This is a security best practice because it reduces the risk of compromised credentials. If a secret is compromised, it will only be valid for a limited time before it's automatically rotated.

Secrets Manager can automatically rotate secrets for databases and other services. You can also configure custom rotation for other types of secrets.

Secret rotation is best for high-risk credentials like database passwords, privileged API keys, and service account credentials. These types of secrets, if compromised, could give attackers access to sensitive data or critical systems, so regular rotation helps limit the damage window.

 AWS Secrets Manager makes it easy for developers to integrate with their applications in a few key ways:

Ready-to-use code snippets — When you create a secret, Secrets Manager provides sample code in multiple languages (Python, Java, JavaScript, .NET, etc.) showing exactly how to retrieve your secret. You can copy-paste this directly into your app with minimal changes.

Programmatic retrieval via SDKs — Using an SDK like boto3 (for Python), your app can fetch secrets at runtime with just a few lines of code. Instead of reading credentials from a config file, your app calls Secrets Manager's API to get them securely.

Key-value pair structure — Secrets are stored as key-value pairs, making it simple for your app to grab exactly the value it needs. For example, your app can request just the AWS_ACCESS_KEY_ID or AWS_SECRET_ACCESS_KEY individually.

No code changes for secret updates — Since your app fetches secrets dynamically, you can update or rotate a secret in Secrets Mana

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

transform our config.py file from a security risk into a secure, professional piece of code. Instead of having our AWS credentials just sitting there in plain text it will use the sample code from Secrets Manager to fetch them securely.

These lines are responsible for actually retrieving the credentials from the secret and assigning them to the AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, and AWS_REGION variables that our app.py code expects:

secret_json = json.loads(get_secret()): This line calls the get_secret() function to retrieve the secret from Secrets Manager. The secret is returned as a JSON string, so we use json.loads() to parse it into a Python dictionary.

AWS_ACCESS_KEY_ID = secret_json['AWS_ACCESS_KEY_ID']: This line extracts the value of the AWS_ACCESS_KEY_ID key from the secret_json dictionary and assigns it to the AWS_ACCESS_KEY_ID variable.

AWS_SECRET_ACCESS_KEY = secret_json['AWS_SECRET_ACCESS_KEY']: This line does the same for the AWS_SECRET_ACCESS_KEY.

AWS_REGION = region_name: This line sets the AWS_REGION variable to the region_name we defined earlier.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

git rebase starts a rebase session, which means rewriting your commit history.

The -i flag makes it interactive, meaning you can edit the list of commits to be rebased.

--root tells us that the rebase should start from the very first commit in your repository's history. This is useful when you need to modify commits from the beginning of your project.
we need to rewrite the history to completely remove the commit that had the hardcoded credentials.

When Git detects conflicting changes in a file, it adds special markers to show you exactly where the conflicts are:

<<<<<<< HEAD marks the beginning of your current version

======= separates the two conflicting versions

>>>>>>> feature-branch marks the end of the incoming changes

To resolve the conflict, you need to choose which version to keep and remove all these markers.

check on GitHub that the commit history is updated and your config.py file doesn't contain any sensitive information.

Head to your forked repository on GitHub.
Config.py is clean of any hardcoded credentials. It only has the code to retrieve credentials from AWS Secrets Manager!

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---
