---
aliases:
  - Parts-of-speech tagging
---

- [[Markov Chain]]s
- [[Hidden Markov Models]]
- [[Viterbi algorithm]]

## Usage
You can use part of speech tagging for:
- Identifying named entities
- Speech recognition
- Coreference Resolution

You can use the probabilities of POS tags happening near one another to come up with the most reasonable output


# Parts-of-speech Tagging
## Creating matrices
#### Transition probabilities matrix

|**A**|...|RBS|RP|SYM|TO|UH|...|
|---|---|---|---|---|---|---|---|
|**RBS**|...|2.217069e-06|2.217069e-06|2.217069e-06|0.008870|2.217069e-06|...|
|**RP**|...|3.756509e-07|7.516775e-04|3.756509e-07|0.051089|3.756509e-07|...|
|**SYM**|...|1.722772e-05|1.722772e-05|1.722772e-05|0.000017|1.722772e-05|...|
|**TO**|...|4.477336e-05|4.472863e-08|4.472863e-08|0.000090|4.477336e-05|...|
|**UH**|...|1.030439e-05|1.030439e-05|1.030439e-05|0.061837|3.092348e-02|...|
|...|...|...|...|...|...|...|...|

$$ P(t_i | t_{i-1}) = \frac{C(t_{i-1}, t_{i}) + \alpha }{C(t_{i-1}) +\alpha * N_{\text{tags}})}\tag{3}$$

#### Emission probability matrix


|**B**|...|725|adroitly|engineers|promoted|synergy|...|
|---|---|---|---|---|---|---|---|
|**CD**|...|**8.201296e-05**|2.732854e-08|2.732854e-08|2.732854e-08|2.732854e-08|...|
|**NN**|...|7.521128e-09|7.521128e-09|7.521128e-09|7.521128e-09|**2.257091e-05**|...|
|**NNS**|...|1.670013e-08|1.670013e-08|**4.676203e-04**|1.670013e-08|1.670013e-08|...|
|**VB**|...|3.779036e-08|3.779036e-08|3.779036e-08|3.779036e-08|3.779036e-08|...|
|**RB**|...|3.226454e-08|**6.456135e-05**|3.226454e-08|3.226454e-08|3.226454e-08|...|
|**RP**|...|3.723317e-07|3.723317e-07|3.723317e-07|**3.723317e-07**|3.723317e-07|...|
|...|...|...|...|...|...|...|...|

$$P(w_i | t_i) = \frac{C(t_i, word_i)+ \alpha}{C(t_{i}) +\alpha * N_{\text{vocab}}}\tag{4}$$

## Viterbi algorithm and dynamic programming

- [[Viterbi algorithm]]


