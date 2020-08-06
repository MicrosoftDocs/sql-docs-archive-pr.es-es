---
title: Ejemplos de consultas de modelos de regresión logística | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- content queries [DMX]
ms.assetid: 7c8e13a3-5c67-46c2-abfa-4881e6ef9c62
author: minewiskan
ms.author: owend
ms.openlocfilehash: d432d38794e65e8b8bea69608479e330649ee395
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662369"
---
# <a name="logistic-regression-model-query-examples"></a>Ejemplos de consultas de modelos de regresión logística
  Cuando se crea una consulta en un modelo de minería de datos, puede tratarse de una consulta de contenido, que proporciona detalles de los patrones detectados durante el análisis, o de una consulta de predicción, que utiliza los patrones del modelo para realizar predicciones con los nuevos datos.  
  
 En esta sección se explica cómo crear consultas para los modelos que se basan en el algoritmo de regresión logística de Microsoft.  
  
 **Consultas de contenido**  
  
 [Recuperar parámetros del modelo utilizando el conjunto de filas de esquema de minería de datos](#bkmk_Query1)  
  
 [Buscar información adicional sobre el modelo utilizando DMX](#bkmk_Query2)  
  
 **Consultas de predicción**  
  
 [Realizar predicciones para un valor continuo](#bkmk_Query3)  
  
 [Realizar predicciones para un valor discreto](#bkmk_Query4)  
  
##  <a name="getting-information-about-the-logistic-regression-model"></a><a name="bkmk_top"></a>Obtención de información sobre el modelo de regresión logística  
 Los modelos de regresión logística se crean utilizando el algoritmo de red neuronal de Microsoft con un conjunto especial de parámetros; por consiguiente, contienen parte de la misma información que los modelos de redes neuronales, pero son menos complejos. Para entender la estructura del contenido del modelo, así como qué tipos de nodo almacenan qué clase de información, vea [Contenido del modelo de minería de datos para los modelos de regresión logística &#40;Analysis Services - Minería de datos&#41;](mining-model-content-for-logistic-regression-models.md).  
  
 Para continuar con los escenarios de la consulta, puede crear un modelo de regresión logística como se describe en la siguiente sección del tutorial intermedio de minería de datos: [Lección 5: Generar modelos de red neuronal y de regresión logística &#40;Tutorial intermedio de minería de datos&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).  
  
 También puede usar la estructura de minería de datos, correo dirigido, desde el [Tutorial básico de minería de datos](../../tutorials/basic-data-mining-tutorial.md).  
  
```  
ALTER MINING STRUCTURE [Targeted Mailing]  
ADD MINING MODEL [TM_Logistic Regression]  
([Customer Key],  
[Age],  
[Bike Buyer] PREDICT,  
[Yearly Income] PREDICT,  
[Commute Distance],  
[English Education],  
Gender,  
[House Owner Flag],  
[Marital Status],  
[Number Cars Owned],  
[Number Children At Home],  
[Region],  
[Total Children]  
)  
USING Microsoft_Logistic_Regression  
```  
  
###  <a name="sample-query-1-retrieving-model-parameters-by-using-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a>Consulta de ejemplo 1: recuperar parámetros del modelo utilizando el conjunto de filas de esquema de minería de datos  
 Al consultar el conjunto de filas de esquema de minería de datos, se pueden encontrar metadatos sobre el modelo, como cuándo se creó, cuándo se procesó por última vez, el nombre de la estructura de minería de datos en que se basa el modelo, y el nombre de la columna que se usa como atributo de predicción. El ejemplo siguiente devuelve los parámetros que se utilizaron cuando se creó por primera vez el modelo, junto con el nombre y el tipo del modelo, y la fecha en que se creó.  
  
```  
SELECT MODEL_NAME, SERVICE_NAME, DATE_CREATED, MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center_LR'  
```  
  
 Resultados del ejemplo:  
  
|MODEL_NAME|SERVICE_NAME|DATE_CREATED|MINING_PARAMETERS|  
|-----------------|-------------------|-------------------|------------------------|  
|Call Center_LR|Microsoft_Logistic_Regression|04/07/2009 20:38:33|HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000|  
  
###  <a name="sample-query-2-finding-additional-detail-about-the-model-by-using-dmx"></a><a name="bkmk_Query2"></a>Consulta de ejemplo 2: Buscar detalles adicionales sobre el modelo mediante DMX  
 La consulta siguiente devuelve información básica sobre el modelo de regresión logística. Un modelo de regresión logística es similar a un modelo de red neuronal en muchos sentidos, por ejemplo en la presencia de un nodo estadístico marginal (NODE_TYPE = 24) que describe los valores que se usan como entradas. En esta consulta de ejemplo se utiliza el modelo de distribución de correo directo y se obtienen los valores de todas las entradas recuperándolos de la tabla anidada NODE_DISTRIBUTION.  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM [TM_Logistic Regression].CONTENT   
```  
  
 Resultados parciales:  
  
|T.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Age|Missing|0|0|0|1|  
|Age|45.43491192|17484|1|126.9544114|3|  
|Bike Buyer|Missing|0|0|0|1|  
|Bike Buyer|0|8869|0.507263784|0|4|  
|Bike Buyer|1|8615|0.492736216|0|4|  
|Commute Distance|Missing|0|0|0|1|  
|Commute Distance|8-15 km|3033|0.173472889|0|4|  
  
 La consulta real devuelve muchas más filas; sin embargo, este ejemplo muestra el tipo de información que se proporciona sobre las entradas. En la tabla se enumera cada valor posible para las entradas discretas. Para entradas de valor continuo como Edad, no se puede realizar una lista completa, de modo que la entrada son datos discretos como media. Para más información sobre cómo usar la información en el nodo de estadísticas marginales, vea [Contenido del modelo de minería de datos para los modelos de regresión logística &#40;Analysis Services - Minería de datos&#41;](mining-model-content-for-logistic-regression-models.md).  
  
> [!NOTE]  
>  Los resultados se muestran sin una estructura jerárquica para facilitar la visualización, pero puede devolver la tabla anidada en una sola columna si su proveedor admite conjuntos de filas jerárquicas.  
  
## <a name="prediction-queries-on-a-logistic-regression-model"></a>Consultas de predicción en un modelo de regresión logística  
 Puede usar la función [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) con cada tipo de modelo de minería de datos para proporcionar nuevos datos al modelo y realizar predicciones basadas en los nuevos valores. También puede utilizar funciones para devolver información adicional sobre la predicción, como la probabilidad de que una predicción sea correcta. En esta sección se proporcionan algunos ejemplos de consultas de predicción en un modelo de regresión logística.  
  
###  <a name="sample-query-3-making-predictions-for-a-continuous-value"></a><a name="bkmk_Query3"></a>Consulta de ejemplo 3: realizar predicciones para un valor continuo  
 Dado que la regresión logística admite el uso de atributos continuos para entrada y predicción, resulta fácil crear modelos que pongan en correlación varios factores de los datos. Puede utilizar las consultas de predicción para explorar la relación entre estos factores.  
  
 La siguiente consulta de ejemplo se basa en el modelo de centro de llamadas del tutorial intermedio. En ella se crea una consulta singleton que predice el nivel del servicio del turno de la mañana del viernes. La función [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) devuelve una tabla anidada que proporciona las estadísticas pertinentes para conocer la validez del valor predicho.  
  
```  
SELECT  
  Predict([Call Center_LR].[Service Grade]) as Predicted ServiceGrade,  
  PredictHistogram([Call Center_LR].[Service Grade]) as [Results],  
FROM  
  [Call Center_LR]  
NATURAL PREDICTION JOIN  
(SELECT 'Friday' AS [Day Of Week],  
  'AM' AS [Shift]) AS t  
```  
  
 Resultados del ejemplo:  
  
 **Grado de servicio predicho**: 0.102601830123659  
  
 **Resultados**  
  
|Service Grade|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|$VARIANCE|$STDEV|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|0.102601830123659|83.0232558139535|0.988372093023256|0|0.00120552660600087|0.034720694203902|  
||0.976744186046512|0.0116279069767442|0.0116279069767442|0|0|  
  
 Para más información sobre los valores de probabilidad, soporte y desviación estándar de la tabla anidada NODE_DISTRIBUTION, vea [Contenido del modelo de minería de datos para los modelos de regresión logística &#40;Analysis Services - Minería de datos&#41;](mining-model-content-for-logistic-regression-models.md).  
  
###  <a name="sample-query-4-making-predictions-for-a-discrete-value"></a><a name="bkmk_Query4"></a>Consulta de ejemplo 4: realizar predicciones para un valor discreto  
 La regresión logística se suele usar en los escenarios en los que se desea analizar los factores que contribuyen a un resultado binario. Aunque el modelo usado en el tutorial predice un valor continuo, **ServiceGrade**, en la vida real es posible que quiera configurar el modelo para predecir si el nivel de servicio cumplió un valor esperado de datos discretos. También podría generar las predicciones mediante un valor continuo pero, posteriormente, agrupar los resultados en **Bueno**, **Aceptable**o **Malo**.  
  
 En el siguiente ejemplo se muestra cómo cambiar la manera en que se agrupa el atributo predecible. Para hacerlo, debe crear una copia de la estructura de minería de datos y, a continuación, cambiar el método de discretization de la columna de destino para que los valores sean agrupados en lugar de continuos.  
  
 En el siguiente procedimiento se describe cómo cambiar la agrupación de los valores de nivel de servicio de los datos del centro de llamadas.  
  
##### <a name="to-create-a-discretized-version-of-the-call-center-mining-structure-and-models"></a>Para crear una versión de datos discretos de la estructura de minería de datos y los modelos del centro de llamadas  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en el Explorador de soluciones, expanda **Estructuras de minería de datos**.  
  
2.  Haga clic con el botón derecho en Call Center.dmm y seleccione **Copiar**.  
  
3.  Haga clic con el botón secundario en **Estructuras de minería de datos** y seleccione **Pegar**. Se agrega una nueva estructura de minería de datos, con el nombre Call Center 1.  
  
4.  Haga clic con el botón derecho en la nueva estructura de minería de datos y seleccione **Cambiar nombre**. Escriba el nuevo nombre, **Centro de llamadas de datos discretos**.  
  
5.  Haga doble clic en la nueva estructura de minería de datos para abrirla en el diseñador. Observe que también se han copiado todos los modelos de minería de datos y todos tienen la extensión 1. Deje los nombres como están.  
  
6.  En la pestaña **Estructura de minería de datos** , haga clic con el botón derecho en la columna de nivel de servicio y seleccione **Propiedades**.  
  
7.  Cambie la `Content` propiedad de **continuo** a **discreto**. Cambie la `DiscretizationMethod` propiedad a **clusters**. En Discretization BucketCount, escriba **3**.  
  
    > [!NOTE]  
    >  Estos parámetros se utilizan simplemente para ilustrar el proceso y no generan necesariamente un modelo válido.  
  
8.  En el menú **Modelo de minería de datos** , seleccione **Procesar estructura de minería de datos y todos los modelos**.  
  
 La siguiente consulta del ejemplo está basada en este modelo de datos discretos y predice el nivel de servicio del día de la semana especificado, junto con las probabilidades de cada resultado previsto.  
  
```  
SELECT  
  (PredictHistogram([Call Center_LR 1].[Service Grade])) as [Predictions]  
FROM  
  [Call Center_LR 1]  
NATURAL PREDICTION JOIN  
(SELECT 'Saturday' AS [Day Of Week]) AS t    
```  
  
 Resultados esperados:  
  
 **Predicciones**  
  
|Service Grade|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|$VARIANCE|$STDEV|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|0.10872718383125|35.7246504770641|0.425293458060287|0.0170168360030293|0|0|  
|0.05855769230625|31.7098880800703|0.377498667619885|0.020882020060454|0|0|  
|0.170169491525|15.6109159883202|0.185844237956192|0.0661386571386049|0|0|  
||0.954545454545455|0.0113636363636364|0.0113636363636364|0|0|  
  
 Tenga en cuenta que los resultados previstos se han agrupado en tres categorías como se ha especificado. Sin embargo, estas agrupaciones están basadas en la agrupación en clústeres de valores reales en los datos, no en valores arbitrarios que se podrían establecer como objetivos empresariales.  
  
## <a name="list-of-prediction-functions"></a>Lista de funciones de predicción  
 Todos los algoritmos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] son compatibles con un conjunto común de funciones. No obstante, el algoritmo de regresión logística de [!INCLUDE[msCoName](../../includes/msconame-md.md)] admite las funciones adicionales que se enumeran en la siguiente tabla.  
  
|||  
|-|-|  
|función de predicción|Uso|  
|[IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx)|Determina si un nodo es un elemento secundario de otro nodo del modelo.|  
|[PredictAdjustedProbability &#40;DMX&#41;](/sql/dmx/predictadjustedprobability-dmx)|Devuelve la probabilidad ajustada de un estado especificado.|  
|[PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)|Devuelve un valor o un conjunto de valores predichos para una columna especificada.|  
|[PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx)|Devuelve la probabilidad de un estado especificado.|  
|[PredictStdev &#40;DMX&#41;](/sql/dmx/predictstdev-dmx)|Devuelve la desviación estándar del valor predicho.|  
|[PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx)|Devuelve el valor de soporte de un estado especificado.|  
|[PredictVariance &#40;DMX&#41;](/sql/dmx/predictvariance-dmx)|Devuelve la varianza de una columna especificada.|  
  
 Para consultar una lista de las funciones comunes a todos los algoritmos de [!INCLUDE[msCoName](../../includes/msconame-md.md)], vea [Funciones de predicción generales &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx). Para más información sobre la sintaxis de funciones específicas, vea [Referencia de funciones de Extensiones de minería de datos &#40;DMX&#41;](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
> [!NOTE]  
>  En los modelos de regresión logística y red neuronal, la función [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) devuelve un valor único que representa el tamaño del conjunto de entrenamiento para todo el modelo.  
  
## <a name="see-also"></a>Consulte también  
 [Consultas de minería de datos](data-mining-queries.md)   
 [Algoritmo de regresión logística de Microsoft](microsoft-logistic-regression-algorithm.md)   
 [Referencia técnica del algoritmo de regresión logística de Microsoft](microsoft-logistic-regression-algorithm-technical-reference.md)   
 [Contenido del modelo de minería de datos para los modelos de regresión logística &#40;&#41;de minería de datos Analysis Services](mining-model-content-for-logistic-regression-models.md)   
 [Lección 5: Generar modelos de red neuronal y de regresión logística &#40;Tutorial intermedio de minería de datos&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
