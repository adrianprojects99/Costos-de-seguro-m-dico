# Costos-de-seguro-m-dico

#  Análisis de Datos para Costos de Seguros Médicos

##  Resumen del Proyecto

Este repositorio contiene la solución a la **Tarea 3** del curso de Inteligencia Artificial, la cual consiste en realizar un **Análisis de Datos Exploratorio (EDA)** profundo sobre factores que influyen en los costos de seguros médicos.

El objetivo principal es limpiar, transformar y comprender la relación de variables demográficas y de salud (como edad, IMC, fumador, etc.) con el costo final del seguro, para preparar un conjunto de datos robusto y preprocesado para la fase posterior de **modelado de Regresión**.

###  Dataset

* **Nombre:** Medical Insurance Cost Dataset
* **Fuente:** [Kaggle - mosapabdelghany/medical-insurance-cost-dataset](https://www.kaggle.com/datasets/mosapabdelghany/medical-insurance-cost-dataset)
* **Objetivo:** Analizar las variables que determinan el valor a pagar por el seguro médico (`charges`).

---

##  Metodología del Análisis de Datos

El proceso se ejecutó en etapas de limpieza, exploración y preparación del dataset, con justificación clara para cada transformación realizada.

### 1. Exploración de Datos (EDA Inicial)

* **Análisis del Conjunto de Datos y Descripción:** Revisión de tipos de datos, estructura y valores estadísticos básicos.
* **Tratamiento de Valores Vacíos (NaN):** Se identificaron y gestionaron los valores nulos. *(Se debe justificar si se eliminaron o se imputaron los valores y por qué esa elección fue la más adecuada para preservar la muestra).*
* **Transformaciones Iniciales:** Conversión de tipos de datos y *encoding* preliminar de variables categóricas si fue necesario.

### 2. Análisis Univariante

Se examinó la distribución individual de cada variable (numérica y categórica) para entender la composición de la muestra:

* **Deducciones Clave:** Se observaron y documentaron los patrones de concentración y distribución de cada variable.
    * *(Ejemplo: Edad):* "La distribución de la edad mostró una concentración uniforme, indicando una buena representación en todos los rangos de edad en la muestra."
    * *(Ejemplo: Fumador):* "Se observó que la proporción de individuos fumadores es significativamente menor que la de no fumadores."

### 3. Filtrado de Variables (Tratamiento de Outliers)

* **Método Aplicado:** Se utilizó el **[Método utilizado, ej. Rango Intercuartílico (IQR)]** para la identificación y eliminación de *outliers* extremos en las variables numéricas.
* **Justificación:** Este proceso es crucial para evitar que valores atípicos, especialmente en variables como el **IMC** o el costo final (`charges`), sesguen el rendimiento del modelo de regresión.

### 4. Tratamiento de la Variable Objetivo (`charges`)

* **Definición:** Se determinó si la variable objetivo, `charges` (costos del seguro), sería utilizada tal y como estaba o si requeriría una **transformación logarítmica** (ej. `log(charges)`).
* **Justificación:** *"(Ejemplo de justificación):* La variable `charges` presenta un sesgo positivo significativo (distribución asimétrica). Se aplicó una transformación logarítmica para hacer su distribución más gaussiana, mejorando la linealidad y el rendimiento de los modelos de regresión."

### 5. Análisis Bivariante

Se examinó la relación de cada variable de insumo contra la variable objetivo (`charges` o `log(charges)`) mediante gráficos de dispersión o cajas.

* **Relaciones Clave:**
    * *(Ejemplo: Objetivo vs. Fumador):* "Existe una relación claramente exponencial: los fumadores tienen un costo de seguro significativamente más alto que los no fumadores."
    * *(Ejemplo: Objetivo vs. IMC):* "Se observa una tendencia positiva: a medida que el IMC aumenta, el costo del seguro tiende a incrementarse, aunque con alta dispersión."

### 6. Matriz de Correlación

* **Análisis:** Se revisaron las correlaciones lineales entre todas las variables numéricas.
* **Redundancia:** Se identificaron **altas correlaciones** entre variables predictoras (ej. correlación entre `edad` e `IMC` si existiera).
* **Eliminación:** Se eliminó la variable con menos sentido teórico o menos correlacionada con la variable objetivo para reducir la multicolinealidad, justificando la decisión.

### 7. División y Guardado del Dataset

* **Regla:** El dataset preprocesado se dividió en conjuntos de entrenamiento (80%) y prueba (20%) para el modelado.
* **Estratificación:** Se aplicó la **estratificación contra la variable objetivo (`charges`)**. *(Nota: En problemas de Regresión, la estratificación se realiza discretizando la variable continua en "bins" o rangos para asegurar que la proporción de los rangos altos y bajos se mantenga similar en `train` y `test`.)*
* **Archivos Generados:** El dataset final se guardó en:
    * `data/train.csv`
    * `data/test.csv`

---

## 🔗 Referencia

Este análisis forma parte de un proyecto continuo de Inteligencia Artificial y ha sido enlazado en la página web del proyecto.

**(https://github.com/adrianprojects99/lab-costo-seguro-medico/tree/main)**
**https://lab-costo-seguro-medico-fnrcyiafdfmra2hygi9z8j.streamlit.app/**
**https://adrianprojects99.github.io/**
