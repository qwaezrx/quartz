

Siamese network learns what makes two inputs the same


#### Classification vs. Siamese Networks
- __Classification__: categorize things
- __Siamese Networks__: Identity similarity between things


## Siamese network architecture

![[Pasted image 20230906203423.png]]

You can use other NN rather than LSTM such as CNNs etc.

>[!important]
>These two sub-networks share __identical__ parameters

You only need to train one set of weights and not two.



## Siamese network applications
- Face recognition
- Handwritten checks
- Question duplicates
- Queries

![[Pasted image 20230906202219.png]]


## Siamese network examples

#### [[Siamese network; LSTM]]

#### [[Siamese network; CNN]]

## Siamese network; Cost function

Siamese network use the [[Triplet Loss]]

## Siamese network Training/Testing

![[Pasted image 20230906211212.png]]

![[Pasted image 20230906211251.png]]

Finally when **testing**:
1. Convert two inputs into an array of numbers
2. Feed it into your model
3. Compare 𝒗1,𝒗2 using cosine similarity
4. Test against a threshold τ