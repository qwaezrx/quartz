
Naive bayes is an example of [[Supervised ML]] and shares many similarities with the [[Logistic regression]] method.

It is called naive because this method takes the assumption that the features you're using for classification are all independent. Which in reality is rarely the case.

## Naive base inference condition rule for binary classification
For pos, neg classification in a sentence,
$$
\prod_{i=1}^{m} \frac{P(w_{i}|pos)}{P(w_{i}|neg)}
$$

## Laplacian smoothing
We usually compute the probability of a word given a class as follows:
$$
P(w_{i}|\text{class}) = \frac{\text{freq}(w_{i}, \text{class})}{N_{\text{class}}} \;\;\;\; \text{class} \in \{ \text{Positive} ,\text{Negative} \}
$$
However, if a word does not appear in the training, then it automatically gets a probability of 0, to fix this we add smoothing as follows
$$
\begin{gather}
P(w_{i}|\text{class}) = \frac{\text{freq}(w_{i}, \text{class}) + 1}{N_{\text{class}} + V} \\ \\
N_{\text{class}} = \text{frequency of all words in class} \\
V = \text{number of unique words for entire vocabulary}
\end{gather}
$$

## Considerations for implementing Naive Bayes
- Products($\prod$) bring risk of underflow -> Log prior + [[Log likelihood]]

	- $\log\left( \frac{P(pos)}{P(neg)} \prod^{n}_{i=1} \frac{P(w_{i}|pos)}{P(w_{i}|neg)} \right) \implies \log \frac{P(pos)}{P(neg)} + \sum^{n}_{i=1} \log \frac{P(w_{i}|pos)}{P(w_{i}|neg)}$

## Calculating Lambda
$$
\lambda(w) = \log \frac{P(w|pos)}{P(w|neg)}
$$

## Word sentiment
$$
\begin{align}
& ratio(w) = \frac{P(w|pos)}{P(w|neg)} \\ \\
& \lambda(w) = \log \frac{P(w|pos)}{P(w|neg)}
\end{align}
$$

Example:

| word  | Pos  | Neg  | $\lambda$ |
| ----- | ---- | ---- | --------- |
| I     | 0.2  | 0.2  | 0        |
| am    | 0.2  | 0.2  | 0         |
| happy | 0.09 | 0.01 | 2.2       |
| sad   | 0.02 | 0.03 | -0.4      |

log likelihood = 0 + 0 + 2.2 + (-0.4) > 0 -> positive

## Training Naive bayes classifier
### Step 0:
Collect and annotate corpus
### Step 1:
Preprocess using [[Preprocessing in NLP logistic regression]]
### Step 2:
Word count
=> freq(w, class)

| word  | Pos | Neg |
| ----- | --- | --- |
| i     | 2   | 2   |
| happy | 4   | 1   |
| sad   | 2   | 5   |
| am    | 2   | 2   |

### Step 3:
$P(w| class)$
$V = 6$
$N_{pos} = 10$
$N_{neg} = 10$
$$
\frac{{\text{freq}(\text{w}, \text{class}) + 1}}{N_{\text{class}} + V}
$$

| word  | Pos  | Neg | ratio |
| ----- | ---- | --- | ----- |
| I     | 0.2  | 0.2 | 1     |
| am    | 0.2  | 0.2 | 1     |
| happy | 0.15 | 0.1 | 1.5   |
### Step 4:
Get lambda $\lambda(w)$

| word  | Pos  | Neg  | $\lambda$ |
| ----- | ---- | ---- | --------- |
| I     | 0.13  | 0.13 | 0        |
| am    | 0.13  | 0.13  | 0         |
| happy | 0.344 | 0.1 | 2.2       |
| sad   | 0.02 | 0.03 | -0.4      |

### Step 5:
Get the log prior
$$
\text{logprior} = \log \frac{N_{pos}}{N_{neg}}
$$
if dataset is balanced (N_pos == N_neg), log prior will be 0.

### Step 6:
Predict
$\text{score} = \text{logprior} + \sum^{m}_{i=1}\lambda_{i}$
$\text{pred} = \text{score} > 0$

### Step 7:
Testing naive bayes
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DBzYqctbQdSc2KnLW5HURA_3de7717134ec4f3ea36f9318083b60c6_Screen-Shot-2020-09-08-at-4.42.03-PM.png?expiry=1692835200000&hmac=EJ--tDkrsUmaoaVrmi-w7F02A1n6FAaprXbDeLKwU7g)

## Applications of Naive Bayes
There are many applications of naive Bayes including:
- Author identification
- Spam filtering
- Information retrieval
- Word disambiguation
- ...
This method is usually used as a simple baseline. It is also really fast

## Assumptions in Naive Bayes
Naive bayes is a very simple model because it doesn't require any custom parameters.
### Independence
for example in "It is sunny and hot in the Sahara desert."
Naive bayes assumes that all text is independent to each other even though it is not.
### Relative frequencies in corpus
