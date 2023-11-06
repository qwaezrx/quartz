---
tags:
  - CS/Programming/Python/PyTorch/Torchvision
---

```python
from torchvision import transforms

image_size = 64

# Define data augmentation
preprocess = transforms.Compose([
	transforms.Resize((image_size, image_size)),
	transforms.RandomHorizontalFlip(), # Data augmentation
	transforms.ToTensor(), # Convert to tensor (0, 1)
	transforms.Normalize([0.5], [0.5]) # Map to (-1, 1)
])
```


```python
batch_size=32

def transform(examples):
	images = [prerpocess(image.convert("RGB")) for image in examples]
	return {"images": images}


dataset.set_transform(transform)


train_dataloader = torch.utils.data.DataLoader(
	dataset, batch_size=batch_size, shuffle=True
)
```

