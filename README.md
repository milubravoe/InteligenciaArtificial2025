# InteligenciaArtificial2025
PROYECTO: Predicción del desempeño en las Pruebas Saber Pro

INTEGRANTES DEL EQUIPO

| Nombre Completo        			| Cédula         | Programa Académico                 |
|-----------------------------------|----------------|------------------------------------|
| Maria Camila Bravo     			| 1085943131     | Bioingeniería					  |            
| Sebastian Bedoya Restrepo      	| 1040048038     | Ingeniería de Sistemas			  |                    
| Jasmin Juliana Jaramillo Tapias 	| 1017163639     | Ingeniería de Sistemas 			  |

DESCRIPCIÓN DEL PROYECTO

Este proyecto forma parte de la competencia "Predicción del Desempeño en las Pruebas Saber Pro" de Kaggle.
El objetivo es desarrollar un modelo de clasificación supervisado que prediga el nivel de desempeño de los estudiantes
en las pruebas Saber Pro, categorizado en cuatro niveles:

- Bajo
- Medio-Bajo
- Medio-Alto
- Alto

REQUISITOS PREVIOS

Antes de ejecutar el notebook, asegúrate de tener instalado:

- Python ≥ 3.8
- Jupyter Notebook o Google Colab
- Librerías necesarias: pandas, numpy, scikit-learn, matplotlib, seaborn, kaggle

CONFIGURACIÓN DE LA API KEY DE KAGGLE

1. Inicia sesión en Kaggle: https://www.kaggle.com/
2. Acepta las reglas/condiciones de la competición
3. En tu perfil, selecciona "Account".
4. Busca la sección "API".
5. Crea un nuevo token con "Create New Token".
   Esto descargará el archivo kaggle.json.
6. Coloca el archivo kaggle.json en una ruta elegida
7. Al ejecutar la primera celda del notebook 01 - exploración.ipynb te pedirá la ubicación del archivo kaggle.json 

ESTRUCTURA DEL PROYECTO

SaberPro-Classifier/
│
├── README.md
├── 01 - exploración.ipynb

EJECUCIÓN DEL NOTEBOOK

1. Abre el notebook 01 - exploración.ipynb.
2. Verifica que tengas el archivo kaggle.json.
3. Ejecuta cada una de las celdas, el orden de la información esta estructurada así:
   - Cargar Datos
   - FUNCIONES
   - Visualización

CRÉDITOS

Proyecto desarrollado como parte de la competencia de aprendizaje automático
para la predicción del desempeño en las Pruebas Saber Pro.

RESUMEN TÉCNICO DEL NOTEBOOK

El notebook "01 - exploración.ipynb" desarrolla la primera fase del proyecto,
centrada en la exploración y análisis de los datos (EDA). A continuación se
detallan las etapas y procedimientos principales:

1. Extracción de datos desde Kaggle
   - Configuración de la API Key (`kaggle.json`) en Google Colab.
   - Descarga automática del dataset de la competencia.
   - Descompresión de los archivos y verificación de su contenido.

2. Carga de librerías y datasets
   - Librerías: pandas, numpy, matplotlib, seaborn, scikit-learn.
   - Archivos cargados: `train.csv`, `test.csv`, `submission_example.csv`.
   - Se verifican dimensiones, tipos de datos y estructura general.

3. Funciones auxiliares
   - resumen(): genera un resumen con tipos de datos, valores nulos, únicos y
     cantidad de registros no nulos.
   - encabezado(): muestra las primeras filas del dataset con estilo visual
     personalizado.

4. Análisis Exploratorio de Datos (EDA)
   - Análisis descriptivo de variables numéricas mediante `describe()`.
   - Clasificación de variables:
       - Binarias: se identifican y visualizan distribuciones.
       - Categóricas: se analizan columnas con alta cardinalidad.
       - Numéricas: se extraen variables de tipo continuo para estudio.
   - Visualización de la distribución de variables socioeconómicas:
       - Estrato de vivienda (`F_ESTRATOVIVIENDA`).
       - Educación del padre y madre (`F_EDUCACIONPADRE`, `F_EDUCACIONMADRE`).
       - Horas de trabajo semanal (`E_HORASSEMANATRABAJA`).

5. Identificación de la variable objetivo
   - La columna RENDIMIENTO_GLOBAL se establece como target para el modelo.
 

En conclusión, este notebook constituye la base exploratoria del proyecto,
proporcionando una visión detallada del dataset y preparando el terreno para las
siguientes etapas de limpieza, preprocesamiento y modelado predictivo.


