---
tags:
  - AI
---

# Introduction
Whether you're tuning [[Hyperparameters]], or trying out different ideas for learning algorithms, etc. You will find the learning process will be much faster if you have a [[Single number evaluation metric]] that lets you quickly tell if the new thing you just tried is working better or worse than your last idea.

So when starting on a machine learning project, it will be a good choice to set up a single real number evaluation metric for your problem.

# Evaluation
## Evaluation metrics

[[Precision]]: What percentage of predicted "cat"s are actually "cat"s?

[[Recall]]: What percentage of "cat"s are recognized as "cat"s?

[[F1 Score]]: Harmonic mean of $P$ (Precision), $R$ (Recall)
$$\frac{2}{\frac{1}{P} + \frac{1}{R}}$$
These evaluation metrics should be evaluated or calculated on a training set or a dev set or maybe on the test set.


## Satisficing optimizing metrics
For example, you care about the "accuracy" and "running time"
$\text{cost = accuracy} - 0.5 \times \text{runningTime}$
maximize accuracy -> Optimizing
subject to $\text{runningTime} \leq 100\text{ms}$ -> Satisficing

N metrics:
- 1 optimizing
- N-1 satisficing


# Train/dev/test sets
## Train/dev/test distributions
The dev set and the test set should come from the same distribution

## Size of dev and test sets

### Old way (small dataset):
- Train 70, Test 30
- Train 60, Dev 20, Test 20
### Modern (much larger dataset):
- Train 98, Dev 1, Test 1

### Size of test set
Set your test set to be big enough to give high confidence in the overall performance of your system


# When starting a new project
1. Set up dev/test set and metric
2. Build initial system quickly
3. Use [[Bias/Variance analysis]] & [[Error analysis]] to prioritize next steps.
4. Iterate


# Learning from multiple tasks
## [[Resource/AI/Training/Transfer learning]]
## [[Multi-task learning]]


