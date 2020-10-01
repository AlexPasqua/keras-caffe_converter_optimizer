# Keras-Caffe converter and optimizer
***This project is a NNs converter between Keras and Caffe (in both directions) and it includes pruning functionalities in Keras.***

### Overview:
1. [Conversion](#conversion)
2. [Optimization](#optimization)

<img src="https://images.exxactcorp.com/CMS/landing-page/resource-center/supported-software/logo/Deep-Learning/caffe.png" width="270" height="90"/>&nbsp;<img src="https://miro.medium.com/fit/c/1838/551/0*BrC7o-KTt54z948C.jpg" width="300" height="100"/>

### Conversion:
**Caffe** is known to be the most efficient framework for developing and deploying NNs. It's made to work with C++, a Python API exists, but it's still a bit uncomplete and not very well documented. Furthermore no pruning/optimization APIs are available.

**Keras** is one the most high level framework for NNs. It works with Python and it's the most approachable. Moreover there's a specific module for pruning: `tensorflow_model_optimization.sparsity`

This tool allows you to convert NNs from Caffe to Keras and back, so it's possible to work with the most approachable and high level framework and deploy your NNs in the most efficient one. It may also turn useful, for example, to manipulate NNs in Keras within a project that requires Caffe.


### Optimization:
In [`src/optimization/`](https://github.com/PARCO-LAB/keras-caffe_converter_optimizer/tree/master/src/optimization) prova prova prova