---
tags:
  - AI/Training
---

## Introduction

>Technique used in [[Resource/AI/Sequential/Seq2seq]] models, such as [[NMT]] or text generation models.
>The basic idea of teacher forcing is to use the correct output from the previous time step as input to the current time step during training, instead of using the output predicted by the model

## Pros & cons
Teacher forcing can lead to better performance during training, but it can also result in the model being too dependent on the correct output from the previous time step, and therefore less robust to errors or noise in the input.

