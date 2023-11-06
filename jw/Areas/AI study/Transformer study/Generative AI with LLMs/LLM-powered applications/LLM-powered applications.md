---
tags:
  - AI/GAI/LLM
---


![[Screenshot 2023-09-05 at 8.33.32 PM.png]]


## Requirements for using LLMs 
#### Plan actions
Steps to process return:
- Step 1: Check order ID
- Step 2: Request label
- Step 3: Verify user email
- Step 4: Email user label

#### Format outputs
SQL Query:
```SQL
SELECT COUNT(*)
FROM orders
WHERE order_id = 21104
```

#### Validate actions
Collect required user information and make sure it is in the completion
User emal:
hongjw0309@email..



[[Langchain]]

[[RAG]]

## See more
#### **LLM powered application architectures**

- [**LangChain Library (GitHub)**](https://github.com/hwchase17/langchain) - This library is aimed at assisting in the development of those types of applications, such as Question Answering, Chatbots and other Agents. You can read the documentation [here](https://docs.langchain.com/docs/).
    
- [**Who Owns the Generative AI Platform?**](https://a16z.com/2023/01/19/who-owns-the-generative-ai-platform/) - The article examines the market dynamics and business models of generative AI.