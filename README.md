![image](https://github.com/user-attachments/assets/a9c777ad-6c90-466c-910c-7803c5964d24)

# Estructura de una Fast RCNN
la estructura completa de la Faster R-CNN, organizada paso a paso:

## 1- Entrada de Imagen
La imagen de entrada se pasa a través de la red.

## 2- DEEP CNN (Red Neuronal Convolucional Profunda)
Una red base (como VGG16, ResNet, etc.) se utiliza para extraer características de la imagen completa.

## 3- RPN (Red de Propuestas de Regiones):
Una red completamente convolucional que toma las características extraídas por la DEEP CNN y genera propuestas de regiones (posibles ubicaciones de objetos).

## 4-Processing RPN Outputs
### - Supresión No Máxima (NMS)
Se aplica para eliminar las propuestas de regiones redundantes y seleccionar las mejores propuestas.
### - Anclajes (Anchors)
Se generan múltiples anclajes de diferentes tamaños y relaciones de aspecto en cada punto de la característica extraída.

## 5- ROI Pooling (Agrupación de Regiones de Interés)
Las regiones propuestas por la RPN se ajustan a un tamaño fijo y se extraen características específicas de cada región utilizando ROI Pooling o ROI Align.

## 6- Red de Detección
### - Region CNN features
Las características específicas de cada región se pasan a través de una red para obtener características más detalladas.
### - Box offset regressor
Ajusta las coordenadas de los cuadros delimitadores para cada región propuesta.
### - Softmax classifier
Determina la clase de objeto presente en cada región propuesta.

## 7- Salida
Las coordenadas ajustadas de los cuadros delimitadores y las clases de objetos detectados se generan como salida final.
