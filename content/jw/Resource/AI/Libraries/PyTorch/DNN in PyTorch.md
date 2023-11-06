---
tags:
  - CS/Programming/Python/PyTorch
---


```python
import torch
import torch.nn as nn

class DNN(nn.Module):
	def __init__(self, d_in, h1, h2, d_out):
		super(DNN, self).__init__()
		self.linear1 = nn.Linear(d_in, h1)
		self.linear2 = nn.Linear(h1, h2)
		self.linear3 = nn.Linear(h2, d_out)

	def forward(self, x):
		x = torch.sigmoid(self.linear1(x))
		x = torch.sigmoid(self.linear2(x))
		x = self.linear3(x)
		return x
```

__With [[torch.nn.Sequential]]__:
```python

model = torch.nn.Sequential(
	torch.nn.Linear(input_dim, hidden_dim1), torch.nn.Sigmoid(),
	torch.nn.Linear(hidden_dim1, hidden_dim2), torch.nn.Sigmoid(),
	torch.nn.Linear(hidden_dim2, output_dim),
)
```

#### Load Data

[[torchvision]].datasets
[[torchvision]].transforms

```python
import torchvision.datasets as dsets
import torchvision.transforms as transforms
from torch.utils.data import DataLoader

train_dataset = dsets.MNIST(root='./data', train=True, transform=transforms.ToTensor())
val_dataset = dsets.MNIST(root='./data', train=False, transform=transforms.ToTensor())

train_loader = torch.utils.DataLoader(dataset=train_dataset, batch_size=2000)
val_loader = torch.utils.DataLoader(dataset=val_dataset, batch_size=2000)

criterion = nn.CrossEntropyLoss()
```


```python
def train(model, criterion, train_loader, val_loader, optimizer, epochs=100):
	i = 0
	useful_stuff = {'training_loss': [], 'val_accuracy': []}
	for epoch in range(epochs):
		for i, (x, y) in enumerate(train_loader):
			optimizer.zero_grad()
			z = model(x.view(-1, 28 * 28))
			loss = criterion(y, z)
			loss.backward()
			optimizer.step()
			useful_stuff['training_loss'].append(loss.data.item())
		
		correct = 0
		for x, y in val_loader:
			z = model(x.view(-1, 28 * 28))
			_, label = torch.max(z, 1)
			correct += (label == y).sum().item()
		accuracy = 100 * (correct / len(val_dataset))
		useful_stuff['val_accuracy'].append(accuracy)
	return useful_stuff
```


```python
import torch.optim as optim

optimizer = optim.SGD(model.parameters(), lr=0.01)
train_stuff = train(model, criterion, train_loader, val_loader, optimizer, epochs=35)


```


#### Visualize
```python
import matplotlib.pylab as plt

plt.plot(train_stuff['training_loss'], label='training loss')
plt.ylabel('loss')
plt.title('training loss iterations')
plt.legend()
```

```python
plt.plot(train_stuff['val_accuracy'], label='valication accuracy')
plt.ylabel('validation_accuracy')
plt.xlabel('Iteration')
plt.legend()
```

