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


