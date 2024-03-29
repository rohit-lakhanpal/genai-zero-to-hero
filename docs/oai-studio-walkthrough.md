# Guide to Azure OpenAI Studio

## Introduction

Let's talk about the magic of Generative AI and how it's changing the game for everyone, not just the tech wizards among us. Imagine having a tool that can write stories, summarize long articles, chat like a human, generate code, answer questions, and even make sense of heaps of data – including pictures. That's the cool stuff Generative AI is up to.

Now, imagine being able to play with this tech, no matter if you're a pro coder or someone who's just curious about what AI can do. That's where Azure OpenAI Studio comes in. It's this neat space where you can mess around with AI, try different things, and see what sticks, without needing to be an expert.

If you prefer to watch a video, here's a quick overview of Azure OpenAI Studio:

[![Overview of Azure OpenAI Studio](https://img.youtube.com/vi/LnGucwdmSu0/0.jpg)](https://www.youtube.com/watch?v=LnGucwdmSu0)


## What's Azure OpenAI Studio All About?

Azure OpenAI Studio isn't just about running AI models; it's a full-blown workshop for tinkering with AI, designed to be accessible for everyone. Here's a closer look at the key sections:

### The Toys You Get to Play With

- **Models**: At the heart of the studio are the AI models. You've got your heavyweight champs like GPT-4, capable of understanding and generating both text and code, and even handling images if you're using the GPT-4 Turbo with Vision. Then there's GPT-3.5-Turbo for when you need something lean but still powerful. For tasks like finding similarities in text, there's the text embedding models, and if you're into generating images or processing speech, DALL-E and Whisper have got you covered.

- **Chat**: When it comes to creating chatbots or any quick-reply system, the Chat Completions API is your go-to. It's all about giving you fast, concise answers perfect for chatbots, simple Q&A setups, or applications that need quick interactions without a lot of back-and-forth.

- **Assistants**:  If your project requires keeping track of longer conversations, diving deeper into topics, or managing more complex contexts, the Assistants API is what you need. It's designed for applications that need to remember what was said earlier in the conversation, making it ideal for more sophisticated virtual assistants or complex dialogue systems.

## Pre-Requisites

- **Azure Subscription**: You need an active Azure subscription to use Azure OpenAI Studio. If you don't have one, you can create a free account [here](https://azure.microsoft.com/en-us/free/).
- Apply for access to Azure OpenAI Service at [https://aka.ms/oai/access](https://aka.ms/oai/access). The form covers some questions about your use case, your expected usage, an overview of RAI Practices and Azure OpenAI's transparency note, which provide information and guidelines for responsible use of the service as well as system limitations that may be applicable to your scenario.
- **Azure OpenAI Service**: Once you have access to Azure OpenAI Service, you can create a resource in the Azure portal using this [guide](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/create-resource?pivots=web-portal).

## Let's Get Our Hands Dirty

Getting started with experiments in Azure OpenAI Studio is pretty straightforward. You don't need to wade through tech jargon or have a degree in computer science. Whether you're tweaking models to get them just right or trying out different ideas to see what the AI can do, Azure OpenAI Studio makes it easy and fun. 

These are some of the capabilities we can test out:
1. Writing aid
1. Summarisation
1. Chat and Conversation
1. Code Generation and Transformation
1. Question Answering
1. Reasoning over data (text, images, etc.)
1. Search

So, why not jump in and start playing with AI? 

### Experiments using Chat Completions:

#### Writing Aid:

Example 1:

- **System Prompt**:
  
  ```plaintext
  Generate 5 product names using provided product descriptions and seed words.
  Ensure names highlight product features, appeal internationally, and evoke positivity.
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  Generate product name ideas for a yet to be launched wearable health device that will allow users to monitor their health and wellness in real-time using AI and share their health metrics with their friends and family.

  Seed words: fast, healthy, compact
  ```

  > Are not happy with the output? If not, what would you change?
  > ---
  > This is where the art and science of prompt engineering comes in. You can tweak the following to get the results you want: 
  > 1. Tweak the prompt: There are five key elements to include in your prompt:
  >     - `Persona`: Define the tool’s role or function (e.g. its job title). 
  >     - `Objective`: State what you want it to achieve. 
  >     - `Audience`: Specify who will read or hear the message. 
  >     - `Parameters`: Set the tone, style, length, and any other rules for the tool. 
  >     - `Context`: Provide the main points, the background information, and the call to action.
  >     - `Examples`: Include examples of the kind of output you want. (a.k.a. One-shot or Few-shot learning)
  > 1. Tweak other parameters:
  >     - Use the `Temperature` parameter to control the randomness of the output. A lower temperature will give you more predictable results, while a higher temperature will give you more creative results.
  >     - Use the `Top P` parameter to control the diversity of the output.
  >     - Use the `Max Tokens` parameter to control the length of the output.
  >     - Use the `Stop` parameter to control the completion of the output.
  >     - Use the `seed` parameter to control the randomness of the output.
  > 1. Try a different model (GPT-4-Turbo, GPT-4, GPT-3.5-Turbo, etc.)
  > 
  > This article provides a good overview of [prompt engineering techniques](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions).



#### Summarisation:

Example 1:

- **System Prompt**:
  
  ```plaintext
  Generate a summary of the conversation in the following format:
  - Customer problem:
  - Outcome of the conversation:
  - Action items for follow-up:
  - Customer budget:
  - Departure city:
  - Destination city:
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  User: Hi there, I’m off between August 25 and September 11. I saved up 4000 for a nice trip. If I flew out from Melbourne, what are your suggestions for where I can go?
  Agent: For that budget you could travel to cities in the US, Mexico, Brazil, Italy, or Japan. Any preferences?
  User: Excellent, I’ve always wanted to see Japan. What kind of hotel can I expect?
  Agent: Great, let me check what I have. First, can I just confirm with you that this is a trip for one adult?
  User: Yes, it is.
  Agent: Great, thank you. In that case, I can offer you 15 days at HOTEL Sugoi, a 3-star hotel close to a Palace. You would be staying there between August 25th and September 7th. They offer free wifi and have an excellent guest rating of 8.49/10. The entire package costs 2024.25AUD. Should I book this for you?
  User: That sounds really good actually. Please book me at Sugoi.
  Agent: I can do that for you! Can I help you with anything else today?
  User: No, thanks! Please just send me the itinerary to my email soon.
  ```

Example 2:
- **System Prompt**:
  
  ```plaintext
  Given a conversation transcript between two or more participants, output a JSON object with the following keys and values:
  - "problem": a summary of the problem or issue discussed in the conversation.
  - "outcome": a summary of the outcome of the conversation.
  - "actionItems": a list of action items or next steps discussed in the conversation.
  - "budget": the budget or financial constraints discussed in the conversation.
  - "departureCity": the city of departure discussed in the conversation.
  - "destinationCity": the city of destination discussed in the conversation.
  ```

#### Code Generation and Transformation:

Example 1:

- **System Prompt**:
  
  ```plaintext
  - You are a SQL expert.
  - You will be given a SQL query and you need to explain the query in simple terms.
  ```
  
- **User's Sample Request**:
  
  ```sql
  SELECT c.customer_id
  FROM Customers c
  JOIN Streaming s
  ON c.customer_id = s.customer_id
  WHERE c.signup_date BETWEEN '2020-03-01' AND '2020-03-31'
  AND s.watch_date BETWEEN c.signup_date AND DATE_ADD(c.signup_date, INTERVAL 30 DAY)
  GROUP BY c.customer_id
  HAVING SUM(s.watch_minutes) > 50 * 60
  ```
  
- **Follow-up**:
  
  ```plaintext
  What might spark an individual's interest in this time period, and a company's in this SQL query?
  ```
  
- **Follow-up**:
  
  ```plaintext
  Modify the query to return the customer_id and the total watch minutes for each customer.
  ```

#### Question Answering:

Example 1:

- **System Prompt**:
  
  ```plaintext
  - You are a SQL expert.
  - You will be given a SQL query and you need to explain the query in simple terms.
  ```

#### Reasoning Over Data (Text, Images, Etc.):

Example 1:

- **System Prompt**:
  
  ```plaintext
  You are an AI assistant.
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  Below is an extract from the annual financial report of a company. 
  Extract key financial number (if present), key internal risk factors, and key external risk factors.

  # Start of Report

  Revenue increased $7.5 billion or 16%. Commercial products and cloud services revenue increased $4.0 billion or 13%. O365 Commercial revenue grew 22% driven by seat growth of 17% and higher revenue per user. Office Consumer products and cloud services revenue increased $474 million or 10% driven by Consumer subscription revenue,   on a strong prior year comparable that benefited from transactional strength in Japan. Gross margin increased $6.5 billion or 18% driven by the change in estimated useful lives of our server and network equipment. Our competitors range in size from diversified global companies with significant research and development resources to small, specialized firms whose narrower product lines may let them be more effective in deploying technical, marketing, and financial resources. Barriers to entry in many of our businesses are low and many of the areas in which we compete evolve rapidly with changing and disruptive technologies, shifting user needs, and frequent introductions of new products and services. Our ability to remain competitive depends on our success in making innovative products, devices, and services that appeal to businesses and consumers.

  # End of Report
  ```

Example 2: Using Vision Capabilities

- **System Prompt**:
  
  ```plaintext
  You are an AI assistant.
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  What is the quickest way to get from the patio to the bathroom?
  ```

### Experiments using Assistants:

#### Helpful Assistant:

Example 1:

- **Name**: Math Tutor
- **System Prompt**:
  
  ```plaintext
  You are a personal math tutor. Answer questions briefly, in a sentence or less.
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  What is the value of x in the equation 3x + 5 = 20?
  ```

### Content Filering

Azure OpenAI Service includes a content filtering system that works alongside core models. This system works by running both the prompt and completion through an ensemble of classification models aimed at detecting and preventing the output of harmful content. 

### Wrap up

You can play with this tech, no matter if you're a pro coder or someone who's just curious about what AI can do. So, just have a go!
