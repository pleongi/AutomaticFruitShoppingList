# Dockerfile 

This Dockerfile will install everything needed to use TensorFlow Object Detection API and run all the python scripts which contain this project.

Tensorflow Object Detection API depends on the following libraries:

* Protobuf 3.0.0
* Python-tk
* Pillow 1.0
* lxml
* tf Slim (which is included in the "tensorflow/models/research/" checkout)
* Jupyter notebook
* Matplotlib
* Tensorflow (>=1.12.0)
* Cython
* contextlib2
* cocoapi

You also need to follow the instructions explained in the following link:
https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md
* COCO API installation
* Protobuf Compilation
* Manual protobuf-compiler installation and usage
* Add Libraries to PYTHONPATH

## To build the Dockerfile
From this directory, build the image as follows (this takes a while): 
* docker build --tag detect-tf .

## Running the container
* docker run --rm -it --privileged -v C:\Users\Paula\Desktop\AutomaticFruitShoppingList:/AutomaticFruitShoppingList -p 8888:8888 detect-tf

As I want to share my git project folder, to modify it inside and outside the docker I have specified  -v C:\Users\Paula\Desktop\AutomaticFruitShoppingList:/AutomaticFruitShoppingList
<br />To open jupyter notebook, open in your browser http://localhost:8888/: password is root.
