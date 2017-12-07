# [Understanding the difficult of training deep feedforward neural networks](http://proceedings.mlr.press/v9/glorot10a.html)

### Category

### Context
### Correctness
### Contributions
### Clarity
## Deep Neural Networks
- Goal is to learn feature hierarchies with features from higher levels of the hierarchy formed by the composition of lower level features.
- In order to learn complicated functions (i.e function approximation) that can represent high-level abstractions, deep architectures are useful.
- Unsupervised training may act as a regularizer that initializes the parameters in a "better" basin for the optimization

### Traditional challenge
#### Drawback of random initialization
- Standard gradient descent performs poorly
- Activaction functions such as logistic sigmoid actication has mean value of zero, which can drive the top hidden layer into saturation

## Saturation of activation functions
- Excessive saturation of activations function prevents the gradients from propogating well
### Sigmoid
- Hidden unit output of 0 corresponds to a saturated sigmoid.
- It slows down learning due to non-zero mean.
 - prevents the gradients to flow backwards
 - prevents the lower layers from learning useful features.
- Deep networks initialized from unuspervised pre-training do not suffer from the saturation behavior.

### tanh
- Don't suffer from this problem since symmetry around 0
- With standard random initialization, however, saturation starts from the lower layers quickly

## Gradients and their propogation
- For classification, logitstic regression or conditional log-likelihood cost function worked better than quadratic cost function

### softsign
- Different from tanh in that the asymptotes are smoother
- 

# TODO
- Monitor saturation of hidden units
