<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Multiple Slots in a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex5)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Build a Chatbot with Multiple Slots

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_67890123)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is an AWS service that lets you build chatbots and voice assistants.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to create a chatbot in the editor and also the visual builder.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was creating the project simply by using cloud formation.

### This project took me...

This project took me an hour 2 hour as i had to redo the project from the begenning steps/parts.

---

## TransferFunds

An intent I created for my chatbot was TransferFunds, which asks the user from which account type you want to transfer to which account type and what is the amount.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_67890123)

---

## Using multiple slots

For this intent, I had to use the same slot type twice. This is because they both used the same option of slottype.
possible for multiple slots to have the same slot type.

I also learnt how to create confirmation prompts, which asks the user to confirm if they want to do this task.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_97dc2351)

---

## Exploring Lex features

It shows every step in a conversation in a logical, chronological order.
You'll also see some blank 'ghost like' responses. These are recommendations for what you could add to your Intent set up and they're clickable!

You could also set up your intent using a visual builder! A visual builder shows the visual representation of the intent

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_12345678)

---

## AWS CloudFormation

AWS CloudFormation is service in which you can use a file that describes all the resources you want to create and their dependencies as code. Then, you can use that template to create, update, and delete the entire stack of resources you described, instead of managing your resources individually

I used CloudFormation to create bot add intents by uploading a file.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_c4fc89af)

---

## The final result!

Re-building my bot with CloudFormation took me 5 minutes.

There was an error after I deployed my bot! The error was a permission error.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_505be5b8)

---

## Using the visual builder

Using the visual builder, I added an automatic check balance if a transfer is done. the bot will ask the user if they want to check.

The new Get slot value card will trigger when the transfer is done and the closing response is invoked. This card will try to ask user for yes/no options for the question.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex5_9cac15cd4)

---

---
