You can find the paper [here](http://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf).


![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Significance**

This 2011 paper by Yoshua Bengio's group at the University of Montreal outlined the benefits of using Rectified Linear Units (ReLUs) for deep but fully supervised networks. Neural networks trained with logistic sigmoid or hyperbolic tangent neurons were hard to train in a fully supervised fashion when the number of layers were too large, requiring semi-supervised or unsupervised pre-training to bootstrap performance. Although rectifier neural networks can take advantage of semi-supervised or unsupervised setups, the authors show that these networks achieve their best performance in purely supervised setups with large quantities of labeled data. The performance is also as good as or even better than networks trained with sigmoid or tanh neurons. This result decreases the performance gap between deep networks trained with and without unsupervised pre-training. 

Rectifier neurons also naturally lead to a sparser network, making it suitable for naturally sparse data. The authors also argue that rectifier units are closer to a biological neuron's response in their main operating regime when compared to sigmoid or tanh neurons, bridging - in a sense - the gap between machine learning and neuroscience.
