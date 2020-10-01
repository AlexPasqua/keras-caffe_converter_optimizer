# Models optimization
### Contents:
* [Simple classifier](#simple-classifier)
* [Retrain ResNet50 for CIFAR10](#retrain-resnet50-for-cifar10)

---

### Simple classifier:
How to use: `python3 simple_classifier`

[`simple_classifier.py`](simple_classifier.py) creates a custom classifier for `Fashion MNIST`.<br>
It loads the dataset with the Keras API: `keras.datasets.fashion_mnist.load_data()`. It returns grayscale images of size 28x28 and the corresponding lables, 60000 samples for training and 10000 for testing.<br>
**Model architecture:** it's a sequential model with the following layers:
* `InputLayer`: input shape = 28x28
* `Reshape`: target shape = 28x28x1
* `Convolution`: 12 filters, kernel size = 3x3, activation ReLU
* `Max pooling`: pool size 2x2
* `Flatten`: to transform the data into a 1-dimensional vector
* `Fully connected`: 128 neurons, activation ReLU
* `Fully connected`: 10 neurons, activation **softmax** to get the 10 classes' probability score<br>
Base model avarage accuracy: 0.8963<br>
Pruned model avarage accuracy: 0.8945<br>
Base model avarage evaluation time: 0.6029<br>
Pruned model avarage evaluation time: 0.2979<br>

---

### Retrain ResNet50 for CIFAR10:
How to use: `python3 retrain_resnet50_cifar10.py [--mode {create, prune, evaluate}]`<br>
Arguments:
* `-m --mode`:
	* `create`: import ResNet50 from Keras.applications and load it with pretrained imagenet weights. Then it adds some layer to adapt the model for performing classifications on cifar10
	* `prune`: load model (it must be already created and saved) and prune it. Then it performs a comparison with the base model
	* `evaluate`: load the model (it must be already created and saved) and evaluate it

The base ResNet50 is created using the Keras API `resnet = applications.ResNet50(include_top=False, weights='imagenet')`, but then the model needs to be adapted to perform classifications on `CIFAR10`, so the following layers are added after ResNet50's output:
* `Flatten`: to transform the data into a 1-dimensional vector
* `BatchNormalization`
* `Fully connected`: 128 neurons, activation ReLU
* `Dropout`: 50%
* `BatchNormalization`
* `Fully connected`: 64 neurons, activation ReLU
* `Dropout`: 50%
* `BatchNormalization`
* `Fully connected`: 64 neurons, activation **softmax** to get the 10 classes' probability score<br>