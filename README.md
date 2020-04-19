# Lista de la compra automática de fruta mediante la detección de objetos en imágenes con Mask R-CNN

TRABAJO FINAL DE MÁSTER.<br />
Autor: Paula León Gil-Gibernau.
Tutor: Jerónimo Hernández González.
Profesor: Jordi Casas Roma.<br />
Universitat Oberta de Catalunya (UOC). Máster Universitario en Ciencia de Datos (Data Science).

## Resumen
El objetivo de este estudio es realizar de forma automática una lista de la compra de fruta.
Mediante un histórico de imágenes realizadas diariamente de un cajón de fruta, sin apilar, de una nevera, se aplicará una red neuronal convolucional profunda para detectar seis tipos de frutas en las imágenes. En concreto se usará una Mask R-CNN, que permite resolver la
segmentación por instancias en imágenes obteniendo así las clases, las máscaras y las cajas delimitadoras de las frutas en las imágenes.<br />
**Palabras clave**: Red neuronal convolucional profunda, detección de frutas, detección de objetos, máscaras, segmentación de instancias, aprendizaje automático, lista de la compra automática

## Abstract
The aim of this project is to generate an automatic fruit shopping list. To do so, we will use a history of images taken daily, of a refrigerator fruit drawer, containing only unstacked fruit. We will apply a deep convolutional neural network to detect six different classed of fruit in the images. In particular, we will use Mask R-CNN, which allows solving the instance segmentation in images, being able to obtain the bounding boxes, the masks and the classes of the fruits which appear in the images.<br />
**Keywords**: Deep convolutional neural network, Fruit detection, Object detection, Masks, Instance segmentation, Machine learning, Automatic shopping list

## **Tabla de contenidos:**

### **Código:**
* **Codigo/get_imagenet_data.ipynb**: python notebook que contiene el código para bajar imágenes de ImageNet de las 6 clases de frutas.
* **Codigo/TensorFlow/workspace/label_map.pbtxt**: TensorFlow requiere un mapa de clases, que mapea cada clase de fruta con un valor integer. Este mapa se usa tanto para el proceso de entrenamiento como para el de detección. 
* **Codigo/TensorFlow/workspace/mask_rcnn_inception_resnet_v2_atrous_coco.config**: fichero que contiene la configuración para volver a entrenar el modelo mask_rcnn_inception_resnet_v2_atrous_coco ya entrenado.
* **Codigo/TensorFlow/workspace/mask_rcnn_resnet101_atrous_coco.config**: fichero que contiene la configuración para volver a entrenar el modelo mask_rcnn_resnet101_atrous_coco ya entrenado.

### **Documentación:**
* **Documentacion/TFM_pleongi.pdf**: PDF que contiene la memoria del TFM.
* **Documentacion/TFM_pleongi.zip**: zip que contiene los archivos usados para generar el PDF con Latex.

### **docker:**
* **docker/Dockerfile.pdf**: Dockerfile que contiene la instalación de todo lo necesario para utilizar la TensorFlow Object Detection API y para ejecutar todos los scripts de python que tiene este proyecto. 
* **docker/README.md**: contiene la explicación de cómo crear y ejecutar la imagen docker.

