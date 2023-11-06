---
aliases:
  - named entity recognition
  - Named Entity Recognition
---

## Named entity recognition
NER locates and extracts predefined entities from text.
It allows you to find places, organizations, names, times and dates.

![[Pasted image 20230906174205.png]]


__NER systems are used in:__
- search efficiency
- recommendation engines
- customer service
- automatic trading
- etc.


## NER training; Data processing
- Convert words and entity classes into arrays:
- Pad with tokens: Set sequence length to a certain number and use the [[<PAD>]] token to fill empty spaces
- Create a data generator

![[Pasted image 20230906194012.png]]


## Training an NER system:
1. Create a tensor for each input and its corresponding number
2. Put them in a batch ==> 64, 126, 256, ...
3. Feed it into an [[LSTM]] unit
4. Run the output through a dense layer
5. Predict using a log softmax over K classes

![[Pasted image 20230906194340.png]]


## NER; Computing accuracy
1. Pass test set through the model
2. Get arg max across the prediction array
3. Mask padded tokens
4. Compare with the true labels.

