# Loan prediction using machine learning
Loan approval prediction using different supervised learning algorithms

Author:

Juan Sebastián Castrillón

## Project Introduction

Dataset: https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset

This dataset contains 642 samples, where each sample represent a person who has applied for a loan, each person have an ID assigned and there are 11 features inlcuding gender, married, number of dependents, education, income, coapplicant income, loan amount, loan term, credit history and property area. Finally there's a label column called Loan_Status that indicates if the loan was approved or not. There's also included a test dataset which has no labels with the purpose of predicting those missing labels and determine the accuracy of the predictions in this webpage: https://datahack.analyticsvidhya.com/contest/practice-problem-loan-prediction-iii/#LeaderBoard.

Este conjunto de datos cuenta con 642 muestras que representan personas que han solicitado un crédito, cada usuario tiene asignado un ID, se presentan 11 caracteristicas dentro de este dataset, entre los que se encuentra; educación, estado civil, nivel de educación, si es trabajador independiente, ingresos del aplicante, ingresos del coaplicante, la cantidad de dinero solicitada, si presenta historial crediticio y el tipo de propiedad en la que reside. Como etiquetas se tiene si el crédito fue aprobado o no. El dataset incluye un conjunto de prueba el cual no cuenta con etiquetas, con el fin de generar las predicciones y validarlas en la siguiente pagina: https://datahack.analyticsvidhya.com/contest/practice-problem-loan-prediction-iii/#LeaderBoard.

## Development

### 1. Identifying the problem

After checking the dataset is clear that this is a binary classification problem, because there's labels for each sample and these labels only have two values(Y/N).

Revisando el conjunto de datos determinamos que es un problema de clasificación binaria, debido a que se tienen etiquetas para las muestras y estas toman unicamente dos valores.

### 2. Data Cleaning

The data cleaning process started with the identification of how many NaN values were present in all of the columns, obtaining these results.

Incialmente se importaron los datos, luego de esto se revisaron las columnas que presentan valores nulos y la cantidad de estos, obteniendo los siguientes resultados.

