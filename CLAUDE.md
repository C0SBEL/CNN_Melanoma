# CLAUDE.md — Práctica 1: CNN Detección de Melanomas

## Contexto del proyecto

Clasificación binaria de lesiones cutáneas (Benign vs. Malignant) usando CNNs en PyTorch.
Entrega académica para el Máster en Data Science (MDS).

Restricción clave: la CNN no puede superar 250.000 parámetros.

## Estructura de carpetas

```
CNN/
├── Deliverable1.ipynb
├── melanoma_train_data_benign/Benign/        6289 imágenes train benignas
├── melanoma_train_data_malignant/Malignant/  5590 imágenes train malignas
└── melanoma_test_data/test/
    ├── Benign/    1000 imágenes test
    └── Malignant/ 1000 imágenes test
```

## Estructura del notebook (exacta según enunciado)

### 0. Carga de librerías y datos
Estado: completada (imports, rutas, listado de archivos).

### 1. Exploración de datos
- 1.1 Distribución de clases — Estado: completada
- 1.2 Inspección visual de muestras — Estado: completada
- 1.3 Análisis de propiedades de imagen — Estado: completada
- 1.4 Distribución de intensidades de píxeles por clase — Estado: completada
- 1.5 Imagen media por clase — Estado: completada
- 1.6 Técnicas de mejora de imagen (normalización, ecualización de histograma, filtrado de ruido) — Estado: pendiente
- 1.7 Data augmentation — Estado: pendiente

### 2. Diseño y entrenamiento de la CNN
- 2.1 Definición de la arquitectura
- 2.2 Preparación de DataLoaders
- 2.3 Entrenamiento baseline
- 2.4 Búsqueda sistemática de hiperparámetros
- 2.5 Entrenamiento del modelo óptimo

### 3. Explainability y análisis avanzado
- 3.1 Grad-CAM sobre predicciones correctas e incorrectas
- 3.2 Interpretación de patrones aprendidos

### 4. Optimización y validación
- 4.1 Early stopping y regularización
- 4.2 Evaluación final (Accuracy, F1-score, AUC)

### 5. Conclusión

## Convenciones de estilo

- Todo el trabajo va en Deliverable1.ipynb. No crear scripts externos.
- Idioma: español para markdown y comentarios, inglés para nombres de variables y funciones.
- Los comentarios van en párrafos de texto en celdas markdown al final de cada sección o subapartado.
- En las celdas de código solo se ponen los comentarios imprescindibles para entender el código.
- No usar caracteres especiales ni guiones decorativos en markdown ni en comentarios de código (evitar guiones largos, flechas, viñetas especiales, etc.).
- Seed fija: SEED = 42.
- Framework: PyTorch y torchvision.
- Estilo visual: color Benign #4C9BE8, color Malignant #E8694C.

## Decisiones tomadas en la Sección 1

- Input size: 128x128 px (imágenes originales ya son 224x224, ratio 1:1, modo RGB, sin corruptas).
- Normalización: media y desviación típica de ImageNet.
- Desbalanceo leve (53% Benign / 47% Malignant): monitorizar con F1 y AUC, no requiere oversampling agresivo.
- Data augmentation solo en train: flip horizontal y vertical, rotación hasta 30 grados, ColorJitter. Sin distorsiones morfológicas extremas.
- Kernels 3x3 adecuados para aprender texturas y formas locales.

## Criterios de evaluación

- 35%: Preparación de datos y exploración
- 40%: Desarrollo de arquitectura y entrenamiento
- 25%: Conclusiones, explainability y razonamiento

## Requisitos de la Sección 2 (CNN)

- Parámetros totales menor o igual a 250.000 (estricto).
- Ajuste de hiperparámetros: número de filtros, tamaño de kernels, learning rate, regularización, dropout, batch normalization.
- Búsqueda sistemática: comparar al menos 2 o 3 configuraciones documentadas.

## Requisitos de la Sección 3 (Explainability)

- Grad-CAM sobre imágenes de test: casos correctos e incorrectos de ambas clases.
- Interpretación de qué regiones activan la red y su relevancia clínica.

## Requisitos de la Sección 4 (Optimización y validación)

- Early stopping implementado durante el entrenamiento.
- Regularización: Dropout y BatchNorm.
- Métricas finales sobre el conjunto de test: Accuracy, F1-score, AUC.
