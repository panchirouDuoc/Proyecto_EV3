# Análisis de Predicción de Ventas Altas (HighSales)

Este proyecto aplica técnicas de Ciencia de Datos para predecir 'HighSales' (Ventas Altas) a partir de un dataset de ventas de asientos de coche (`dataset_car_seats.csv`). El objetivo principal es identificar factores que influyen en las ventas altas y desarrollar un modelo predictivo robusto.

## Objetivo
Desarrollar un flujo completo que incluya limpieza de datos, análisis exploratorio (EDA), preprocesamiento, modelado supervisado para clasificación de 'HighSales', y optimización de hiperparámetros para seleccionar el mejor modelo predictivo.

## Estructura del Proyecto
El repositorio se organiza de la siguiente manera:
- `data/raw/`: Dataset original `dataset_car_seats.csv`.
- `data/processed`: Dataset procesado `x_train_scaled.csv`
- `notebooks/`: Notebook principal con el flujo de análisis `2Evaluacion 3.ipynb`.

## Metodología

### 1. Análisis Exploratorio y Preprocesamiento
- **Limpieza de datos:** Se revisaron valores nulos y se realizó un análisis inicial de distribución de datos.
- **Transformación de variables:**
    - Creación de la variable objetivo `HighSales` (1 si `Sales` > 8, 0 en caso contrario).
    - Conversión de precios (`CompPrice`, `Income`, `Price`) de USD a CLP utilizando APIs externas de cotización del dólar.
- **Codificación de variables categóricas:** Aplicación de `OneHotEncoder` a `ShelveLoc`, `Urban`, y `US`.
- **Estandarización de variables numéricas:** Uso de `StandardScaler` en `Sales_CLP`, `Advertising`, `Population`, `Age`, `Education`, `CompPrice_CLP`, `Income_CLP`, `Price_CLP`.
- **División de datos:** Separación en conjuntos de entrenamiento y prueba (`X_train`, `X_test`, `y_train`, `y_test`) con `stratify=y` para mantener la proporción de clases.

### 2. Modelado Supervisado y Optimización de Hiperparámetros
Se implementaron y evaluaron varios modelos de clasificación:
- Regresión Logística
- Árbol de Decisión
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Gaussian Naive Bayes

**Optimización de Hiperparámetros:** Se utilizó `RandomizedSearchCV`, `GridSearchCV` y **Validación Cruzada (K-Fold)** para encontrar la mejor combinación de parámetros y asegurar la robustez y generalización de los modelos.

### 3. Comparación de Modelos
Se realizó una comparación exhaustiva de todos los modelos basándose en métricas como Accuracy, Precision, Recall y F1-Score, tanto antes como después de la optimización de hiperparámetros y validación cruzada.

## Resultados Clave
- El modelo de **Regresión Logística** optimizado mostró el mejor rendimiento general con una precisión media en validación cruzada del **96.79%**.
- Otros modelos como **SVM** también obtuvieron buenos resultados después de la optimización, aunque ligeramente inferiores a la Regresión Logística.
- La selección final para la predicción de 'HighSales' recae en el modelo de Regresión Logística debido a su balance entre rendimiento y robustez.

## Requisitos
- Python 3.x
- Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Plotly, Dash, `requests`, `pyngrok`.

## Resources
- Colab Notebook: `2Evaluacion 3.ipynb`
- Dataset: `dataset_car_seats.csv`
- API Dólar: `https://cl.dolarapi.com/v1/cotizaciones/usd` and `https://mindicador.cl/api`

---
*asignatura: Programación para la Ciencia de Datos (SCY1101)*
