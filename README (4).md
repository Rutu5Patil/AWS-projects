<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Save User Info with a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex4)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Save User Info with a Lex Chatbot

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a fully managed AWS service for building conversational AI interfaces into applications using voice and text.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to to add anothe intent and copy te data to make lex remember the previous user data for a short amount of time to find more information.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was so many steps are intermingled.

### This project took me...

This project took me a while.

---

## Context Tags

Context tags in Amazon Lex are used to store and check for specific information across different parts of a conversation. They help save the user from having to repeat certain information

Output context tag: This tells the chatbot to remember certain details after an intent is finished.
Input context tag: This checks if specific details are already available before an intent activates. 

I created a context tag called CheckBalance Intent. This tag stores information about the balance in a users account.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_97dc2351)

---

## FollowUpCheckBalance

I created a new intent called FollowupCheckBalance. The purpose of this intent is to check if there is a follow-up question.

FollowupCheckBalance is connected to CheckBalance as in the context option it is connected to contextCheckBalance and in the default option of slot dateofBirth in FCB in the advanced section we have added the link between the two. to save the user date, if there is a follow up question.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_12345678)

---

## Input Context Tag

the users dob is carried over from checkbalance to find the data for the same user of another account.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_c4fc89af)

---

## The final result!

To see the context tags and followup intent in action, I just asked to check and accounttype.

If FollowupCheckBalance is triggered without context in Amazon Lex, it usually means the bot doesn’t have the required session data (slots, intent state, or prior conversation flow). This can cause errors or unexpected behavior.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_505be5b8)

---

## Managing context expiry

An extension for this project is to manage contextCheckBalance's context expiry, which means how long your bot will remember information for. 

changed the time gear icon in the contextCheckBalance option.



A long context expiry window would be helpful when the user has many questions, or lot of information is to be given. A shorter context expiry window would be helpful when sensitive data is handeled.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex4_81b763822)

---

---
