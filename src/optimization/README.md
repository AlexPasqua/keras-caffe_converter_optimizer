# Models optimization
### Contents:
* [Simple classifier](#simple-classifier)
* [Retrain ResNet50 for CIFAR10](retrain-resnet50-for-cifar10)

---

### Simple classifier:
[`simple_classifier.py`](simple_classifier.py) creates a custom classifier for `Fashion MNIST`.<br>
It loads the dataset with the Keras API: `keras.datasets.fashion_mnist.load_data()`. It returns grayscale images of size 28x28 and the corresponding lables, 60000 samples for training and 10000 for testing.

### Retrain ResNet50 for CIFAR10: 