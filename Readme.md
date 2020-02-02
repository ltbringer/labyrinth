# labyrinth

This is a personal project to build Automatic Speech Recognition models. The objective is to avoid the massive amount of utility that projects like [kaldi](https://github.com/kaldi-asr/kaldi) lend to a developer and build those as and when needed. To understand mainly:

- Why are certain tools used?
- What is the theoretical background behind the recipes?

... and be able to replicate a training pipeline using pytorch, avoiding [`torchaudio.compliance.kaldi`](https://pytorch.org/audio/compliance.kaldi.html).


## Milestones

- [x] Data preparation. 
  - [x] Prepare a batch containing audio frames of 250ms windowed by 50ms. Kaldi takes audio frames of 25ms shifted by 10ms each time. This, I anticipate, would impact RTF factor (for `x` seconds of audio the model needs `n` seconds for transcription.)
  - [x] Understanding features. Kaldi trains their models on MFCC, CMVN etc features, I'll start with raw spectrogram.
  - [x] Build a streaming data loader, Pytorch has a neat [`IterableDataset`](https://pytorch.org/docs/stable/data.html#torch.utils.data.IterableDataset) utility that should help training models with sufficient data without pressuring a machine's memory.
- [ ] Modelling
  - [ ] Raw CNN-GRU architecture.
  - [ ] Using a pretrained model like resnet, [chop off final layers](https://forums.fast.ai/t/pytorch-best-way-to-get-at-intermediate-layers-in-vgg-and-resnet/5707/2) and feed it to a:
    - [ ] GRU
    - [ ] LSTM
- [ ] Metrics
  - [ ] Use a popular open source data-set for publishing results.

## docs/
A themed notebook is saved in `./docs` for faster access. Prepared by:
```
jupyter nbconvert --to html am_training.ipynb --output index.html 
```

## Choice of name?

> Fish, the first vertebrates, arose between 450 and 600 million years ago, a mere one tenth of the age of our planet. Primitive fish had an internal balance organ inherited from some obscure invertebrate ancestor. Eventu-ally, the balance labyrinth came to include an auditory receptor. --[Development of Hearing. Part I: Phylogeny ](https://www.audiology.org/sites/default/files/journal/JAAA_05_05_02.pdf)

