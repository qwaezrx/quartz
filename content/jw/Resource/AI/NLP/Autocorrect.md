---
tags:
  - AI/NLP
---



## Building the model

1. Identify a misspelled word
2. Find strings __n__ edit distance away: (these could be random strings)
	1. Insert (add a letter)
	2. Delete (remove a letter)
	3. Switch (swap 2 adjacent letters)
	4. Replace (change 1 letter to another)
3. Filter candidates: (keep only the real words from the previous steps)
4. Calculate word probabilities: (choose the word that is most likely to occur in that context)


