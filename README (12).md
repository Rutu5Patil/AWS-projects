<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# 3-Tier E-Commerce Infrastructure

**Project Link:** [View Project](https://learn.nextwork.org/projects/be99ef92-72a5-4549-935b-cb706453e434)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_5e5ngqhk)

## Deploying a Production-Pattern 3-Tier AWS Infrastructure

### Project goals and architecture overview

A production-pattern 3-tier e-commerce infrastructure on AWS, deployed and monitored entirely with Terraform.

Tools and Services involved:-
A fully provisioned VPC with 6 subnets across 2 Availability Zones, separating public, private, and isolated network tiers.
Secure tier-to-tier traffic flow from an Application Load Balancer through EC2 instances to an isolated RDS database, enforced by security group chaining.
CloudWatch alarms monitoring all three tiers with SNS email notifications.
Replace the single EC2 instance with an Auto Scaling Group for automatic horizontal scaling.

## Structuring the Terraform Project

### Setting up the project foundation

Create the project directory and Terraform file structure.
Configure the AWS provider and define project variables.
Initialize Terraform and download the AWS provider plugin.

### Handling sensitive variables safely

The db_password is marked sensitive = true, so Terraform never prints it in plan or apply output.

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_7uzb06d1)

### Understanding the initialized project structure

Terraform initialised backend, the plugins, found and installed the latest version of hashicorp/aws.
Created the .terrafom directory. Created terrafom.lock.hcl file and to record the provider.

## Building the VPC and Networking Foundation

### Designing the network layer

Create a custom VPC with six subnets spread across two Availability Zones.
Configure gateways and route tables that control traffic flow for each tier.
Run terraform plan to verify the networking resources before deploying.

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_0wadmtg8)

### How the three subnet tiers control internet access

Route tables define where each subnet sends outbound traffic. Public subnets route to the Internet Gateway, private subnets route through a NAT Gateway for outbound-only access, and isolated subnets have no internet route at all.

## Enforcing Tier Isolation with Security Group Chaining

### Defining the security boundaries

Create three security groups in security.tf with strict inbound and outbound rules.
Chain each security group so it only accepts traffic from its adjacent tier.
Run terraform plan to verify the new resources.

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_eggqat27)

### How chaining enforces strict tier-to-tier communication

Each security group references the one in the tier above it: the app SG references the ALB SG, and the database SG references the app SG. Traffic can only flow from one tier to the next. A request from the internet can never skip the ALB and reach the database directly.

## Deploying the Load Balancer and App Tier

### Wiring the ALB to private EC2 instances

Create the ALB, target group, and listener in alb.tf.

Deploy an EC2 instance running a web server in compute.tf.

Wire the instance to the ALB and run terraform apply to provision everything.

### Traffic flow and instance protection

Traffic enters through the Application Load Balancer a it faces the internet in the public subnet, which forwards to the listner which sends to Target group that is the EC2 instance. The instance is protected because it is in the private subnet which connects to internet through NAT gateway.

### Verifying end-to-end traffic through the ALB

The ALB DNS name is http://ecommerce-3tier-alb-1064714838.ap-south-1.elb.amazonaws.com/
 Seeing the page proves that everything is working properly.

## Provisioning the Database Tier and Verifying End-to-End Flow

### Adding RDS MySQL in isolated subnets

Create an RDS MySQL database in isolated subnets with no internet access.
Verify end-to-end traffic from the internet through the ALB to the EC2 instance.
Add a Terraform output for the database endpoint.

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_7splk7kn)

### Security group chaining across all three tiers

While the RDS instance provisions, trace how each security group chains to the next. The ALB security group allows HTTP from the internet. The app security group allows HTTP only from the ALB security group. The database security group allows MySQL only from the app security group.

## Adding CloudWatch Monitoring Across All Tiers

### Setting up SNS notifications and metric alarms

Create an SNS topic and email subscription for alarm notifications.
Define CloudWatch metric alarms for the ALB, EC2, and RDS tiers.
Deploy the monitoring stack and verify alarms in the AWS Console.

### Comparing security chaining with alarm dimension patterns

Both use a “linked relationship” between AWS components, but for different purposes.

Security group chaining controls network traffic flow between tiers.
Example: ALB SG → App SG → DB SG. Each tier only accepts traffic from the previous tier’s security group.
Alarm dimensions connect monitoring data between components.
Example: the CloudWatch alarm links the ALB and Target Group using dimensions (LoadBalancer and TargetGroup) so AWS knows exactly which resources to monitor.

So, security groups create a security connection, while alarm dimensions create a monitoring association between related tiers.

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_v30wn2x0)

### What each alarm monitors and why

The ALB tier cares about whether healthy targets exist. The EC2 and RDS tiers care about CPU utilization. 

The treat_missing_data = "breaching" setting is important. If CloudWatch cannot get data about healthy hosts, it likely means the target group has no registered targets. That should trigger the alarm, not be silently ignored.

## Secret Mission: Adding Auto Scaling to the App Tier

![Image](https://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/be99ef92-72a5-4549-935b-cb706453e434_f2jxnfdz)

### How an ASG improves reliability over a single instance

An Auto Scaling Group solves this by managing a fleet of instances. It automatically replaces unhealthy ones and scales up when demand increases.

## Project Reflection

### Key tools and concepts learned

In this project
Built a complete 3-tier VPC with public, private, and isolated subnets across two Availability Zones, enforcing strict tier-to-tier isolation through security group chaining.

Deployed an end-to-end traffic flow from an Application Load Balancer through private EC2 instances to an RDS MySQL database in isolated subnets with zero internet access.

Set up CloudWatch alarms monitoring all three tiers with SNS email notifications, matching how production teams get alerted when something goes wrong.

Added an Auto Scaling Group to make the app tier horizontally scalable under load.
All this through Terraform.

### Time and challenges

It took time as the project was big and was to be done on Terraform. There was an error but it got solved eventually.

### Takeaways and next steps

This project was very helpful in understanding many concepts and connections.

---

*Built with [NextWork](https://learn.nextwork.org) - [View this project](https://learn.nextwork.org/projects/be99ef92-72a5-4549-935b-cb706453e434)*
