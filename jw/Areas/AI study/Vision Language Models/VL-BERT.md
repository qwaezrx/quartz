---
tags:
  - AI
---

Shares similar architecture with [[VisualBERT]], but uses Faster [[R-CNN]] as regions of interest(ROI) extractor, and leverages this extracted ROI information as the image region embedding.

VL-BERT also includes an additional pre-training mask, masked ROI classification with linguistic clues, for better incorporating the visual information. 