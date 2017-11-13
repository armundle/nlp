# [An overview of gradient descent optimization algorithms](http://ruder.io/optimizing-gradient-descent/)
## Challenges with mini-batch gradient descent (and SGD or batch gradient)
- A small learning rate leads to slow convergence; large learnign rate hinders convergence or may lead to divergence.
- With sparse data and features with varying frequencies, learning rate update mechanism might be different - e.g. larger update for rare features.
- Saddles points occuring in non-convex error functions (common for neural networks) are difficult for SGD to escape since the gradient is ≈ 0.
- Ravines - areas where surface curves much more steeply in one dimension than another, common around local optima - are difficult for SGD to navigate.

## Gradient Descent Optimization Algorithms
### Momentum
- **Main idea** - Just like a ball rolling downhill gets faster and faster, the parameter updates increase if the gradients point in the same direction but reduce for those whose gradients change directions. Result is faster convergence and reduce oscillations. Can think of a damping the oscillations.
- Adds a fraction of the update vector `γ := momentum` from pervious time step to the current update vector in SGD to help solve the ravine problem.
- Typical values for `γ ≈ 0.9`

### Nesterov Accelerated Gradient (NAG)
- **Main idea ** - Instead of just rolling downhill with `Momentum`, NAG slows down before the hill slopes up again.
- The "anticipatory" nature of the updates results in increased reponsiveness. This has helped improve the performance of RNNs.

### Adagrad
- **Main idea** - In addition to NAG, adapting to each parameters to peform larger (infrequence parameters) of smaller updates depending on their importance.
- Suited for sparse data (e.g. training GloVe embedings which contain infrequent words); improves the robustness of SGD.
- In the SGD update step, Adagrad modifies learning rate for every parameter based past gradients computed for that particular parameter.
- No need to manually tune the learning rate; use a default value of `0.01`

### Adadelta
- Improves upon Adagrad's shortcoming of aggressive and monotonically decreasing learning rate.
- Eliminates the need for a default learning rate.

### RMSprop
- Another solution for Adagrad's radically diminishing learning rate problem (developed by Hinton)

### Adam (Adaptive Momentum Estimation)
- Calculates adaptive learning rates for each parameter - alternative to Adagrad.
- Default values: `β1 ≈ 0.9`, `β2 ≈ 0.999`, `ϵ ≈ 10−8`
- Can be seen as a combination of RMSprop and Momentum.

### Adamax
- More stable than Adam (?)

### Nadam
- Combination of Adam and NAG

## Which optimizer to use?
- In input data is sparse, best results using adaptive learning rate methods.
- No need to tune the learning rate for the adaptive methods, start with the default value.
- Adam seems to be the best choice.
