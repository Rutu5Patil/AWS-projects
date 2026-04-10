<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect Amazon Lex with Lambda

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex3)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Connect Amazon Lex with Lambda

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex3_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a fully managed AWS service for building conversational AI interfaces into applications using voice and text.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to connect to lamda to calculate the balance.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was its making it easy to underatnd how different services are connected.

### This project took me...

This project took me half an hour.

---

## AWS Lambda Functions

AWS service that lets you run code in the cloud without needing to manage any computers/servers - Lambda will manage them for you.

AWS Lambda to generate random bank balance numbers.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex3_97dc2351)

---

## Chatbot Alias

An alias in Amazon Lex as a pointer for a specific version of your bot.
So when you're connecting Lex with other AWS services or your custom applications, those external resources will connect to an alias, which will point to the specific version of your bot that you want to use.

TestBotAlias is a default version of your bot that's made for testing or development.

To connect Lambda with my BankerBot, I visited my bot's TestBotAlias and, on the Languages panel, click English (US).

A Lambda function panel pops up. This panel lets you associate a Lambda function to this TestBotAlias version of your bot.

For Source, choose your Lambda function BankingBotEnglish.Leave the Lambda function version or alias field at the default $LATEST.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex3_c4fc89af)

---

## Code Hooks

Code hooks help you connect your chatbot to custom Lambda functions for doing specific tasks during a conversation.

They're used to handle more complex actions that the basic chatbot setup can't do on its own, like checking data from a database or making decisions based on past conversations.

Essentially, code hooks make your chatbot smarter and more useful by allowing it to perform these extra steps seamlessly during chats.

The bot has all the information it needs and moves to fulfilment. This is where it will use the Lambda function to get the account balance and pass it back to the user.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex3_505be5b9)

---

## The final result!

I've set up my chatbot to trigger Lambda and return a random dollar figure when the user inputs the account type and correct date.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex3_505be5b8)

---

## Customizing the Lambda function

---

---
