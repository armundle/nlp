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

# TODO
- Monitor saturation of hidden units
