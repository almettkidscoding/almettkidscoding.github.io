---
title: "Easy chatbot implementation"
date: 2019-06-04T16:38:20+08:00
weight: 1
pre: "<b>1. </b>"
chapter: false
---

### Chatbot architecture

![](/images/chatbot.jpg)

#### Step 1: Open `Sublime Text` editor, `File` -> `New File` create a Python file `chatbot.py`.

#### Step 2: Import library

Import random library

	import random

#### Step 3: Specify greetings

Create a Python list, specify greetings that we start the conversation with chatbot.

	greetings = ['hola', 'hello', 'hi', 'Hi', 'hey!','hey']

#### Step 4: Specify chatbot greetings

Presumably, chatbot replys randomly to our greetings. Therefor `chatbot_greeting` variable carrys random value.

	chatbot_greeting = random.choice(greetings)

#### Step 5: Specify questions and responses

Specify list of questions and answers.

	greetings = ['hola', 'hello', 'hi', 'Hi', 'hey!','hey']
	responses = ['Okay',"I'm fine"]

#### Step 6: Specify the workflow

Workflow is where the code runs in expected order.

	while True:
		userInput = input(">>> ")
		if userInput in greetings:
			print(random_greeting)
		elif userInput in question:
			print(chatbot_response)
		else:
			print("I did not understand what you said")

#### Step 7: Wrap the code together

	import random

	greetings = ['hola', 'hello', 'hi', 'Hi', 'hey!','hey']
	chatbot_greeting = random.choice(greetings)

	question = ['How are you?','How are you doing?']
	responses = ['Okay',"I'm fine"]
	chatbot_response = random.choice(responses)


	while True:
		userInput = input(">>> ")
		if userInput in greetings:
			print(random_greeting)
		elif userInput in question:
			print(chatbot_response)
		else:
			print("I did not understand what you said")


