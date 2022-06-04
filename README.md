# Loan prediction using machine learning
Predicción de la aprobación de un credito. 

Integrantes:

Juan Sebastián Castrillón

Carlos Humberto Diaz

## Introducción del proyecto

Se utilizó el siguiente dataset: https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset

Este conjunto de datos cuenta con 642 muestras que representan personas que han solicitado un credito, cada usuario tiene asignado un ID, se presentan 11 caracteristicas dentro de este dataset, entre los que se encuentra; el genero, si se encuentra casado, el nivel de educación, si es trabajador independiente, los ingresos del aplicante, ingresos del coaplicante, la cantidad de dinero solicitada, si presenta histroial crediticio y el tipo de propiedad en la que reside. Como etiquetas se tiene si el credito fue aprobado o no. El dataset incluye un conjunto de prueba el cual no cuenta con etiquetas, con el fin de generar las predicciones y validarlas en la siguiente pagina: https://datahack.analyticsvidhya.com/contest/practice-problem-loan-prediction-iii/#LeaderBoard.

## Desarrollo

### 1. Identificación del problema

Revisando el conjunto de datos determinamos que es un problema de clasificación binaria, debido a que se tienen etiquetas para las muestras y estas toman unicamente dos valores.

### 2. Analisis y limpieza de los datos

Incialmente se importarón los datos, luego de esto se revisaron las columnas que presentan valores nulos y la cantidad de estos, obteniendo los siguientes resultados.

![image](https://user-images.githubusercontent.com/106851565/171973897-87b40b09-c1ee-4162-be59-6c06c6c98f4d.png)

Posteriormente definimos las estrategias para rellenar los valores nulos, para LoanAmount se utilizo la media del resto de valores y para el resto de caracteristicas se utilizó la moda. Una vez eliminados todos los valores NaN realizamos un analisis de las diferentes caracterisitcas, iniciando con un histograma de todas las caracteristicas numericas.

![image](https://user-images.githubusercontent.com/106851565/171975189-a84740c0-b69d-4f77-bb08-2414ed3ea478.png)

Encontramos que la mayoria de las muestras cuentan con historial crediticio, la mayor parte de los creditos solicitados son a un termino de 360 y que el ingreso de gran parte de los solicitantes es menor a 10000. Posteriormente hallamaos la distribución de los creditos aprobados en relación a diferentes caracteristicas categoricas.

De la siguiente grafica determinamos que la mayoria de los solicitantes son hombres y que la distribución de creditos aprobados es similar sin importar el genero.
![download](https://user-images.githubusercontent.com/106851565/171975345-cbbda6d6-66e2-4308-8005-83382d8d56af.png)

La siguiente grafica presenta la distribución de los creditos aprobados según si el solicitante cuenta con historial crediticio, encontramos que para los solicitantes sin historial es mayor la probabilidad de que el credito sea denegado y en el caso de los solicitante con historial la probabilidad de tener un credito aprobado es mucho mayor.

![download](https://user-images.githubusercontent.com/106851565/171975339-a632097a-50f9-4d2a-8a47-83a0018b1be8.png)

La ultima grafica presenta la distribución de los creditos aprobados con relación a la eduación del solicitante, encontramos que es mayor la solicitud de creditos por parte de graduados y que la distribución de creditos aprobados es mayor para los solicitantes graduados.

![download](https://user-images.githubusercontent.com/106851565/171975537-49bff492-34ac-47d9-a97e-75440c2c60b8.png)

Para terminar con la limpieza de los datos, pasamos a valores numericos los valores categoricos.

## Metodo de evaluación y normalización

Se escogió un conjunto de validación del 10%, utilizando cross-validation con 5 pliegues y para la normalización implementamos un StandardScaler, ajustado por medio del conjunto de entrenamiento.

## Representación y reducción dimensional

