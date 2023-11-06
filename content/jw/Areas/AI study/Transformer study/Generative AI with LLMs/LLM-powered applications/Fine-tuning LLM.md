---
tags:
  - AI/Fine-Tuning
---

## What is finetuing doing for you?
- Behavior change
	- Learning to respond more consistently
	- Learning to focus, e.g. moderation
	- Teasing out capability, e.g. better at conversation
- Gain knowledge
	- increasing knowledge of new specific concepts
	- Correcting old incorrect information
- Both

## Tasks to finetune
- Just text-in, text-out:
	- Extraction: text in, less text out
		- "Reading"
		- Keywords, topics, routing, agents (planning, reasoning, self-critique, tool use), etc.
	- Expansion: text in, more text out
		- "Writing"
		- Chat, write emails, write code
- Task clarity is key indicator of success
- Clarity means knowing what's bad vs. good vs. better


## Steps to finetune LLMs ( beginner)
1. Identify task(s) by prompt-engineering a large LLM
2. Find tasks that you see an LLM doing ~OK at
3. Pick one task
4. Get ~1000 inputs and outputs for the task
	1. Better than the ~OK from the LLM
5. Finetune a small LLM on this data


