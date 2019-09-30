You can find the paper [here](https://arxiv.org/pdf/1909.01311.pdf).

**Summary**   
This paper shows that only error sign information, and not the explicit errors, is sufficient to maintain feedback alignment and provide learning in the hidden layers. This solves the weight transport problem (symmetry requirement between forward and backward weights), removes update locking and leads to a purely feedforward algorithm that only needs a label-dependent random vector selection for estimating layerwise loss gradients. 

**Related work**   
Feedback Alignment (FA) and Direct Feedback Alignment (DFA): solves the weight transport problem, but not update locking, because a full forward pass still needs to be done before the exact error can be determined.  
Error locality approaches which rely on layerwise loss functions: still suffer from update locking at the layer-scale because they need single-layer forward and backward passes. 

**Proposed approach**   
The proposed DRTP algorithm solves both the weight transport and update locking problems by projecting the targets (one-hot encoded labels) instead of the error onto the hidden layers. Key advantages include:  
a) No neeed for dedicated feedback pathways.    
b) Independent update of layers possible because a full forward pass is not required, reducing memory overhead.    
Thus DRTP is **purely feedforward** and **low cost**, ideal for use in edge computing devices with memory and power constraints.

**Results**   
The authors first showed that modulatory signals based on error signs can effectively train multilayer neural networks for regression and classification tasks by using an error-sign-based modification of FDA, referred to as sDFA. They are able to show that modulatory signals based only on error signs are within 90 degrees of those provided by BP, and hence are able to train multi-layer networks.  

Now comes the most beautiful part...  

*We don't even need to wait for a full forward pass to know the error sign in classification, because we already know it!*   

How? The output layer nonlinearity (usually signoid or softmax) in multi-layer networks bounds the output values between 0 and 1. This, for one-hot encoded labels, ensures that the error sign (output neuron response - binary label) is negative for the target class, and positive for every other class. So not only is DRTP free from weight transport, it is also free from update locking, because we know what the error sign is for each example at every training step! But what the authors actually do, is take the target labels as a kind of surrogate for the error sign - making DRTP a simplified version of sDFA. It works, because there is a one-to-one mapping from the target vector to the error sign vector - the target vector is basically a shifted and rescaled version of the error sign vector. And one easy reason why this is better for us is because the target vector has all zeroes except 1, making it less computation-heavy, whereas all elements in the error sign vector are non-zero.

The authors also show that the directions of DRTP and BP modulatory signals are within 90 degrees of each other, so that DRTP is able to align the weights so as to decrease the output error. Results on MNIST and CIFAR-10 datasets show that the mean test error for DRTP is reasonably close to BP, FA and DFA. 

**Discussions**
The paper proposes a simple approach for training multi-layer networks that removes both weight-transport and update-locking problems of BP-based methods. This solves the key biological implausibility issues, as well as reducing hardware requirements in memory and computation. This approach also has a potential in developing neuromorphic algorithms using the three-factor synaptic plasticity rules, which state that pre- and post-synaptic activities are modulated by a local dendritic voltage that integrates higher-order feedback. For DRTP, these modulatory signals would be based on the targets themselves.
