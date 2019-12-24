You can find the paper [here](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf).

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Significance**

With well over 50,000 citations till date, this 2012 paper by Geoffrey Hinton's group at University of Toronto is a seminal paper in computer vision and regarded as one of the papers that established Convolutional Neural Networks in the forefront for image classification tasks. A variant of the deep CNN proposed here was entered in the ILSVRC (ImageNet Large-Scale Visual Recognition Challenge) 2012, which won with a top-5 error rate of 15.3%, outperforming the second-place winner (26.2%) by a large margin.

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Summary**

This paper came at a time when two important (and very fortunate) things happened almost at the same time: large, labeled datasets consisting of millions of images became available for feeding data-hungry giant networks; and powerful GPUs capable of running such large-scale networks also became available. The authors trained one of the largest CNNs of that time on the subsets of ImageNet dataset that were used in 2010 and 2012 competitions using a highly-optimized GPU implementation of 2D convolution; and experimented with several techniques to improve performance, reduce training time and reduce overfitting. Their experiments suggested that these results can be improved upon by simply waiting for faster GPUs and bigger datasets.

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Dataset**

The ImageNet dataset consists of 15 million labeled high-resolution images from 22,000 categories, collected from the web and labeled manually. The ILSVRC challenge uses a subset of ImageNet with roughly 1000 images from each of 1000 categories, summing up to about 1.2 million training images, 50,000 validation images and 150,000 test images. The images have variable resolution, so they were first downsampled to a fixed resolution of 256x256 and the mean activity over the entire training set was subtracted from each pixel.

![#1589F0](https://placehold.it/15/1589F0/000000?text=+) **Proposed Approach**

The CNN used in the paper had 5 convolutional and 3 fully-connected layers. Interestingly, the authors found that removing any convolutional layer (each of which has <1% of the model's parameters) resulted in a deterioration in performance. The characteristic features of the proposed architecture are listed below in the order of importance:
- **ReLU nonlinearity:** Training with gradient descent on saturating neurons typically takes much more time than training on non-saturating nonlinearities like ReLU (f(x) = max(0, x)). So ReLU was a natural choice for training such a large network on a large dataset.
- **Training on multiple GPUs:** Memory size of a single GPU limits the maximum network size that can be trained on it. The authors spread the network over 2 GPUs and tuned the architecture so that cross-GPU communication was an acceptable fraction of the total amount of computation. Half of the kernels (neurons) were put on each GPU, and additionally, the GPUs only communicated in certain layers while taking inputs from kernels residing on the same GPU for other layers. They note that compared to a network with half as many kernels in each conv layer trained on one GPU, the 2-GPU net reduces top-1 and top-5 error rates by 1.7% and 1.2% respectively.
