[Paper link](https://arxiv.org/pdf/1909.01311.pdf)

This paper shows that only error sign information, and not the explicit errors, is sufficient to maintain feedback alignment and provide learning in the hidden layers. This solves the weight transport problem (symmetry requirement between forward and backward weights), removes update locking and leads to a purely feedforward algorithm that only needs a label-dependent random vector selection for estimating layerwise loss gradients.
