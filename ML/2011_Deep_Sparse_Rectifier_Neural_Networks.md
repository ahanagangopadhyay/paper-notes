You can find the paper [here](http://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf).


![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Significance**

This 2011 paper by Yoshua Bengio's group at the University of Montreal outlined the benefits of using Rectified Linear Units (ReLUs) for deep but fully supervised networks. Neural networks trained with logistic sigmoid or hyperbolic tangent neurons were hard to train in a fully supervised fashion when the number of layers were too large, requiring semi-supervised or unsupervised pre-training to bootstrap performance. Although rectifier neural networks can take advantage of semi-supervised or unsupervised setups, the authors show that these networks achieve their best performance in purely supervised setups with large quantities of labeled data. The performance is also as good as or even better than networks trained with sigmoid or tanh neurons. This result decreases the performance gap between deep networks trained with and without unsupervised pre-training. 

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Summary**

The authors argue that rectifier units are closer to a biological neuron's response in their main operating regime when compared to sigmoid or tanh neurons, bridging - in a sense - the gap between machine learning and neuroscience. In biological networks, only around 1-4% of the total number of neurons are active at any time, leading to a naturally sparse representation. Without imposing additional L1 regularization, feedforward networks do not have this property. In fact sigmoid neurons have a steady-state around 0.5, so that on an average, neurons fire at half their saturation, making it biologically implausible. Tanh neurons have a steady state at 0, making them better in terms of optimization, but they have an antisymmetry around 0 which is also biologically implausible.

Activation functions that plot expected firing rate as a function of total input in models of biological neurons, on the other hand, are typically one-sided, having zero response below a threshold, and a slowly saturating one above threshold.
