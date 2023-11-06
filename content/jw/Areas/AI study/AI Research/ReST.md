---
tags:
  - Paper_review
---


Paper: [https://arxiv.org/abs/2308.08998](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqazZBZ3lIeHc2cnBEcE9zUTVncEd0MmljTFJad3xBQ3Jtc0trOTN2RnRCRmRteE5GMEhxOXhYdWh5U1BrRmw5Z3F2cWdzaTdJN0xBbTdtazFtWkFTdlkyTmNQcGJTUFJvQlFFZzlTaUM3RGdaVXhOeWZNZmQ0YzZ3WG9QUmxDd3RFQXp2Y0gyVjYybzZGdHN4T0VtOA&q=https%3A%2F%2Farxiv.org%2Fabs%2F2308.08998&v=V4dO2pyYGgs)


## Reinforced Self-Training for Language Models

[[RLHF]] can improve the quality of LLMs outputs by aligning them with human preferences. We propose a simple algorithm for aligning LLMs with human preferences inspired by growing batch RL.

Given an initial LLM policy, _ReST_ produces a dataset by generating samples from the policy, which are then used to improve the LLM policy using offline RL algorithms.

Our results show that _ReST_ can substantially improve translation quality, as measured by automated metrics and human evaluation on machine translation benchmarks in a compute and sample-efficient manner.


![[Screenshot 2023-09-18 at 9.47.53 AM.png]]


Need a good Reward model

![[Screenshot 2023-09-18 at 10.23.54 AM.png]]