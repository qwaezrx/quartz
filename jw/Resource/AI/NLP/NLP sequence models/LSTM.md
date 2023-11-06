---
tags:
  - AI/LSTM
---


## LSTM architecture

![[Pasted image 20230906173947.png]]

![[IMG_541468457D88-1.jpeg]]

![[LSTM_cell_forward.png]]


$$
\begin{align}
& \tilde{c}^{<t>} = \tanh(W_{c}[a^{<t-1>}, X^{<t>}] + b_{c}) \\ \\

& \Gamma_{u} = \sigma(W_{u}[a^{<t-1>}, X^{<t>}] + b_{u}) \to \text{Update} \\
& \Gamma_{f} = \sigma(W_{f}[a^{<t-1>}, X^{<t>}] + b_{f}) \to \text{Forget} \\
& \Gamma_{o} = \sigma(W_{o}[a^{<t-1>}, X^{<t>}] + b_{o}) \to \text{Output} \\ \\
& c^{<t>} = \Gamma_{u} * \tilde{c}^{<t>} + \Gamma_{f} * c^{<t-1>} \\
& a^{<t>} = \Gamma_{o} * \tanh(c^{<t>})
\end{align}
$$

## Gates and states in LSTM
##### 🎈 Forget gate $\Gamma_{f}$
- := Tensor containing values(0 ~ 1) 
- $\approx 0 \implies$ LSTM will forget $c^{<t-1>}$

__Equation__
$$
\Gamma^{<t>}_{f} = \sigma(\mathbf{W}_{f}[\mathbf{a}^{<t-1>}, \mathbf{x}^{<t>}] + \mathbf{b}_{f})
$$
![[Screenshot 2023-08-29 at 9.21.46 PM.png]]
##### 🎈 Candidate value $\tilde{\mathbf{c}}^{<t>}$
- := Tensor ($\ni$ info from $t$ ( $\dots>$ stored in $c^{<t>}$ ))  
- := Parts of the candidate value (get passed on depend on $\Gamma_{u}$)
- := Tensor ($\ni$ (0...1))

__Equation__
$$
\tilde{\mathbf{c}}^{<t>} = \tanh(\mathbf{W}_{c}[\mathbf{a}^{<t-1>}, \mathbf{x}^{<t>}] + \mathbf{b}_{c})
$$
- The _tanh_ produces values (-1 ... 1)

##### 🎈 Update gate $\Gamma_{i}$
- : Used to decide what aspects of $\tilde{\mathbf{c}}^{<t>}$ to add to $\mathbf{c}^{<t>}$.

__Equation__
$$
\Gamma^{<t>}_{i} = \sigma(\mathbf{W_{i}}[\mathbf{a}^{<t-1>}, \mathbf{x}^{<t>}] + \mathbf{b}_{i})
$$

##### 🎈 Cell state $\mathbf{c}^{<t>}$
- := "Memory" (gets passed onto future time steps)

__Equation__
$$
\mathbf{c}^{<t>} = \Gamma^{<t>}_{f} * \mathbf{c}^{<t-1>} + \Gamma_{i}^{<t>} * \tilde{\mathbf{c}}^{<t>}
$$
- $\mathbf{c}$.shape = $(n_{a}, m, T_{x})$
- $\mathbf{c}^{<t>}$.shape = $(n_{a}, m)$

##### 🎈 Output gate $\Gamma_{o}$
- : Decides what gets sent to the prediction (output) of the time step
- := Tensor ($\ni$ (0...1))

__Equation__
$$
\Gamma^{<t>}_{o} = \sigma(\mathbf{W_{o}}[\mathbf{a}^{<t-1>}, \mathbf{x}^{<t>}] + \mathbf{b}_{o})
$$

##### 🎈 Hidden state $\mathbf{a}^{<t>}$
- := Hidden state (gets passed to LSTM cell's next time step)
- : Used to determine 3 gates of next time step
- : Used for prediction ($y^{<t>}$)

__Equation__
$$
\mathbf{a}^{<t>} = \Gamma^{<t>}_{o} * \tanh(\mathbf{c}^{<t>})
$$

##### 🎈Prediction $y^{<t>}_{\text{pred}}$
$$
y^{<t>}_{\text{pred}} = \text{softmax}(\mathbf{W}_{y}\mathbf{a}^{<t>} + \mathbf{b}_{y})
$$
- shape = $(n_{y}, m)$



## Important features of LSTM
- LSTM $\sim$ [[RNN]] $\because$ (both use hidden states($a^{<t>}$) to pass along information), but LSTM also uses a cell state($c^{<t>}$), which is like a long-term memory, to help deal with the issue of [[RNN#Vanishing gradients with RNNs]]. 

- LSTM cell consists of a cell state(long-term memory), a hidden state(short-term memory), along with 3 gates that constantly update the relevancy of its inputs:
	- __forget gate__:= Gate that decides which input units should be remembered and passed along. It's tensor with values between 0 and 1.
		- if $\Gamma_{f} \approx 1 \implies$ LSTM will mostly remember the corresponding value
		- if $\Gamma_{f} \approx 0 \implies$LSTM will "forget" the stored state in the previous cell state
	- __update gate__:= decides on what information to throw away, and what new information to add.
		- if $\Gamma_{u} \approx 0 \implies ($$\tilde{c}^{<t>}$  :passed=> hidden state)
		- if $\Gamma_{u} \approx 1 \implies$($\tilde{c}^{<t>}$ :prevented from being passed=> hidden state).
	- __output gate__:= decides what gets sent as the output of the time step


## LSTM applications:
- Next-character prediction
- Chatbots
- Music composition
- Image captioning
- Speech recognition


## See more
- https://colah.github.io/posts/2015-08-Understanding-LSTMs/

