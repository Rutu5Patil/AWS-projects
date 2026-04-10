<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Add Custom Slots to a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex2)

**Author:** naru uzu  
**Email:** rutu13patil@gmail.com

---

## Add Custom Slots to a Lex Chatbot

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex2_c4fc89af)

---

## Introducing Today's Project!

In today's project, I used Amazon Lex to add slots and intent to the chatbot. so user could enter the account type and dob.

### What is Amazon Lex?

Amazon Lex is an AWS service to build conversational AI or a chatbot to get common user queries and answer them accordingly.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was getting to interact directly while working only. steps are easy but have to be done in the same format if you do differently some mistakes happen which you can resolve but ti takes time.

### This project took me...

It did take a while as i had encountered some error so had to re do the steps a few times.

---

## Slots

Slots are pieces of information that a chatbot needs to complete a user's request. Think of them as blanks that need to be filled in a form.

By adding custom slots in utterances, my chatbot's users can ask the same question differently, but the chatbot will understand that and get back to the user.

In this project, I created a custom slot type to to fit the users specific needs, which is related to the banking system.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex2_97dc2351)

---

## Connecting slots with intents

Restrict to slot values makes sure that only the values that you specify will count as a valid accountType!

Otherwise, Amazon Lex might use machine learning to accept other values that it frequently encounters from users.

I associated my custom slot with CheckBalance, which takes users' info about their account type and then asks their birth date to find their account and check the alance to relay it to them.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex2_c4fc89af)

---

## Slot values in utterances

I created a new intent for checking user's bank account balance.

Add slots in the intent, so Lex can store the user's bank account type and birthday.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex2_505be5b8)

---

## Handling failures in slot values

I added variations for the dateOfBirth slot prompt, such as "Sorry, that wasn't clear to me. What's your date of birth?" and "write a valid date!!!!!!!! "The messages play in order, so my end user will see message 1 then 2 then lastly 3.

![Image](http://learn.nextwork.org/content_rose_beautiful_white_sapote/uploads/aws-ai-lex2_a028bc8d2)

---

---
