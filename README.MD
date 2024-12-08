
# Clasificación de Variedades de Uva con Random Forest

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar un modelo de clasificación para identificar la variedad de uva con base en características químicas y visuales de muestras de vino. Utilizando **Random Forest** como modelo definitivo, se lograron registrar los experimentos y las métricas en **MLflow**, así como analizar la importancia de las variables y realizar predicciones para nuevas muestras.

---

---

## Flujo de Trabajo

### 1. Carga y Exploración de los Datos

- Se cargaron los datos (asumir que el dataset está en `data/wine_dataset.csv`).
- Columnas:
  - `CLASS`: Variedad de uva (variable objetivo).
  - Características químicas como `ALCOHOL`, `MALIC ACID`, `ASH`, `MAGNESIUM`, etc.
- Se verificaron valores nulos y se exploraron valores atípicos con gráficos de bigotes.

### 2. Preprocesamiento de Datos

- Tratamiento de valores atípicos utilizando **recorte con IQR**.
- Balanceo de clases con **SMOTE**:
  - Clase 1: 59 datos.
  - Clase 2: 71 datos.
  - Clase 3: 48 datos.
  - Después de SMOTE, todas las clases tienen 71 datos (o un número similar, dependiendo del método de sobremuestreo).

### 3. Modelos Entrenados

Se evaluaron los siguientes modelos:

- **Regresión Logística**
- **Random Forest** (Modelo Seleccionado)
- **Support Vector Machine (SVM)**

Los modelos fueron entrenados y evaluados usando métricas como precisión, exactitud (Accuracy), AUC-ROC y matriz de confusión.

### 4. Registro en MLflow

- Todos los experimentos fueron registrados en **MLflow**.
- Métricas registradas:
  - `accuracy`
  - `roc_auc`
  - `precision`
  - `recall`
  - `f1_score`
- Artefactos registrados:
  - Matriz de confusión.
  - Importancia de las variables.
  - Modelo entrenado.

### 5. Análisis de Importancia de Variables

Se analizó la importancia de las variables utilizando los valores proporcionados por **Random Forest**. Las características más relevantes incluyen:

- `FLAVONOIDS`
- `PROLINE`
- `COLOR_INTENSITY`  (Este análisis se encuentra en el notebook y en los artefactos de MLflow)

### 6. Predicción con Nuevas Muestras

El modelo definitivo (Random Forest) se usó para predecir la variedad de uva en dos nuevas muestras:

```plaintext
Muestra 1: [13.72, 1.43, 2.5, 16.7, 108, 3.4, 3.67, 0.19, 2.04, 6.8, 0.89, 2.87, 1285]
Muestra 2: [12.37, 0.94, 1.36, 10.6, 88, 1.98, 0.57, 0.28, 0.42, 1.95, 1.05, 1.82, 520]
```

Resultados:

Muestra 1: Clase 1
Muestra 2: Clase 3


---

## Requisitos

- Python 3.9 o superior.
- Librerías:
  - pandas
  - numpy
  - scikit-learn
  - matplotlib
  - seaborn
  - imblearn
  - mlflow

---

## Cómo Reproducir

1. Clona este repositorio:
   ```bash
   git clone <URL_del_repositorio>
   cd <nombre_del_repositorio>
   ```

2. Crea un entorno virtual (Recomendado):
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  #Linux/macOS
   .venv\Scripts\activate  #Windows
   ```

3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Configura MLflow (si se usa Databricks, sigue sus instrucciones):
   - Crea un experimento en MLflow.  Anota el `experiment_id`.

5. Abre el archivo notebook (`wine_classification.ipynb`) en tu entorno Jupyter o Databricks.  Actualiza el `experiment_id` en el código si es necesario.

6. Ejecuta el notebook.

---

## Resultados

- **Modelo seleccionado:** Random Forest
- **Métricas del modelo:** (Estos valores deben ser obtenidos de la ejecución del notebook y MLflow)
    - Accuracy:  1
    - ROC_AUC: 1


- La importancia de las variables y la matriz de confusión están disponibles en la interfaz de MLflow.

---

## Conclusiones

Random Forest demostró ser un modelo robusto para este problema, mostrando una alta precisión en la clasificación de variedades de uva.  `FLAVONOIDS` fue la variable más importante para la clasificación, según el modelo.  El proyecto proporciona una base sólida para futuros desarrollos en la clasificación de vinos.



![alt text](https://github.com/demolinar/WINE_CLASSIFICATION/blob/main/images/ml0.png)
![alt text](https://github.com/demolinar/WINE_CLASSIFICATION/blob/main/images/ml1.png)
![alt text](https://github.com/demolinar/WINE_CLASSIFICATION/blob/main/images/ml2.png)




