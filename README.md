# Keras-Caffe converter and optimizer
***This project is a NNs converter between Keras and Caffe (in both directions) and it includes pruning functionalities in Keras.***

### Overview:
1. [Directories structure](#directories-structure)
2. [Conversion](#conversion)
3. [Optimization](#optimization)
4. [Results](#results)

**Directories structure:**<br>
```
  keras-caffe_converter_optimizer
    |-- src
    |   |-- op_kp_printer.cpp
    |   |-- conversion
    |   |   |-- caffe2keras_converter.py
    |   |   |-- keras2caffe_converter.py
    |   |   |-- caffe2keras
    |   |   |   |-- create_nn_struct.py
    |   |   |   |-- caffe_weight_converter
    |   |   |   |   |-- caffe_weight_converter.py
    |   |   |-- keras2caffe
    |   |   |   |-- create_prototxt.py
    |   |   |   |-- k2c_1.py
    |   |   |   |-- k2c_2.py
    |   |   |-- README.md
    |   |-- optimization
    |   |   |-- simple_classifier.py
	|   |   |-- retrain_resnet50_cifar10.py
	|   |   |-- README.md
```

### Conversion:
<img src="https://images.exxactcorp.com/CMS/landing-page/resource-center/supported-software/logo/Deep-Learning/caffe.png" width="270" height="90"/>&nbsp;<img src="https://miro.medium.com/fit/c/1838/551/0*BrC7o-KTt54z948C.jpg" width="300" height="100"/>

**Caffe** is known to be the most efficient framework for developing and deploying NNs. It's made to work with C++, a Python API exists, but it's still a bit uncomplete and not very well documented. Furthermore no pruning/optimization APIs are available.

**Keras** is one the most high level framework for NNs. It works with Python and it's the most approachable one, moreover there's a specific module for pruning: `tensorflow_model_optimization.sparsity`

This project allows you to convert NNs from Caffe to Keras and back, so it's possible to work with the most approachable and high level framework to later deploy your NNs in the most efficient one. It may also turn useful, for example, to manipulate NNs in Keras within a project that necessarily requires Caffe.<br>

**User instructions:** see the [apposite README.md](src/conversion/README.md)


### Optimization:
In [`src/optimization/`](/src/optimization) there are 2 demo scripts to test Keras' pruning functionalities.
* [`simple_classifier.py`](src/optimization/simple_classifier.py) creates and prune a small custom model for image classification
* [`retrain_resnet50_cifar10.py`](src/optimization/retrain_resnet50_cifar10.py) is an example of transfer learning with pruning. The scripts loads ResNet50 with imagenet weights, adapt the net to perform classifications on `CIFAR10` and implements pruning functionalities.

**User instructions:** see the [apposite README.md](src/optimization/README.md)


### Results:
**Conversion:**
The models conversion has been tested with [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose). I created a C++ script ([`op_kp_printer.cpp`](src/op_kp_printer.cpp)) to be placed in `openpose/examples/user_code/` to process the frames from a video input and write all the keypoints (code, name and coordinates) in a csv file. Then, giving that file as input to [`INDE_performance_test`](https://github.com/PARCO-LAB/INDE_performance_test) the following graphs were extracted:<br>
The first one was generated using the original [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose)'s models
![](data/original_models_test.png?raw=true)
The second one with those models converted from Caffe to Keras and back to Caffe
![](data/complete_conversion_test.png?raw=true)
As it's possible to notice, they're basically identical, so *the conversion back and forth does not introduce any error nor approximation.*

**Pruning:**<br>
[`simple_classifier.py`](src/optimization/simple_classifier.py):
* Base model avarage accuracy: 0.8963
* Pruned model avarage accuracy: 0.8945
* Base model avarage evaluation time: 0.6029
* Pruned model avarage evaluation time: 0.2979<br>

[`retrain_resnet50_cifar10.py`](src/optimization/retrain_resnet50_cifar10.py):
* Base model avarage accuracy: 0.8123
* Pruned model avarage accuracy: 0.8001
* Base model avarage evaluation time: 5.2928
* Pruned model avarage evaluation time: 4.2747