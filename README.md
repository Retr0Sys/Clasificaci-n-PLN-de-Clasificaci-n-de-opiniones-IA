# Clasificaci-n-PLN-de-Clasificaci-n-de-opiniones-IA
## Modelo de Regresión Logística para la Clasificación Binaria de Opiniones a partir de Texto (LogisticRegression)

---
Este proyecto presenta la implementación de un modelo de **Aprendizaje Supervisado** (**Regresión Logística**) desarrollado en Python para la **clasificación binaria de opiniones** a partir de texto. El objetivo es clasificar los mensajes de texto como **positivo (1)** o **negativo (0)**, mediante la identificación de patrones lingüísticos y características textuales correlacionadas con la **polaridad de la opinión**.
---

\<div align="center"\> \<img src="[![ai-bot](https://github.com/user-attachments/assets/77b1e086-9728-48da-acc9-09a10dfff9a7)
)" alt="afa0e8\_0be0c0c7217d427dbc939dbd0017eea7" width="800"\> \</div\>

---

## 1\. Preprocesamiento y Ingeniería de Datos

La fase inicial es crucial y se centra en la preparación y transformación del *dataset* para su posterior análisis mediante técnicas de **Procesamiento del Lenguaje Natural (PLN)**.

### Proceso de Limpieza y Organización

  * **Inspección Estructural:** Se realiza una visualización inicial del conjunto de datos para comprender su conformación y la forma de las variables.
  * **Gestión de Valores Nulos y Duplicados:** Se emplean las funciones `.info()` y `df.isnull().sum()` para diagnosticar la cantidad de datos faltantes en las variables clave. Adicionalmente, se utiliza `df.drop_duplicates(inplace=True)` para verificar y eliminar cualquier registro duplicado, asegurando la calidad del *dataset*.
  * **Alineación de la Variable Objetivo:** La columna que contiene la polaridad de las opiniones en el *dataset* de entrenamiento (`dataset_train95.csv`) se renombra como **`etiqueta`** antes de la exportación final para cumplir con el formato requerido por la plataforma de *ranking*.

-----

## 2\. Desarrollo y Entrenamiento del Modelo

El modelo se entrena para establecer la relación probabilística entre el contenido del mensaje y su clasificación binaria de opinión.

### Variables Clave y Metodología

  * **Variable Independiente:** **`text`** (Contenido textual a analizar).
  * **Variable Dependiente (Objetivo):** **`etiqueta`** (Clasificación binaria de la opinión: 1 = positivo, 0 = negativo).
  * **Vectorización:** Se aplica un método de vectorización sobre la variable `declaracion` para transformar el contenido textual en una representación numérica que sea procesable por el algoritmo de *Machine Learning*.
  * **Validación Interna:** Para evaluar el rendimiento interno, el conjunto de datos de entrenamiento es dividido mediante la técnica de **`train_test_split`**. La función **`accuracy_score`** se utiliza para comprobar el porcentaje de acierto del modelo en el conjunto de prueba.

-----

## 3\. Evaluación y Validación Externa

La robustez del modelo se comprueba mediante la aplicación a un conjunto de datos ciego y una validación externa que simula un entorno real de competición.

### Proceso de Generación y Validación de Predicciones

1.  **Generación de Predicciones:** El modelo entrenado se aplica al conjunto de datos de prueba externo (`dataset_test_5_sin_etiqueta.csv`), que carece de la columna objetivo (`etiqueta`). El modelo genera y asigna los valores predictivos a esta columna.
2.  **Entrega Final:** El archivo resultante (`submission.csv`), que contiene el **ID** y la columna objetivo predicha (`etiqueta`), es exportado para su validación en la plataforma de *ranking*, donde se mide la eficiencia del modelo frente a los valores reales.