-----ENTREGA 2----------

RESUMEN TÉCNICO DEL NOTEBOOK

El notebook “02 - preprocesamiento.ipynb” corresponde a la segunda fase del proyecto y tiene como objetivo limpiar, transformar y preparar los datos del conjunto de entrenamiento (train.csv) para su uso en modelos de aprendizaje automático.

Abrir el notebook 02 - preprocesamiento.ipynb Se recomienda abrirlo en Google Colab.

Carga de librerías y datasets

Librerías: pandas, numpy, matplotlib, seaborn, scikit-learn, itertools, json, os
Cargar los datos de entrenamiento

El notebook trabaja únicamente con los datos de entrenamiento (train.csv), ya que el objetivo es definir las transformaciones que luego se aplicarán a test.csv
Exploración de datos

Se realiza un análisis profundo de los datos para identificar tipos, categorías y valores faltantes
Limpieza de datos y tratamiento de valores faltantes
Ejecutar la celda que muestra el resumen general de nulos, tipos de dato y porcentaje de valores faltantes por columna.
Analizar qué columnas presentan información incompleta y de que tipo son
Imputación de valores faltantes, ejecutando la función imputar_moda() -->(categoría más frecuente).
Se verifica que despues del proceso no queden valores faltantes.
Se mapea por medio de la función mapear(), las columnas ordinales y binarias
Correlación de variables
Se genera la matriz de correlación
Se eliminan columnas redundantes
Se eliminar la columna ID (identificador del estudiante), ya que no aporta información al modelo.
Separación de variables predictoras y objetivo
Ejecutar la función separar_X_y() para dividir el DataFrame en: X: Variables predictoras. y: Variable objetivo (RENDIMIENTO_GLOBAL).
Codificación y estandarización
Se realiza el ColumnTransformer que incluye: StandardScaler → para variables numéricas. OneHotEncoder → para variables categóricas nominales (E_PRGM_ACADEMICO, E_PRGM_DEPARTAMENTO).
Se ejecutar el preprocesador y se confirma que las variables se han codificado correctamente.
Se Guarda la configuración del preprocesamiento
Usuario de Kaggle: https://www.kaggle.com/jasminjaramillo

Link video: https://www.youtube.com/watch?v=xAtlrqK1gHQ

---

-----ENTREGA FINAL----------

Los notebooks 
* 03 - XGBoost_y_SGDClassifier.ipynb
* 04 - KNN_ y_Random_Forest.ipynb
* 99 - modelo solución.ipynb

Siguen la siguiente estructura y se deben de ejecutar en el orden en que cada uno fue desarrollado:

1. Carga de datos (train y test) desde Kaggle o Drive
   Se realiza mediante API de Kaggle

2. Preprocesamiento completo
Incluye:
   Imputación de valores faltantes
      Variables categóricas → moda
      Variables numéricas → media
   Codificación y mapeo de variables ordinales y binarias
   Separación correcta de ID y target
   División en X y y
   train_test_split() para validación interna
   Construcción de pipelines con:
      ColumnTransformer
      Escalado
      Codificación OneHot
      Modelos (XGB, SGD, KNN y RF)

3. Optimización de hiperparámetros con Optuna

      Para realizar el entrenamiento, se acelero el proceso con Optuna, en donde se usaron estrategias como:
         Submuestreo del dataset
         Menor número de trials
         StratifedKFold con pocas particiones

4. Entrenamiento y evaluación final

Cada modelo se entrena con sus best_params y se evalúa con:
   Accuracy
   F1 score (weighted)
   Precision
   Recall
   Classification report

NOTA: En el notebook final (99 - modelo solución.ipynb) se selecciona el modelo ganador según Accuracy, que es el criterio de la competencia y únicamente este continua con el siguiente flujo:

5. Reentrena el modelo usando el 100% del dataset de entrenamiento y predice sobre test.csv.

6. Arma un Dataframe con los valores convertidos de los valores numéricos a categorías originales:
bajo, medio-bajo, medio-alto, alto con su correspondiente ID

7. Generación del archivo submission.csv 

  Guarda automáticamente el archivo en Google Drive Link: https://drive.google.com/file/d/1KqvzDd3aBgOWKBhnXAjGZkJzdzz70O3x/view?usp=drive_link 
  (Estan indicados los permisos para el grupo de trabajo, para el Profesor Raúl Ramos y para el monitor Jonathan Granda)

Link video: 

CRÉDITOS

Proyecto desarrollado como parte de la competencia de aprendizaje automático para la predicción del desempeño en las Pruebas Saber Pro.
