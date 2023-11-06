---
tags:
  - AI/Fine-Tuning/PEFT/Prompt-Engineering
---

### 1. Offer context

- Think about exactly what you want the [[AI]] to generate, and provide a prompt that’s tailored specified to that
    
- Examples
    
    > **Basic:** “Write about productivity”
    > 
    > ********************Improved:******************** “Write a blog post about the importance of productivity for small businesses”
    
    > **************Basic:************** “Write about how to horse train a dog”
    > 
    > **Improved:** “As a professional dog trainer, write an email to a client who has a new 3-month-old Corgi about the activities they should do to house train their puppy”
    

### 2. Include helpful information upfront

- Examples
    
    > Reid’s resume: [paste full resume here]
    
    Given the above information, write a witty speaker bio about Reid.
    
    > [Paste the full text of the article here]
    
    Summarize the context from the above article with 5 bullet points
    

### 3. Give examples

### 4. Tell it the length of the response you want

- Examples
    
    > **************Basic:************** “Summarize this article”
    
    **********Improved:********** “Write a 500-word summary of this article.”
    

### 5. Define the expected formats

- Can output various code languages like Python and HTML as well as visual styles like charts and CSVs
    
- Examples
    
    > Product Name, Quality
    
    Apple, 1
    
    Orange, 2
    
    Banana, 1
    
    Using the above CSV, output a chart of the frequency each product appears in the text above
    

### 6. Use some of handy expressions

- __"Lets think step by step"__ - [[Resource/AI/Generative AI/Transformer/Prompt engineering/CoT]]
- **“Thinking backwards”**
- **“In the style of [famous person]”**
- “**As a [insert a profession/role]”**