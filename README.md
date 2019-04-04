# GAMO: Generative Adversarial Minority Oversampling

The following is an implementation of a deep oversampling approach for classification in presence of class imbalance in image dataset. The algorithm can be described as a game between three players, where a classifier performs its usual actions, a generator attempts to create convex combination of points inside a class which are likely to be misclassified by the classifier, and a discriminator which enforces the generator to adhere the class distribution. 

## Reference
Mullick, Sankha Subhra, Shounak Datta, and Swagatam Das. "Generative Adversarial Minority Oversampling." arXiv preprint arXiv:1903.09730 (2019).

## Data and code files
The GAMO framework can be used on pre-computed feature vectors or flattened image. Additionally, GAMO can extract useful convolutional features from images by itself in an end-to-end fashion. To illustrate both of these features of GAMO framework we have provided a couple of exemplary codes, respectively applicable on MNIST (flattened image is taken as features) and Fashion-MNIST (deep convolutional features are extracted, where the network is simultaneously trained with the classifier). 

### Dependencies:
You can use either **python2.7 (and above) or python3** as per your choice.
Additionally you will need **keras (with any backend), scikit-learn, scipy, numpy, os, sys, opencv, pickle, matplotlib** as supporting libraries.

### Data preparation:
Neither MNIST nor Fashion-MNIST are sufficiently imbalanced in nature to test the efficacy of GAMO. Therefore,we subsample from the different classes and form a new training set with an imbalance ratio of 100. You can [download MNIST](http://yann.lecun.com/exdb/mnist/) and 
[download Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) from the sources, convert it to csv and respectively run the preprocessing script **MNIST_process.py** and **fMNIST_process.py** to create training and test sets which are similar to those used in our experiments.

### MNIST codes:
* Data files:
  * **Mnist_100_testData.csv** (testing dataset)
  * **Mnist_100_trainData.csv** (training dataset)
* Code files:
  * **dense_net.py** (network models)
  * **dense_suppli.py** (supplementary functions, for data loading, pre-processing, performance evaluation etc.)
  * **dense_gamo_main.py** (main code file for GAMO)

### Fashion-MNIST codes:
* Data files:
  * **fMnist_100_testData.csv**
  * **fMnist_100_trainData.csv**
* Code Files: (the naming convention follows from the MNIST)
  * **fashion_mnist_net.py**
  * **fashion_mnist_suppli.py**
  * **fashion_mnist_gamo_main.py**

### GAMO2pix:
A tool to visualize the feature vectors generated by GAMO in the original image space. This may be useful for an application which explicitly requires the artificially generated images, in addition to the trained classifier.
* Code files:
  * **fashion_mnist_gamo2pix_net.py**
  * **fashion_mnist_gamo2pix__main.py**
* Additional requirements:
  * **fashion_mnist_net.py**
  * **fashion_mnist_suppli.py**
  * trained generator network and class-specific generator output processing networks
  * trained convolutional network
  * training and test dataset

For example, some of the generated images for Fashion-MNIST when visualized by GAMO2pix are as follows, where the imbalance ratio compared to the majority class decreases from the top:


        GAMO/FashionMNIST_GAMO2pix.png
      

