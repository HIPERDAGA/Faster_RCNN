# Fast RCNN
![image](https://github.com/user-attachments/assets/a9c777ad-6c90-466c-910c-7803c5964d24)

## Estructura de una Fast RCNN
la estructura completa de la Faster R-CNN, organizada paso a paso:

### 1- Entrada de Imagen
La imagen de entrada se pasa a través de la red.

### 2- DEEP CNN (Red Neuronal Convolucional Profunda)
Una red base (como VGG16, ResNet, etc.) se utiliza para extraer características de la imagen completa.

### 3- RPN (Red de Propuestas de Regiones):
Una red completamente convolucional que toma las características extraídas por la DEEP CNN y genera propuestas de regiones (posibles ubicaciones de objetos).

### 4-Processing RPN Outputs
#### - Supresión No Máxima (NMS)
Se aplica para eliminar las propuestas de regiones redundantes y seleccionar las mejores propuestas.
#### - Anclajes (Anchors)
Se generan múltiples anclajes de diferentes tamaños y relaciones de aspecto en cada punto de la característica extraída.

### 5- ROI Pooling (Agrupación de Regiones de Interés)
Las regiones propuestas por la RPN se ajustan a un tamaño fijo y se extraen características específicas de cada región utilizando ROI Pooling o ROI Align.

### 6- Red de Detección
#### - Region CNN features
Las características específicas de cada región se pasan a través de una red para obtener características más detalladas.
#### - Box offset regressor
Ajusta las coordenadas de los cuadros delimitadores para cada región propuesta.
#### - Softmax classifier
Determina la clase de objeto presente en cada región propuesta.

### 7- Salida
Las coordenadas ajustadas de los cuadros delimitadores y las clases de objetos detectados se generan como salida final.

# DEEP CNN (Red Neuronal Convolucional Profunda)
![image](https://github.com/user-attachments/assets/4e84cbf1-ec6f-4265-a4ef-e68f62c4df12)

Es un componente crucial en la Faster R-CNN, ya que se encarga de extraer características de la imagen de entrada. 

## Función de la DEEP CNN
Su función es la extracción de características. La DEEP CNN toma la imagen de entrada y pasa por varias capas convolucionales, de activación y de agrupamiento (pooling) para extraer características de alto nivel. Estas características son representaciones abstractas de la imagen que capturan información relevante como bordes, texturas y formas.

## Ejemplos de Arquitecturas Comunes
#### 1- VGG16
Una red profunda con 16 capas que ha sido ampliamente utilizada en tareas de visión por computadora. Es conocida por su simplicidad y efectividad.
### 2- ResNet (Red Residual)
Introduce conexiones residuales que permiten entrenar redes mucho más profundas (como ResNet-50, ResNet-101). Estas conexiones ayudan a mitigar el problema de la degradación en redes profundas.
### 3- EfficientNet
Una familia de modelos que optimiza tanto la precisión como la eficiencia computacional. Utiliza un enfoque de escalado compuesto para ajustar la profundidad, el ancho y la resolución de la red.

## Proceso de Extracción de Características
### 1- Capas Convolucionales
Aplican filtros para detectar características locales en la imagen.
### 2- Capas de Activación (ReLU)
Introducen no linealidades para permitir que la red aprenda representaciones más complejas.
### 3- Capas de Agrupamiento (Pooling)
Reducen la dimensionalidad de las características, manteniendo la información más relevante y reduciendo la carga computacional.
### 4- Capas de Normalización
Ayudan a estabilizar y acelerar el entrenamiento.
### 5- Salida de la DEEP CNN
La salida de la DEEP CNN es un mapa de características que se pasa a la RPN para generar propuestas de regiones.
