<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex1)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Build a Chatbot with Amazon Lex

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex1_505be5b8)

---

## Introducing Today's Project!

### Project overview

I am going to create a chatbot called BankerBot, designed for an imaginary banking service. This bot will greet users and be ready to handle conversations through voice or text.

### What is Amazon Lex?

Amazon Lex is an AWS service to build conversational AI or a chatbot to get common user queries and answer them accordingly.

### Key tools and concepts

Services I used were AWS Lex. Key concepts I learnt include setting up a bot giving inital responce and intents asking question or giving responce when it was not understood.

### Personal reflections

One thing I didn't expect in this project was taht it could be done in so few steps.

### Project timeline

This project took me approximately half an hour. It had few step but as the concept was new it took a little whaile to get to understand why few steps were used.

---

## Setting up a Lex chatbot

### Approach to chatbot setup

In this step, I will set up a bot using an AWS service called Amazon Lex.

### Chatbot creation process

I created my chatbot from scratch with Amazon Lex. Setting it up took me about 5 minutes.

### IAM role configuration

While creating my chatbot, I also created a role with basic permissions because Amazon Lex needs the permission to call other AWS services our your behalf.

### Intent classification confidence score

In terms of the intent classification confidence score, I kept the default value of 0.40. This means this threshold is like a minimum score for the chatbot to confidently understand what the user is trying to say.

Setting this to 0.4 means that the chatbot needs to be at least 40% confident that it understands what the user is asking to be able to give a response.

So if a user's input is ambiguous and your chatbot's confidence score is below 0.4, it'll throw an error message.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex1_97dc2351)

---

## Intents

In this step, I will train our bot on how to say hello.

### Creating my first intent

An intent is what the user is trying to achieve in their conversation with the chatbot. For example, checking a bank account balance; booking a flight; ordering food.

I created my first intent, WelcomeIntent, to greet and introduce the type of chatbot you are interacting with.

### Testing chatbot responses

I launched and tested my chatbot, which could respond successfully if I enter hi, Hello.

---

## Handling unrecognized inputs

My chatbot returned the error message 'Intent FallbackIntent is fulfilled' when I entered guide, yo as it did not know what i was asking for.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex1_505be5b8)

---

## Configuring FallbackIntent

When the chatbot doesn't understand the user, it falls back on the FallbackIntent and displays it. I am going to re-phrase that message so it's clearer to the user that your chatbot doesn't understand the user's request.

### When FallbackIntent triggers

FallbackIntent is a default intent in every chatbot that gets triggered when the chatbot is not sure what the user is asking for. not clear on the question.

I wanted to configure FallbackIntent to get the chat bot to specify to the user that they are not clear and to rephrase what they are asking for.

### My FallbackIntent configuration

To configure FallbackIntent, I clicked on the Message option on the closing responce on the fallback intent page.

I also added variations! What this means for an end user is that the bot will reply in different ways, so the user will feel that they are having a conversation.

---

## FallbackIntent with Variations

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex1_c4fc89af)

---

## Initial Responses

In this project extension, I'm about to add FallbackIntent with an initial response. Also, add variations to your initial response.

### Setting up initial responses

It send an initial response primarily for the Welcome Intent (or Greeting Intent) when a conversation starts, and for the Fallback Intent when user input is unclear.

### Initial response implementation

The initial response messages I set up are for the chatbot to make an initial statement that the user is not asking or saying something different and to give an exclamation.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex1_09bcb9701)

---

---
