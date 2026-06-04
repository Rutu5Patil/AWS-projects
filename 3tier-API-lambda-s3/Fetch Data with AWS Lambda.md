<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Fetch Data with AWS Lambda

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-lambda)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Fetch Data with AWS Lambda

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_p9thryj2)

---

## Introducing Today's Project!

🗄️ Create a database table to store user data.

🐑 Create a serverless function to retrieve user data.

📝 Write tests to validate if your function can fetch data from DynamoDB.

🔑 Secure your serverless function with proper permissions.

💎 Secure your database with an inline policy



### Tools and concepts

🗄️ Set up a DynamoDB database.

🐑 Create and configure an AWS Lambda function.

💻 Write code to interact with DynamoDB using the AWS SDK.

🧪 Test your Lambda function.

💎 Tighten permission settings for your Lambda function.

### Project reflection

This project took me approximately half an hour as half the work was done in the last project.

I chose to do this project today because I want to learn about 3-tier architecture.

---

## Project Setup

To set up my project, I created a database using DynamoDB. A partition key is the heart of how DynamoDB organizes data. Think of it as a label that you can use to group similar items. Under the hood, the partition key is how DynamoDB spreads out your data across different servers for quick access and efficient querying.

Every item in your table must have a unique partition key.

This JSON code defines a new item for our UserData table.

This item represents a user with...





A userId of 1



A name of Test User, and



An email of test@example.com

DynamoDB is schemaless, meaning you can add attributes as you need, and every item in your database can have a different set of attributes. This flexibility is one of the key benefits of using a NoSQL database like DynamoDB.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_a112c3d5)

### AWS Lambda

AWS Lambda is a service that lets you run code without needing to manage any computers/servers - Lambda will manage them for you.

Lambda runs your code only when you need it to (so you're not paying for any idle time).

It also scales automatically, from a few requests per day to thousands per second - all you need to do is supply your code in one of the languages that Lambda supports.

A Lambda function is a piece of code that you run in AWS Lambda.

---

## AWS Lambda Function

An execution role is an IAM role for your Lambda function. It defines what the function is allowed to do, e.g. accessing other AWS services like DynamoDB.

By default, AWS creates a role for Lambda with basic permissions for writing logs to CloudWatch. That's why you could see an error message when you tested your Lambda function!

The first half of the code uses the AWS SDK for JavaScript to interact with DynamoDB.

It takes a userId as input, grabs the corresponding data from the UserData table, and returns it to you.

The second half of the code (i.e. beginning with try {) handles potential errors during the database operation, so you get a tailored error message that tells you what went wrong.

The AWS Software Development Kit (SDK) is a set of tools that let developers build apps that interact with AWS.

Think of it like a library of pre-written code that lets you use AWS services without having to write all the code yourself. It gives you functions and classes that simplify common tasks, like creating an S3 bucket or launching an EC2 instance.

There's a different SDK for different programming languages or platforms, and JavaScript is one of them! Your code uses the AWS SDK to use pre-written functions for communicating with DynamoDB and getting data from a table. Without the SDK, you'd have to manually write the code to interact with AWS, which would be much more complex and error-prone.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_a1b2c3d5)

---

## Function Testing

In this test, we're asking our Lambda function to search for an item in our DynamoDB table. The item needs to have a userID of 1

By using JSON to input test data, we ensure it's in a format that’s easy for Lambda to understand and work with.

Even though we created an execution role for our Lambda function, we haven't given it explicit permission to access our DynamoDB table. This means DynamoDB is currently blocking off our Lambda function from reading the table's items!

Because Lambda can't read any items, it has no choice but to tell us that its access was denied.


The "success" message simply means the function itself could run (there are no errors with the code), it doesn't mean the function achieved what you want it to do

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_u1v2w3x4)

---

## Function Permissions

Reviewing the error message tells us exactly which permissions the Lambda function lacks.

To solve the access denied error, we can add a permission policy that give us the permissions we're lacking!

AWSLambdaDynamoDBExecutionRole gives your Lambda function the permissions to see a DynamoDB stream i.e. a live news feed of changes to your tables (like new, updated, or deleted items) in the last 24 hours.

AWSLambdaInvocation-DynamoDB is used to automatically trigger your Lambda functions in response to events captured in the DynamoDB stream. You'd use this in apps where you need immediate action based on data changes - for example, if a user should get a notification when they add a new product to their in-app shopping cart.

AmazonDynamoDBFullAccess lets you do everything with DynamoDB, like creating, deleting, and managing tables. It also lets you read and write data.

But, if your Lambda function only needs to read data, you don't need this level of access. Granting this permission when you don't need it can make your resources less secure. For example, if someone gets unauthorized access to your function, they could manipulate or delete crucial data by editing your function, which could disrupt your service or lead to data loss.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_3ethryj2)

---

## Final Testing and Reflection

When you see a successful result in AWS Lambda, it means your function successfully executed its code from start to finish without running into any unhandled crashes or errors.

No more undefined variables: Before, the code was looking for event.queryStringParameters.userId. Because event.queryStringParameters did not exist in your test JSON, JavaScript crashed because it cannot read properties of something that is undefined. Now, the code looks for event.userId directly, which matches your test event perfectly.

Graceful execution: Because the code can now find and read the user ID, it was able to proceed with its main task—like querying your DynamoDB database—and return a completed response.

Lambda's definition of "Success": When AWS Lambda displays that green "succeeded" status, it simply means the handler function reached its final return statement (or resolved its promise) without throwing any unhandled exceptions.

Lambda can be a serverless backend for web apps, grabbing data from DynamoDB when a user logs in or interacts with your app. For example...

Lambda can help customers find products, get product information or see their order history by fetching data from DynamoDB.

Lambda can help social media apps fetch user profiles or automatically retrieve all content (e.g. videos or images) linked with a profile.

Lambda can help news sites or blogs fetch articles based on user queries.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_p9thryj2)

---

## Enahancing Security

While AmazonDynamoDBReadOnlyAccess grants read-only access to all your DynamoDB tables, an inline policy allows for more granular control. In this case, we only want our Lambda function to access the UserData table, so an inline policy is more secure.

It's just like the reason why we gave our Lambda function ReadOnlyAccess instead of full access earlier in this project. We're now narrowing permissions even more - let's take out the unnecessary permissions that ReadOnlyAccess is still giving us.

With the visual editor, you're using a more beginner friendly, guided interface that breaks up policy writing into checkboxes and dropdowns.

With JSON, you're writing the policy directly without guidance. It's more challenging, but is a more efficient solution if you're familiar with policy writing.

back to your Lambda function's Test tab.

Select Test again.

You should be able to see the results for your DyanamoDB table's items again.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-lambda_1qthryj2)

---

---
