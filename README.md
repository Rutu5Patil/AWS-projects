<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-terraform1)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to automate the deployment of an S3 bucket.

 The goal is to...create s3 bucket without the use of the console.

### Tools and concepts

Services I used were... Key concepts I learnt include infrastructure as code, setting up terraform , configuring and running it, connectiong by using credentials, launching S3 bucket and adding object to it. Also destroying the terraform to delete the changes made.

### Project reflection

This project took me approximately...3hours The most challenging part was as terraform was a new concept for me it took time to get used to and add the deatails and learn the new concepts that is understand what i was doing exactly and documenting it for future reference. It was most rewarding to see the bucket being created and object being added on it own without using the console. understanding terraform in a more hands on way.

I chose to do this project today because i wanted to know about terraform, thankyou for making such a simple and guided project to help understand the concept easily. Something that would make learning with NextWork even better is if the projects had real world scenario problems or set up to make it more relatable.

---

## Introducing Terraform

Terraform is a tool to configure different cloud services using same text file.

Terraform is one of the most popular tools used for infrastructure as code (IaC), which is a practice of describing cloud setup in a file to run and build.

Terraform uses configuration files to... main.tf is..It is a blueprint of the infrastructure.




![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in Terraform stores its instructions in self-contained “blocks.” The advantage of doing this is By keeping each piece of your infrastructure in its own block, the file stays easy to read and you can tweak one part without touching the rest of your setup! like compartmentalizing.

### My main.tf configuration has three blocks

The first block indicates the cloud being used. The second block provisions the service which need to be set up and naming it.The third block manages service policy.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to see what all changes it provides . The documentation shows different set ups, policys, extensions.

I chose to customise my bucket by Tags are like labels:
Help organize resources
Used for billing, filtering, management
Example:
Environment = Dev → development environment

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

I ran 'terraform init' to...initialsise the set up

Next, I ran 'terraform plan' to...

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

When I tried to plan my Terraform configuration, I received an error message because it was not connect to a user.

To resolve my error, first I installed AWS CLI, which is command line tool for aws.
Connects to your AWS account using credentials
Sends requests to AWS services
Returns output in your terminal

I set up AWS access keys to connect to the user console in an encrypted way.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

I ran 'terraform apply' to run a plan and ask for confirmation before making any changes.  Running 'terraform apply' will affect my AWS account by making the changes mentioned in the main.tf file.

The sequence of running terraform init, plan, and apply is crucial because... initialsises the set up, plan is used for reviewing and apply is used to run the changes.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to... to add the image to the s3 bucket. Each aws_s3_object resource represents one object (one file). so for 2 images 2 blacks are needed/ or you can change the code to simplify the process.

We need to run terraform apply again because anytime you change your Terraform configuration. This will make sure the changes are correctly applied to your infrastructure.

To validate that I've updated my configuration successfully, I checked s3 bucket in the console. and the images were uploaded.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
