# Keras-Caffe converter and optimizer
***This project is a NNs converter between Keras and Caffe (in both directions) and it includes pruning functionalities in Keras.***

### Overview:
1. [Conversion](#conversion)
2. [Optimization](#optimization)
3. [Results](#results)

<img src="https://images.exxactcorp.com/CMS/landing-page/resource-center/supported-software/logo/Deep-Learning/caffe.png" width="270" height="90"/>&nbsp;<img src="https://miro.medium.com/fit/c/1838/551/0*BrC7o-KTt54z948C.jpg" width="300" height="100"/>

### Conversion:
**Caffe** is known to be the most efficient framework for developing and deploying NNs. It's made to work with C++, a Python API exists, but it's still a bit uncomplete and not very well documented. Furthermore no pruning/optimization APIs are available.

**Keras** is one the most high level framework for NNs. It works with Python and it's the most approachable one, moreover there's a specific module for pruning: `tensorflow_model_optimization.sparsity`

This project allows you to convert NNs from Caffe to Keras and back, so it's possible to work with the most approachable and high level framework to later deploy your NNs in the most efficient one. It may also turn useful, for example, to manipulate NNs in Keras within a project that necessarily requires Caffe.


### Optimization:
In [`src/optimization/`](https://github.com/PARCO-LAB/keras-caffe_converter_optimizer/tree/master/src/optimization) there are 2 demo scripts to test Keras' pruning functionalities.
* [`simple_classifier.py`](https://github.com/PARCO-LAB/keras-caffe_converter_optimizer/tree/master/src/optimization/simple_classifier.py) creates and prune a small custom model for image classification
* [`retrain_resnet50_cifar10.py`](https://github.com/PARCO-LAB/keras-caffe_converter_optimizer/tree/master/src/optimization/retrain_resnet50_cifar10.py) is an example of transfer learning with pruning. The scripts loads ResNet50 with imagenet weights, adapt the net to perform classifications on `CIFAR10` and implements pruning functionalities.


### Results:
#### Conversion:
to be filled

#### Pruning:
to be filled