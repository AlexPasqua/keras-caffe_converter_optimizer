# Models conversion
### Caffe to Keras:
**Instructions:**<br>
`python3 caffe2keras_converter.py <prototxt> <caffemodel> <output_dir> [--verbose]`<br>
Arguments:
* `prototxt`: The filename (full path including file extension) of the '.prototxt' file that defines the Caffe model
* `caffemodel`: The filename (full path including file extension) of the '.caffemodel' file that contains the network's parameters
* `output_dir`: The path to the directory where to save the Keras model and the file where you want the code to be written in