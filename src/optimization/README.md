# Models optimization
### Contents:
* [Simple classifier](#simple-classifier)
* [Retrain ResNet50 for CIFAR10](#retrain-resnet50-for-cifar10)

---

### Simple classifier:
[`simple_classifier.py`](simple_classifier.py) creates a custom classifier for `Fashion MNIST`.<br>
It loads the dataset with the Keras API: `keras.datasets.fashion_mnist.load_data()`. It returns grayscale images of size 28x28 and the corresponding lables, 60000 samples for training and 10000 for testing.<br>
**Model architecture:** it's a sequential model with the following layers:
* `InputLayer`: input shape = 28x28
* `Reshape`: target shape = 28x28x1
* `Convolution`: 12 filters, kernel size = 3x3, activation ReLU
* `Max pooling`: pool size 2x2
* `Flatten`: to transform the data into a 1-dimensional vector
* `Fully connected`: 128 neurons, activation ReLU
* `Fully connected`: 10 neurons, activation **softmax** to get the 10 classes' probability score

---

### Retrain ResNet50 for CIFAR10: 