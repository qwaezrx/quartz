---
tags:
  - AI/ML
---


In supervised [[Machine learning]], you usually have input $X$, which goes into your prediction function to get your $\hat{Y}$. You can then compare your prediction with the true value $Y$. This gives you your cost which you use to update the parameters $\theta$.


| Input(x)      | Output(y)            | Application             | Useful [[Neural Network]] |     
| ------------- | -------------------- | ----------------------- | ------------------------- | 
| Home features | Price                | Real Estate             | Standard NN               |     |
| Ad, user info | Click on ad? (0/1)   | Online Advertising      | Standard NN               |     |
| Image         | Object(1, ..., 1000) | Photo tagging           | [[CNN]]                   |     
| Audio         | Text transcript      | [[Speech recognition]]  | [[RNN]]                   |     
| English       | Chinese              | [[Machine translation]] | [[RNN]]                   |     


# Structured data vs. Unstructured data
## Structured data
Basically databases of data (with columns and rows)
## Unstructured data
Things like audio, image, text ... etc.