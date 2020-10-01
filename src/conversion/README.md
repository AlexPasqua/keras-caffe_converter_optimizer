# Models conversion
### Contents:
* [Caffe to Keras](#caffe to keras)
* [Keras to Caffe](#keras to caffe)
### Caffe to Keras:
**Instructions:**<br>
`python3 caffe2keras_converter.py <prototxt> <caffemodel> <output_dir> [--verbose]`<br>
Arguments:
* `prototxt`: The filename (full path including file extension) of the '.prototxt' file that defines the Caffe model
* `caffemodel`: The filename (full path including file extension) of the '.caffemodel' file that contains the network's parameters
* `output_dir`: The path to the directory where to save the Keras model and the file where you want the code to be written in

**Description:** the net's weights are taken with [`caffe_weight_converter.py`](https://github.com/AlexPasqua/caffe_weight_converter/blob/8a703e53c60ac6673f1091260065d090157ad8e0/caffe_weight_converter.py) which also manipulates them in order to match Keras' requirements.<br>
[`create_nn_struct.py`](caffe2keras/create_nn_struct.py) goes through the Caffe net and creates an equivalent network structure in Keras. It generates also the Python file containing the source code necessary to create that structure, so it's possible to manually modify or check it.

---

### Keras to Caffe:
**Instructions:**<br>
`python3 keras2caffe_converter.py <keras_model> <output_dir> [--caffemodel_name CAFFEMODEL NAME] [--prototxt PROTOTXT]`<br>
Arguments:
* `keras_model`: The filename (full path including extension) of the file that contains the Keras model
* `output_dir`: The path to the output directory where to save th caffemodel (and prototxt if necessary)
* `--caffemodel_name CAFFEMODEL_NAME`: The name (WITHOUT extension) of the file where to save the Caffe model
* `--prototxt PROTOTXT`: The filename (full path including file extension) of the '.prototxt' file that defines the Caffe model