![image](https://user-images.githubusercontent.com/106851565/171973897-87b40b09-c1ee-4162-be59-6c06c6c98f4d.png)

Next it was defined the strategy for filling the NaN values, for LoanAmount it was used the mean of all of the present values and for all of the other features we use the mode. Once all of the NaN values were eliminated/replaced.

Posteriormente se definio las estrategias para rellenar los valores nulos, para LoanAmount se utilizo la media del resto de valores y para las demás características se utilizó la moda. Una vez eliminados todos los valores NaN realizamos un análisis de las diferentes caracterísitcas, iniciando con un histograma de todas las características numéricas.

## 3. EDA(Exploratory Data Analysis)

A series of histograms were created for all the numerical features, it was found that most of the sample have credit history, most of the loans are requested for a term of a 360 months and the income for a large portion of the applicants is less than 10000.

Luego de analizar los histogramas se encontró que la mayoría de las muestras cuentan con historial crediticio, la mayor parte de los créditos solicitados son a un termino de 360 meses y que el ingreso de gran parte de los solicitantes es menor a 10000. 

![image](https://user-images.githubusercontent.com/106851565/171975189-a84740c0-b69d-4f77-bb08-2414ed3ea478.png)

Multiple bar charts were created to found the distribution of the approval of loans in relation to multiple categorical features. The first graph created was the distribution of loans by the gender of the applicant, it was found that most of the applicants are men and that the distribution of approved loans its the same regardless of the gender.

Posteriormente se generaron graficas para observar la distribución de los créditos aprobados en relación a diferentes características categóricas. De la siguiente grafica se determina que la mayoria de los solicitantes son hombres y que la distribución de créditos aprobados es similar sin importar el genero.
![download](https://user-images.githubusercontent.com/106851565/171975345-cbbda6d6-66e2-4308-8005-83382d8d56af.png)

The following grapgh presents the distribution of loan request by credit history, from this graph its clear thar most of tha applicants without credit history have a lower chance of getting its loan approved.

La siguiente gráfica presenta la distribución de los créditos aprobados según si el solicitante cuenta con historial crediticio, encontramos que para los solicitantes sin historial es mayor la probabilidad de que el crédito sea denegado y en el caso de los solicitantes con historial la probabilidad de tener un crédito aprobado es mucho mayor.

![download](https://user-images.githubusercontent.com/106851565/171975339-a632097a-50f9-4d2a-8a47-83a0018b1be8.png)

This last graph displays the distribution of loan requests by the education level of the applicant's education level, it was found that most of the aplicants are graduates and the proportion of approved credits is higher compared to non-graduates.

La ultima grafica presenta la distribución de los créditos aprobados con relación a la eduación del solicitante, se encontro que es mayor la solicitud de créditos por parte de graduados y que la distribución de créditos aprobados es mayor para los solicitantes graduados.

![download](https://user-images.githubusercontent.com/106851565/171975537-49bff492-34ac-47d9-a97e-75440c2c60b8.png)

The last step of the data cleaning process was to transform the categorical data to numerical data, for the features with only two categories it was implemented a label enconding and for features with 3 or more categaries it was used a One-Hot enconding. 

Para terminar con la limpieza de los datos, se convirtieron a valores numéricos los valores categóricos, para esto se realizo label enconding para los valores que presentaban dos categorias y para el caso de tener tres o más categorias se utlizó One Hot encoding.

## 4. Validation method and standardization

A split of the train dataset was made creating a train set with 90% of the data that was used to train the different algorithms, the remaining 10% was used to create a validation set, additionaly the classifiers were trained using 5-fold Cross-Validation, finally all of the data was standardized using the StandardScaler utility class from the library sklearn.

Se escogió un conjunto de validación del 10%, además para el entrenamiento de los clasificadores se utilizo cross-validation con 5 pliegues y para la normalización se implementó un StandardScaler, ajustado por medio del conjunto de entrenamiento.

## 5. Principal Component Analysis(PCA)

After executing a PCA to the test set it was obtained these variance for the components.

Se realizó una descomposición en componentes principales del conjunto de entrenamiento, obteniendo la siguiente varianza explicada de los componentes.

![download](https://user-images.githubusercontent.com/106851565/171976705-ac35e306-34d0-4b9b-8b96-bfb836f99467.png)
![image](https://user-images.githubusercontent.com/106851565/171976846-8b9d8c5f-7a07-4ce0-8306-57d7623774c5.png)

It was decided not to apply dimmensional reduction because it wasn't possible to have a retention of the variance higher than 98%, but it was applied a linear transformation to simplify the represantion of the data. 

Se decidió no realizar reducción dimensional debido a que no se retiene más de un 98% de la varianza, pero si se realizó la transformación para simplificar la representación de los datos. 

## 6. Classifiers and evaluation metrics

The implementation of 4 different classifiers was carried out, these being; logistic regression, SVM, Random forest and KNN. MCC and F1 were chosen as evaluation metrics. The function GridSearchCV from the library sklearn was used to find the best set of parameters for each classifier, after training all the classifiers the ones with the best MCC and F1 score were the logistic regression and random forest.

Se realizo la implementación de 4 clasificadores diferentes, siendo estos; regresión logistica, SVM, Random forest y KNN. Como metricas de evaluación se escogió MCC y F1, finalmente se escogera el clasificador que obtenga las mayores calificaciones.

Para la iteración de los parametros se utilizó la función GridSearchCV, finalmente se obtuvo que los mejores clasificadores fueron la regresión logistica y random forest, ya que obtuvieron los mismos resultados de MCC y F1.

![image](https://user-images.githubusercontent.com/106851565/171978975-c699ca05-5a5e-45b5-b61e-69690c2e8355.png)

![image](https://user-images.githubusercontent.com/106851565/171979154-1b3d2c4e-0a6b-476d-8b8b-161b018ca2fb.png)

## 7. Validation

The chosen classifiers were trained using all of the train set, then a test were performed with the validation set, and the following results were obtained for both classifiers.

Se reentrenaron los clasificadores escogidos con todo el conjunto de entrenamiento, luego se realizaron pruebas con el conjunto de validación obteniendo los siguientes resultados para ambos clasificadores.

![image](https://user-images.githubusercontent.com/106851565/171980534-9c2dea96-3fee-4749-b929-9e6a17da96da.png)

## Results

Finally, the prediction.csv file was uploaded to the contest page, obtaining an accuracy of 76.38%.

Finalmente se cargó el archivo prediction.csv a la pagina del concurso obteniendo un accuracy de 76.38%.
![image](https://user-images.githubusercontent.com/106851565/171984333-b7feb55e-5fa5-40ce-85aa-a98f3b0a00ae.png)

## Future Improvements

The precision of the predictions could improve using Ensemble learning methods like Gradient Boosting, ADABoosting or xgboosting.

La precisión de las predicciones podria mejorar utilizando tecnicas más avanzandas de Ensemble Learnning como Gradient Boosting, ADABossting o xgBoosting
