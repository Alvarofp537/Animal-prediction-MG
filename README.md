# Clasificación de Imágenes de Animales con VGG16 

Este proyecto implementa un clasificador de imágenes en **10 clases de animales** usando **transfer learning** con la red convolucional **VGG16** preentrenada en *ImageNet*.

## Contexto
El proyecto surge como parte de la competición de Kaggle:

[MG Animal Prediction 25-26](https://www.kaggle.com/competitions/mg-animal-prediction-25-26/data)

De ahí se han obtenido los datos originales: un conjunto de **21,179 imágenes** de animales distribuidas en **10 clases**:
- `cane`, `cavallo`, `elefante`, `farfalla`, `gallina`,  
  `gatto`, `mucca`, `pecora`, `ragno`, `scoiattolo`.

Las imágenes presentan dimensiones y proporciones variables, lo que nos obliga a un reescalado previo para ajustarlas a la entrada de la red VGG16 (224x224).

## Características
- Dataset: **21,179 imágenes** de 10 clases.
- Entrada: imágenes reescaladas a **224x224** para VGG16.
- Arquitectura:
  - **VGG16** como *feature extractor* (no entrenable).
  - Clasificador denso con **4 capas densas** + **Dropout**.
  - Activaciones ReLU en capas ocultas y **Softmax** en la salida para clasificación multiclase.
- Entrenamiento en dos fases:
  1. Entrenamiento inicial del clasificador.
  2. Re-entrenamiento/fine-tuning cargando el modelo previamente guardado.
- El formato de subida del resultado será un archivo **.csv** con las siguientes columnas:

    ```csv
    id,category
    nombre_imagen, categoría
    ...
    
