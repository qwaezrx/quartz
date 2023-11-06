---
tags:
  - Open_Source
  - AI/GAI/Audio
author: OpenAI
date: 2020-04-30
---

## Motivation and Prior Work
---
A prominent approach is to generate music symbolically in the form of a piano roll, which specifies the timing, pitch, velocity, and instrument of each note to be played. This has led to impressive results like producing Bach chorals, polyphonic music with multiple instruments, as well as minute long and musical pieces.

But __symbolic generators have limitations__ - they cannot capture human voices or many of the more subtle timbres, dynamics, and expressivity that are essential to music. 

A different approach is to model music directly as raw audio. Generating music at the audio level is challenging since the sequences are very long. 
>[!note]
>A typical 4-minute song at CD quality (44kHz, 16-bit) has over 10 million timesteps. 

Thus, to learn the high level semantics of music, a model would have to deal with extremely long-range dependencies.

One way to addressing the long input problem is to use an [[AutoEncoder]] that compresses raw audio to a lower-dimensional space by discarding some of the perceptually irrelevant bits of information. We can then train a model to generate audio in this compressed space, and upsample back to the raw audio space.

We chose to work on music because we want to continue to push the boundaries of generative models. Our previous work on [[MuseNet]] explored synthesizing music based on large amounts of [[MIDI]] data. Now in raw audio, our models must learn to tackle high diversity as well as very long range structure, and the raw audio domain is particularly unforgiving of errors in short, medium, or long term timing.


## Approach
### Compressing Music to Discrete Codes
_Jukebox_'s autoencoder model compresses audio to a discrete space, using a quantization-based approach called [[VQ-VAE]]. 

Hierarchical VQ-VAEs can generate short instrumental pieces from a few sets of instruments, however they suffer from _hierarchy collapse_ due to use of successive encoders coupled with autoregressive decoders. A simplified variant called [[VQ-VAE-2]] avoids these issues by using feedforward encoders and decoders only, and they show impressive results at generating high-fidelity images.

We draw inspiration from VQ-VAE-2 and apply their approach to music. We modify their architecture as follows:
- To alleviate codebook collapse common to VQ-VAE models, we use random restarts where we randomly rest a codebook vector to one of the encoded hidden states whenever its usage falls below a threshold.
- To maximize the use of the upper levels, we use separate decoders and independently reconstruct the input from the codes of each level.
- To allow the model to reconstruct higher frequencies easily, we add a spectral loss that penalizes the norm of the difference of input and reconstructed spectrograms.

We use three levels in our VQ-VAE, shown below, which compress the 44kHz raw audio by 8x, 32x, and 128x, respectively, with a codebook size of 2048 for each level. This downsampling loss much of the audio detail, and sounds noticeably noisy as we go further down the levels. However, it retains essential information about the bitch, timbre, and volume of the audio.

__Compress__:
![](https://cdn.openai.com/jukebox/assets/vqvae-1.svg)

__Generate__:
![](https://cdn.openai.com/jukebox/assets/vqvae-2.svg)

### Generating Codes using Transformers
Next, we train the prior model whose goal is to learn the distribution of music codes encoded by [[VQ-VAE]] and to generate music in this compressed discrete space. Like the VQ-VAE, we have three levels of priors: 
1. a top-level prior that generates the most compressed codes
2. two upsampling priors that generate less compressed codes conditioned on above.

The top-level prior models the long-range structure of music, and samples decoded from this level have lower audio quality but __capture high-level semantics like singing and melodies__. The middle and bottom upsampling priors add local musical structures like timbre, significantly improving the audio quality.

We train these as [[Autoregressive model]]s using a simplified variant of [[Sparse Transformer]]s. Each of these models has 72 layers of factorized self-attention on a context of 8192 codes, which corresponds to approximately 24 seconds, 6 seconds, and 1.5 seconds of raw audio at the top


## Resources
- https://openai.com/research/jukebox
- [Paper](https://arxiv.org/abs/2005.00341)
