# Guide to Azure OpenAI Studio

## Introduction

Let's take a deeper look at the technology behind the scenes.

## What Problem Are We Solving?

The Azure OpenAI Studio is a great place to start your experimentation with the different capabilities that Generative AI models have to offer. Capabilities such as:

1. Writing aid
1. Summarisation
1. Chat and Conversation
1. Code Generation and Transformation
1. Question Answering
1. Reasoning over data (text, images, etc.)
1. Search

Now, let's explore each of these capabilities and run through some experiments to see how they work.

### Experiments using Chat Completions:

#### Writing Aid:

Example 1:

- **System Prompt**:
  
  ```plaintext
  - Generate 5 product names using provided seed words.
  - Ensure names highlight product features, appeal internationally, and evoke positivity.
  ```
  
- **User's Sample Request**:
  
  ```plaintext
  Generate product name ideas for a yet to be launched wearable health device that will allow users to monitor their health and wellness in real-time using AI and share their health metrics with their friends and family.
  ```

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
  User: Hi there, I’m off between August 25 and September 11. I saved up 4000 for a nice trip. If I flew out from San Francisco, what are your suggestions for where I can go?
  Agent: For that budget you could travel to cities in the US, Mexico, Brazil, Italy, or Japan. Any preferences?
  User: Excellent, I’ve always wanted to see Japan. What kind of hotel can I expect?
  Agent: Great, let me check what I have. First, can I just confirm with you that this is a trip for one adult?
  User: Yes, it is.
  Agent: Great, thank you. In that case, I can offer you 15 days at HOTEL Sugoi, a 3-star hotel close to a Palace. You would be staying there between August 25th and September 7th. They offer free wifi and have an excellent guest rating of 8.49/10. The entire package costs 2024.25USD. Should I book this for you?
  User: That sounds really good actually. Please book me at Sugoi.
  Agent: I can do that for you! Can I help you with anything else today?
  User: No, thanks! Please just send me the itinerary to my email soon.
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
