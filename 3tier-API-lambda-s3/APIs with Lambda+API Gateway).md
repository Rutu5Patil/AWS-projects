<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# APIs with Lambda + API Gateway

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-api)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_c9d0e1f2)

---

## Introducing Today's Project!

⚙️ Develop a serverless Lambda function.

🚪 Configure an API with API Gateway.

🔌 Connect Lambda with API Gateway.

💎 Write JSON documentation for your API.



### Tools and concepts

🐑 Create and configure a Lambda function.

🚪 Set up and configure an API in API Gateway.

🧱 Create resources and methods within your API.

🚀 Deploy your API to a live stage.


### Project reflection

This project took me approximately two hours as i ad to read and understand the settings, to get a better idea of the infrastructure.

I chose to do this project today because I wanted to set up and understand the layers of a three-tier architecture.

---

## Lambda functions

The function will fetch data from a database and return it to the user. This is a very common use case in web apps.

For example, when a user searches for a product in an online shop, the website's backend needs to query the product database, find the relevant product, and send its details back to the user's browser as swiftly as possible.

This code sets up a Lambda function that retrieves data from a DynamoDB table.

It looks for specific user data based on a 'userId' and returns that data. If there's an error e.g. the userId doesn't exist in the database, it returns an error message.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_a1b2c3d5)

---

## API Gateway

API Gateway supports different types of APIs, like REST, HTTP, and WebSocket. Each type is suited for different use cases, whether it’s maintaining a standard web API (REST), providing real-time capabilities (WebSocket), or routing requests (HTTP).

Amazon API Gateway is an AWS service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

It manages incoming traffic, directing them to the correct services, and makes sure only authorized requests get through.

API Gateway acts as the "front door" to our Lambda function. It receives requests and then forwards them to Lambda functions for processing.

Lambda processes the request, then sends the response through the API Gateway back to the user.



Directly exposing Lambda functions to user requests isn't best practice, because Lambda doesn't have built in security or API management features.

API Gateway brings in authentication and authorization features, and advanced API management capabilities (e.g. request routing) that make your app more efficient.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_m3n4o5p6)

---

## API Resources and Methods

API resources are individual endpoints within your API that handle different parts of its functionality.

For example, an API for a messaging app might have separate resources for retrieving messages and for retrieving user profiles.

API methods define the actions you can perform on a resource.

They are based on standard HTTP methods, which are different commands that let you interact with data over the internet. For example:

GET to retrieve,

POST to add,

PUT to update, and

DELETE to remove data.

Method Type: GET, which is the standard HTTP command used when you want to retrieve or fetch data.

API Resource: /users, which acts as the specific endpoint path for user-related requests.

Integration Type: Integrated directly with your RetrieveUserData Lambda function.

Lambda Proxy Integration: This is switched on so that the entire request (like headers, query parameters, and paths) is passed directly to Lambda in its raw format, making it much easier for your function to process.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_c9d0e1f2)

---

## API Deployment

In API Gateway, a stage is a snapshot of your API at a specific point in time.

API Gateway lets you deploy different versions of your API to different stages. This way, you can easily control who accesses what version of your API and when.

Usually, developers work on new features or changes in a development stage of the API, test new features in the testing stage, then deploy in in the production stage.

The invoke URL is the URL where your API can be used.

In real world scenarios, developers use the prod stage's invoke URL into their live application's code, so users are using the live/production version of the API.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_3ethryj2)

---

## API Documentation

API documentation is a detailed description of an API's functionality, including its endpoints (e.g. /users), methods (e.g. GET), parameters (e.g. userId), and responses (e.g. errors or success response).

Good documentation is crucial for developers to understand how to use the API correctly and efficiently.

Selecting a stage when publishing documentation makes sure that your documentation is consistent with the API version deployed to that stage.

This means you can write different versions of documentation across different stages of your API lifecycle, such as development, testing, and production.

The other text in this file are documentation that API Gateway has automatically generated for you!

You can see metadata like your API's version and title, resources (/users), and methods (like GET) you can perform on these endpoints.

The main difference between the automatically generated documentation and the manually written part in your API is the level of customization and specificity in each section. In your written documentation, you can address specific questions, add insights, or guide the user through the API’s functionality in a more user-friendly way.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-compute-api_z9a0b1c2)

---

---
