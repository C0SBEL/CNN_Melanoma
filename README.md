# Detección de melanomas con redes neuronales convolucionales

Clasificación binaria de imágenes dermatoscópicas (**benigno / maligno**) con una CNN propia en PyTorch, desde el análisis exploratorio hasta la explicabilidad con Grad-CAM.

Práctica del Máster en Data Science (La Salle, Universitat Ramon Llull).

## Contenido

Todo el trabajo está en [`Deliverable1.ipynb`](Deliverable1.ipynb):

1. **Exploración de datos**: distribución de clases, propiedades de imagen, intensidades de píxel e imagen media por clase, técnicas de mejora de imagen y data augmentation.
2. **Diseño y entrenamiento de la CNN**: arquitectura propia, entrenamiento baseline y búsqueda sistemática de hiperparámetros (dropout, learning rate).
3. **Explicabilidad**: Grad-CAM sobre predicciones correctas e incorrectas e interpretación de los patrones aprendidos.
4. **Optimización y validación**: early stopping, regularización y evaluación final.

## Stack

Python · PyTorch · torchvision · scikit-learn · NumPy · Matplotlib · Pillow

## Resultados

Modelo final sobre el conjunto de test:

| Métrica  | Valor  |
|----------|--------|
| Accuracy | 0.872  |
| F1-score | 0.866  |
| AUC      | 0.952  |

Los pesos del mejor modelo están en `best_model.pth`.

## Cómo ejecutarlo

1. Instala las dependencias:
   ```bash
   pip install torch torchvision scikit-learn numpy matplotlib pillow jupyter
   ```
2. Descarga el dataset de imágenes de melanoma y colócalo en las carpetas (ya creadas con `.gitkeep`):
   ```
   melanoma_train_data_benign/Benign/
   melanoma_train_data_malignant/Malignant/
   melanoma_test_data/test/Benign/
   melanoma_test_data/test/Malignant/
   ```
3. Abre y ejecuta el notebook:
   ```bash
   jupyter notebook Deliverable1.ipynb
   ```

## Licencia

[MIT](LICENSE)
