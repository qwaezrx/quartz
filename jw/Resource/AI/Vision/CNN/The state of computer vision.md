---
tags:
  - AI/CV
---

---
Little data (more hand-engineering)
- Transfer learning
- Object detection
- Image recognition
- Speech recognition
Lots of data (simpler algorithms, less hand-engineering)
---

Tow sources of knowledge
- Labeled data (x, y)
- Hand engineered features/network architecture/other components

## Tips for doing well on benchmarks/winning competitions
- [[Ensembling]] := Train several (random) networks independently and average their outputs (not weights)
	- Used for benchmarks
	- $\diamond$ used in real production

- Multi-crop at test time
	- Run classifier on multiple versions of test images and average results
	- Used for benchmarks
	- $\diamond$ used in real production

## Use open source code
- Use architectures of networks published in the literature

Because a lot of the computer vision problems are in the small data regime, others have done a lot of hand-engineering of the network architectures. And a NN that works well on one vision problem often may work well on other problems.

