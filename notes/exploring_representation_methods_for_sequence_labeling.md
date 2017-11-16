# [Exploring Representation Methods For Sequence Labeling](https://openreview.net/pdf?id=BJoBfQ-0b)
*(Under review at ICLR 2018)*

---
#### Category
- Description of research prototype

#### Context
- Related works
  - [End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF; Ma and Hovey 2016](https://arxiv.org/pdf/1603.01354)
  - [Neural Architectures for Named Entity Recognition; Lample et. al. 2016](https://arxiv.org/pdf/1603.01360)
- Theoretical bases
  - ???

#### Correctness
- ???

#### Contributions
- Establish a controlled experiment setup to compare performances for "popular" neural network architectures using character-level representations.
- Evaluate SOTA using controlled experiments.
- Improve SOTA for sequence labeling task, specifically using the above.
- Novel dropout "word wise" strategy - better handle out-of-training-vocabulary (OOTV)
- Make implementation code public.

#### Clarity
- ???
---

# Summary
## Main Problem
- How effective are character level representations in representation learning?
- How to leverage pre-trained embeddings?
- No standard method for controlled experiments.

# Notes
- Applications of sequence labeling - POS tagging, NER, Entity Detection, Event Detection, etc.
- Traditional methods use domain-specific engineering; representation learning break such limitation and make neural networks state of the art.
- Without controlled experiments, even Ma & Hovey 2016, Lample et al. 2016 and Reimers & Gurevych end up with conflicting observations.
- Embedding techniques demonstrably capture semantics for extensive word dictionary.
  - character level representations (utilized using CNNs and highway networks) make better predictions for OOTV and misspellings.
- CRF layer helps with label dependency.

## Architecture
- character level representations extract lexical features; keeping the character level input case sensitive
- word level representations lower cased (that's how GloVe is too)
- rare words with freq < 5 := `<UNK>`
- CRF layer uses Viterbi alrogrithm
- Dropout at every layer
- SGD with momentum
- treat characters of whole sentences as a sequence instead of a single word
- highway layers
- `?` udpate word embeddings with fine-tune
- `?` apply dropout to the "fine-tuned" part of word embedding

## Datasets
 - WSJ-PTB, Accuracy measure.
 - CoNLL03 NER (BIOES schema), F1 measure.
 
## Observations
- character level representations with LSTM (size 300) is significantly better and has less spread than CNN
- pair wise CRF layer has lesser spread
- world level structures are more vulnerable than character level LSTMS; more prove to overfit

 # TODO
 ## Follow up readings
 - [Reporting Score Distributions Makes a Difference: Performance Study of LSTM-networks for Sequence Tagging; Reimers and Guervych 2017](https://arxiv.org/pdf/1707.09861)
 - [Empower Sequence Labeling with Task-Aware Neural Language Model; Liu et al. 2017](https://arxiv.org/abs/1709.04109)
 
 ## Future Ideas

 # UNK
 
