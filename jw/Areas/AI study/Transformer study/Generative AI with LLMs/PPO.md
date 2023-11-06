---
aliases:
  - Proximal Policy Optimization
tags:
  - AI/RL
---

## Proximal Policy Optimization
In PPO. the goal is to find an improved policy for an agent by iteratively updating its parameters based on rewards received from interacting with the environment.

Updating the policy too aggressively can lead to unstable learning or drastic policy changes. To address this, PPO introduces a constraint that limits the extend of policy updates. This constraint is enforced using [[KL-Divergence]].


## Read more
- https://huggingface.co/blog/trl-peft

- [**Proximal Policy Optimization Algorithms**](https://arxiv.org/pdf/1707.06347.pdf) - The paper from researchers at OpenAI that first proposed the PPO algorithm. The paper discusses the performance of the algorithm on a number of benchmark tasks including robotic locomotion and game play.
    
- [**Direct Preference Optimization: Your Language Model is Secretly a Reward Model**](https://arxiv.org/pdf/2305.18290.pdf) - This paper presents a simpler and effective method for precise control of large-scale unsupervised language models by aligning them with human preferences.