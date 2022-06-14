# Loan prediction using machine learning
Predicción de la aprobación de un credito utilizando diferentes métodos de clsificación supervisada. 

Integrantes:

Juan Sebastián Castrillón

Carlos Humberto Diaz

## Introducción del proyecto

Se utilizó el siguiente dataset: https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset

Este conjunto de datos cuenta con 642 muestras que representan personas que han solicitado un credito, cada usuario tiene asignado un ID, se presentan 11 caracteristicas dentro de este dataset, entre los que se encuentra; educación, estado civil, nivel de educación, si es trabajador independiente, ingresos del aplicante, ingresos del coaplicante, la cantidad de dinero solicitada, si presenta histroial crediticio y el tipo de propiedad en la que reside. Como etiquetas se tiene si el credito fue aprobado o no. El dataset incluye un conjunto de prueba el cual no cuenta con etiquetas, con el fin de generar las predicciones y validarlas en la siguiente pagina: https://datahack.analyticsvidhya.com/contest/practice-problem-loan-prediction-iii/#LeaderBoard.

## Desarrollo

### 1. Identificación del problema

Revisando el conjunto de datos determinamos que es un problema de clasificación binaria, debido a que se tienen etiquetas para las muestras y estas toman unicamente dos valores.

### 2. Análisis y limpieza de los datos

Incialmente se importaron los datos, luego de esto se revisaron las columnas que presentan valores nulos y la cantidad de estos, obteniendo los siguientes resultados.

![image](https://user-images.githubusercontent.com/106851565/171973897-87b40b09-c1ee-4162-be59-6c06c6c98f4d.png)

Posteriormente definimos las estrategias para rellenar los valores nulos, para LoanAmount se utilizo la media del resto de valores y para las demás características se utilizó la moda. Una vez eliminados todos los valores NaN realizamos un análisis de las diferentes caracterísitcas, iniciando con un histograma de todas las características numéricas.

![image](https://user-images.githubusercontent.com/106851565/171975189-a84740c0-b69d-4f77-bb08-2414ed3ea478.png)

Encontramos que la mayoría de las muestras cuentan con historial crediticio, la mayor parte de los creditos solicitados son a un termino de 360 y que el ingreso de gran parte de los solicitantes es menor a 10000. Posteriormente hallamos la distribución de los créditos aprobados en relación a diferentes características categóricas.

De la siguiente grafica determinamos que la mayoria de los solicitantes son hombres y que la distribución de creditos aprobados es similar sin importar el genero.
![download](https://user-images.githubusercontent.com/106851565/171975345-cbbda6d6-66e2-4308-8005-83382d8d56af.png)

La siguiente gráfica presenta la distribución de los créditos aprobados según si el solicitante cuenta con historial crediticio, encontramos que para los solicitantes sin historial es mayor la probabilidad de que el crédito sea denegado y en el caso de los solicitantes con historial la probabilidad de tener un crédito aprobado es mucho mayor.

![download](https://user-images.githubusercontent.com/106851565/171975339-a632097a-50f9-4d2a-8a47-83a0018b1be8.png)

La ultima grafica presenta la distribución de los creditos aprobados con relación a la eduación del solicitante, encontramos que es mayor la solicitud de creditos por parte de graduados y que la distribución de creditos aprobados es mayor para los solicitantes graduados.

![download](https://user-images.githubusercontent.com/106851565/171975537-49bff492-34ac-47d9-a97e-75440c2c60b8.png)

Para terminar con la limpieza de los datos, pasamos a valores numéricos los valores categóricos.

## 3. Metodo de evaluación y normalización

Se escogió un conjunto de validación del 10%, decidimos entrenar los clasificadores utilizando cross-validation con 5 pliegues y para la normalización implementamos un StandardScaler, ajustado por medio del conjunto de entrenamiento.

## 4. Representación y reducción dimensional
Realizamos una descomposición en componentes principales del conjunto de entrenamiento, obteniendo la siguiente varianza explicada de los componentes.

![download](https://user-images.githubusercontent.com/106851565/171976705-ac35e306-34d0-4b9b-8b96-bfb836f99467.png)
![image](https://user-images.githubusercontent.com/106851565/171976846-8b9d8c5f-7a07-4ce0-8306-57d7623774c5.png)

Decidimos no realizar reducción dimensional debido a que no se retiene más de un 98% de la varianza, pero si se realizó la transformación para simplificar la representación de los datos. 

## 5. Implementación de clasificadores y selección de metricas de evaluación y optimización

Realizamos la implementación de 4 clasificadores diferentes, siendo estos; regresión logistica, SVM, Random forest y KNN. Como metricas de evaluación utilizamos MCC y F1, finalmente escogimos el clasificador que tuviera las mayores calificaciones.

Para la iteración de los parametros utilizamos la función GridSearchCV, finalmente obtuvimos que los mejores clasificadores fueron la regresión logistica y random forest, ya que obtuvieron los mismos resultados de MCC y F1.

![image](https://user-images.githubusercontent.com/106851565/171978975-c699ca05-5a5e-45b5-b61e-69690c2e8355.png)

![image](https://user-images.githubusercontent.com/106851565/171979154-1b3d2c4e-0a6b-476d-8b8b-161b018ca2fb.png)

## 6. Validación

Finalmente re entranando los clasificadores con todo el conjunto de entranamiento y realizando las pruebas con el conjunto de validación, obtuvimos los siguientes resultados para ambos clasificadores.

![image](https://user-images.githubusercontent.com/106851565/171980534-9c2dea96-3fee-4749-b929-9e6a17da96da.png)

## Resultados
Finalmente subimos el archivo prediction.csv a la pagina del concurso obteniendo un accuracy de 76.38%
![image](https://user-images.githubusercontent.com/106851565/171984333-b7feb55e-5fa5-40ce-85aa-a98f3b0a00ae.png)

