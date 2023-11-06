

>Train a smaller student model from a larger teacher model

![[Screenshot 2023-09-05 at 7.32.06 PM.png]]

LLM Teacher - LLM Student
- Train smaller model with bigger(teacher) model
- Then use the smaller model for inference to lower your storage and compute budget.
- The knowledge distillation between teacher and student model is achieved by minimizing a loss function called the distillation loss.

![[Screenshot 2023-09-05 at 7.38.53 PM.png]]

__Temperature__
$$
\begin{align}
\text{Tenperature} > 1 \implies \text{probability distribution becomes broader}
\end{align}
$$

>[!note]
>_Distillation_ is not as effective for generative decoder models.
>It's typically more effective more effective for encoder only models.

- Works better on encoder only model that have a lot of representation redundancy.
