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
The authors first showed that modulatory signals based on error signs can effectively train multilayer neural networks for regression and classification tasks by using an error-sign-based modification of FDA, referred to as sDFA.
