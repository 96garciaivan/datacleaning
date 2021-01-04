

Este trabajo se ha realizado en el contexto de la asignatura Tipología y Ciclo de Vida del Dato, correspondiente al máster en ciencia de datos de la UOC.

Este conjunto de datos contiene datos de uso de camiones de gran tonelaje de Scania. El caso de estudio se centra en el Sistema de Aire a Presión (APS, del inglés Air Pressure System), sistema responsable de proveer de aire comprimido a varias de las funciones del camión, como el freno o embrague. Los casos con clase positiva son fallos de componentes relacionados con el sistema APS.

Por el contrario, los caos con clase negativa corresponden a fallos de componentes no relacionados con el APS. El conjunto de datos presenta casos de ambos tipos, si bien es cierto que los casos negativos son mucho más frecuentes.

El objetivo del conjunto de datos es predecir qué tipo de fallos tienen su origen en el sistema APS y cuáles son debidos a otras causas. Este hecho tiene repercusión en las revisiones o reparaciones a realizar sobre el camión. De hecho, la bondad de la predicción se medirá en términos de coste. El coste total se evaluará como la suma de fallos de tipo 1 por el coste asociado (Coste1) más la suma de fallos de tipo 2 por el coste asociado (Coste2).Un error de tipo I se origina cuando el modelo predice positivo cuando en realidad el fallo no tiene origen en un componente el APS.

El coste 1 asociado a este hecho es debido a la revisión innecesaria del APS que debe ser realizada en el taller, que se ha valorado en 10 unidades. Por el contrario, el error de tipo II podría tener como resultado permitir el tráfico del camión con defecto en un componente APS, que puede causar una averís. El coste 2 asociado a este tipo de fallo es superior y se ha valorado en 500 unidades. El mejor modelo de predicción será aquel que minimice el coste total.

Este conjunto ha sido proporcionado por la empresa Scania y están disponibles en el repositorio UCI Machine Learning Repository (https://archive.ics.uci.edu/ml/datasets/APS+Failure+at+Scania+Trucks). Los datos proporcionados son un conjunto de datos de entrenamiento y otro de validación.

Las variables del dataset estan anonimizadas, debido a temas de privacidad de la empresa, esto hace que no se pueda saber a que corresponde cada variable.

Los casos positivos y negativos están desequilibrados. Deberá analizarse qué implica este hecho en el análisis de los datos. El resultado debe ayudar en la toma de decisiones desde una perspectiva de coste.

El trabajo ha comenzado con la limpieza de datos y tratamiento de perdidos y ceros, en la cual se han probado diferentes tipos de imputación y se ha echo un tratamiento por separado para los atributos binarizados. También se ha realizado una reducción de dimensionalidad mediante PCA, y aunque esto pueda PCA hacer que se pierda un poco el sentido de los atributos co de cara a sacar conclusiones sobre qué variables son las más influyentes, hay que tener en cuenta que las variables viene anonimizadas y no se sabe a que corresponde cada una.

En la fase de análisis, se han utilizado el árbol de decisión c5.0, regresión logística y Naive Bayes, en diferentes escenarios. El mejor resultado se ha obtenido con la regresión logística, utilizando la técnica SMOTE para balancear los datos. Cabe destacar cómo se han reducido los falsos negativos al balancear los datos con SMOTE, ya que el problema de los algorimtos de clasificación es que tienden a favorecer la clase mayoritaria (si no se utiliza otra técnica para balancear casos). En el caso de Naive Bayes se ha utilizado el paquete ROSE para el balanceo de datos.

El mejor coste total del modelo de predicción ha resultado ser con el modelo de regresión logística con SMOTE, sobre datos imputados con la mediana, obteniéndose un coste total de 16980.

Por último, el principal reto de este conjunto de datos de SCANIA ha sido el gran tamaño del mismo (tanto número de filas como de columnas), seguido del desequilibrio entre las clases positivo y negativa. Para trabajar con grandes volúmenes de datos, ha sido importante utilizar técnicas exploratorias y técnicas de análisis eficientes computacionalmente.
