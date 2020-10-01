# Models conversion
### Caffe to Keras:
**Instructions:**<br>
`python3 caffe2keras_converter.py <prototxt> <caffemodel> <output_dir> [--verbose]`<br>
Arguments:
* `prototxt`: The filename (full path including file extension) of the '.prototxt' file that defines the Caffe model
* `caffemodel`: The filename (full path including file extension) of the '.caffemodel' file that contains the network's parameters
* `output_dir`: The path to the directory where to save the Keras model and the file where you want the code to be written in

**Description:** the net's weights are taken with [`caffe_weight_converter.py`](https://github.com/AlexPasqua/caffe_weight_converter/blob/8a703e53c60ac6673f1091260065d090157ad8e0/caffe_weight_converter.py)