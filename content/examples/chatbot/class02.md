---
title: "Smart chatbot design"
date: 2019-06-11T18:58:00+08:00
weight: 2
pre: "<b>2. </b>"
chapter: false
---

In today's class, we're going to build a smart Chatbot. A smart Chatbot can be trained with data sets and react to the question more efficiently.

Our smart Chatbot training is based on Chatterbot which is Python library that provides basic capabilities to train Chatbots.

#### Chatterbot architecture

![](/images/chatterbot_architecture.png)

### Step 1: Install Chatterbot to our local environment

1. Open Terminal application
2. Type `pip3 install chatterbot`
3. Wait for installation complete

### Step 2: Import Chatterbot libraries to our work environment

Open up `Sublime Text` editor to create Python file `chatbot_smart.py`.

### Step 3: Import Chatterbot libraries

	from chatterbot import ChatBot
	from chatterbot.trainers import ListTrainer	

- `chatterbot` is the main library of Chatterbot
- `chatterbot.trainers` is the trainer library inside Chatterbot

### Step 4: Define a new Chatbot instance

Define a new instance of Chatterbot called "Smart Bot".

	chatbot = ChatBot('Smart Bot')

### Step 5: Define a Chatbot trainer

Define a Chatbot trainer with the chatbot instance that we just defined.

	trainer = ListTrainer(chatbot)

### Step 6: Train our Chatbot

Train our Chatbot with conversational data sets. 

**Odd number of lines are your, even number of lines are the Robot.**

	trainer.train([
	    'Hello, how are you?',
	    'I am doing well.',
	    'That is good to hear.',
	    'Thank you',
	    '你好',
	    '你叫什么名字？',
	    '你好啊！',
	    '我叫蜘蛛侠'
	])

### Step 7: Chat workflow

Set up the chat workflow under a `while loop`.

	while True:
	request=input("You: ")
	response=chatbot.get_response(request)
	print("Bot: ", response)

### Step 8: Wrap the code all together

	from chatterbot import ChatBot
	from chatterbot.trainers import ListTrainer

	chatbot = ChatBot('Smart Bot')

	trainer = ListTrainer(chatbot)

	trainer.train([
	    'Hello, how are you?',
	    'I am doing well.',
	    'That is good to hear.',
	    'Thank you',
	    '你好',
	    '你叫什么名字？',
	    '你好啊！',
	    '我叫蜘蛛侠'
	])

	while True:
		request=input("You: ")
		response=chatbot.get_response(request)
		print("Bot: ", response)
