---
title: Consultas de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- queries [DMX], creating
- prediction queries [DMX]
- Prediction Query Builder
- mining models [Analysis Services], querying
ms.assetid: 802806a6-69bb-4c3c-b9aa-d1a1ddfc7fc2
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab6725ddd86d18132de9c408125fa9084161a187
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677317"
---
# <a name="data-mining-queries"></a>Consultas de minería de datos
  Las consultas de minería de datos son útiles para muchos propósitos. Puede:  
  
-   Aplicar el modelo a nuevos datos, para realizar una o varias predicciones. Proporcionar valores de entrada como parámetros o en un lote.  
  
-   Obtener un resumen estadístico de los datos utilizados para entrenar.  
  
-   Extraer patrones y reglas, o generar un perfil del caso típico que representa un patrón del modelo.  
  
-   Extraer fórmulas de regresión y otros cálculos que expliquen los patrones.  
  
-   Obtener los casos que se ajusten a un patrón determinado.  
  
-   Recuperar detalles sobre casos individuales usados en el modelo, incluidos los datos no usados en el análisis.  
  
-   Volver a entrenar un modelo agregando nuevos datos, o realizar predicciones cruzadas.  
  
 Esta sección proporciona información general sobre lo que debe saber para empezar a trabajar con consultas de minería de datos. Describe los tipos de consultas que puede crear con los objetos de minería de datos, presenta las herramientas y lenguajes de consulta y proporciona vínculos a ejemplos de consultas que puede crear con modelos que fueron compilados utilizando los algoritmos proporcionados en la minería de datos de SQL Server.  
  
 [Descripción de las consultas de minería de datos](#bkmk_Understand)  
  
 [Herramientas e interfaces de consulta](#bkmk_Interfaces)  
  
 [Consultas para los diferentes tipos de modelos](#bkmk_ModelTypes)  
  
 [Requisitos](#bkmk_Reqs)  
  
##  <a name="understanding-data-mining-queries"></a><a name="bkmk_Understand"></a>Descripción de las consultas de minería de datos  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] admite los siguientes tipos de consultas:  
  
-   [Consultas de predicción &#40;minería de datos&#41;](prediction-queries-data-mining.md)  
  
     Consultas que realizan deducciones basadas en los patrones del modelo y partiendo de los datos de entrada.  
  
-   [Consultas de contenido &#40;minería de datos&#41;](content-queries-data-mining.md)  
  
     Consultas que devuelven metadatos, estadísticas y otra información sobre el propio modelo.  
  
-   [Consultas de obtención de detalles &#40;minería de datos&#41;](drillthrough-queries-data-mining.md)  
  
     Consultas que pueden recuperar los datos de casos subyacentes del modelo o incluso los datos de la estructura que no se utilizó en el modelo.  
  
-   [Consultas de definición de datos &#40;minería de datos&#41;](data-definition-queries-data-mining.md)  
  
     Consultas que no devuelven información sobre el modelo, sino que se usan para compilar modelos y estructuras o para actualizar los datos de un modelo o estructura.  
  
 Antes de crear consultas, recomendamos que se familiarice con las diferencias que existen entre los modelos creados con cada uno de los algoritmos de minería de datos proporcionados por SQL Server.  
  
-   Examine y explore cada tipo de modelo utilizando los visores de minería de datos personalizados que se proporcionan para cada tipo de algoritmo. Para más información, vea [Tareas y procedimientos del Visor de modelos de minería de datos](mining-model-viewer-tasks-and-how-tos.md).  
  
-   Revise el contenido del modelo para cada tipo modelo, utilizando el **Visor de árbol de contenido genérico de Microsoft**. Para interpretar esta información, vea [Contenido del modelo de minería de datos &#40;Analysis Services - Minería de datos&#41;](mining-model-content-analysis-services-data-mining.md).  
  
##  <a name="query-tools-and-interfaces"></a><a name="bkmk_Interfaces"></a>Herramientas e interfaces de consulta  
 Puede compilar consultas de minería de datos de forma interactiva mediante una de las herramientas de consulta proporcionadas por SQL Server. El Generador de consultas de predicción gráfico está disponible en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] y en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si no ha utilizado el Generador de consultas de predicción antes, recomendamos seguir los pasos de [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md) para familiarizarse con la interfaz. Para una introducción rápida a los pasos, vea [Crear una consulta de predicción con el Generador de consultas de predicción](create-a-prediction-query-using-the-prediction-query-builder.md).  
  
 El Generador de consultas de predicción es útil para iniciar consultas que personalizará después. Puede agregar orígenes de datos con facilidad y asignarlos a columnas y, a continuación, pasar a la vista DMX y personalizar la consulta agregando una cláusula WHERE u otras funciones.  
  
 Una vez familiarizado con los modelos de minería de datos y con el modo de compilar consultas, también puede escribir consultas directamente utilizando Extensiones de minería de datos (DMX). DMX es un lenguaje de consultas que es similar a Transact-SQL y que puede utilizar en muchos clientes diferentes. DMX es la herramienta adecuada para crear predicciones personalizadas y consultas complejas. Para una introducción a DMX, vea [Crear y consultar modelos de minería de datos con DMX: tutoriales &#40;Analysis Services - minería de datos&#41;](../../tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] y [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]disponen de editores DMX. También puede utilizar el Generador de consultas de predicción para iniciar sus consultas y, a continuación, cambiar la vista al editor de texto y copiar la instrucción DMX en otro cliente. Para obtener más información, vea [interfaces de consulta de minería de datos](data-mining-query-tools.md).  
  
 Puede crear instrucciones DMX mediante programación y enviarlas de su cliente al servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante AMO o XMLA. Sin embargo, DMX es el lenguaje que debe utilizar para crear consultas en un modelo de minería de datos.  
  
 También puede consultar los metadatos, estadísticas y parte del contenido del modelo usando Vistas de administración dinámica (DMV) basadas en los conjuntos de filas de esquema de minería de datos. Con estas DMV resulta fácil recuperar información sobre el modelo mediante instrucciones SELECT; sin embargo, no se pueden crear predicciones. Para más información sobre las DMV admitidas por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vea [Usar vistas de administración dinámica &#40;DMV&#41; para supervisar Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).  
  
 Finalmente, puede crear consultas de minería de datos para utilizarlas en paquetes de Integration Services mediante la [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md)o la [Data Mining Query Transformation](../../integration-services/data-flow/transformations/data-mining-query-transformation.md). La tarea de flujo de control admite varios tipos de consultas DMX, mientras que la transformación de flujo de datos solo admite consultas que trabajan con datos del flujo de datos, lo cual significa que las consultas utilizan la sintaxis de PREDICTION JOIN.  
  
##  <a name="queries-for-different-model-types"></a><a name="bkmk_ModelTypes"></a> Consultas para los diferentes tipos de modelos  
 El algoritmo utilizado al crear el modelo influye notablemente en el tipo de información que se puede recibir de una consulta de minería de datos. La razón de las diferencias es que cada algoritmo procesa los datos de forma diferente y almacena diferentes tipos de modelos. Por ejemplo, algunos algoritmos crean clústeres y otros crean árboles. Por consiguiente, podría tener que utilizar predicción y funciones de consulta especializadas, según el tipo de modelo con el que esté trabajando.  
  
 La siguiente lista proporciona un resumen de las funciones que puede utilizar en las consultas:  
  
-   **Funciones de predicción generales:** La `Predict` función es polimórfica, lo que significa que funciona con todos los tipos de modelo. Esta función detectará automáticamente el tipo de modelo con el que está trabajando y solicitará parámetros adicionales. Para más información, vea [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx).  
  
    > [!WARNING]  
    >  No todos los modelos se utilizan para realizar predicciones. Por ejemplo, puede crear un modelo de agrupación en clústeres que no tenga un atributo de predicción. Sin embargo, aun cuando un modelo no tenga un atributo de predicción, puede crear consultas de predicción que devuelvan otro tipo de información útil sobre el modelo.  
  
-   **Funciones de predicción personalizadas:** cada tipo modelo proporciona un conjunto de funciones de predicción diseñado para trabajar con los modelos creados por ese algoritmo.  
  
     Por ejemplo, la función `Lag` se proporciona para los modelos de serie temporal, para que pueda ver los datos históricos utilizados para el modelo. Para los modelos de agrupación en clústeres, las funciones como `ClusterDistance` tienen más sentido.  
  
     Para obtener más información sobre las funciones que se admiten para cada tipo de modelo, vea los siguientes vínculos:  
  
    |||  
    |-|-|  
    |[Ejemplos de consultas del modelo de asociación](association-model-query-examples.md)|[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md)|  
    |[Ejemplos de consultas de modelos de agrupación en clústeres](clustering-model-query-examples.md)|[Ejemplos de consultas de modelos de red neuronal](neural-network-model-query-examples.md)|  
    |[Ejemplos de consultas de modelos de árboles de decisión](decision-trees-model-query-examples.md)|[Ejemplos de consultas de modelos de clústeres de secuencia](sequence-clustering-model-query-examples.md)|  
    |[Ejemplos de consultas de modelos de regresión lineal](linear-regression-model-query-examples.md)|[Ejemplos de consultas de modelos de serie temporal](time-series-model-query-examples.md)|  
    |[Ejemplos de consultas de modelos de regresión logística](logistic-regression-model-query-examples.md)||  
  
     También puede llamar a funciones VBA o crear sus propias funciones. Para más información, vea [Funciones &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
-   **Estadísticas generales:** hay varias funciones que se pueden utilizar con casi cualquier tipo de modelo, que devuelven un conjunto estándar de estadísticas descriptivas, como la desviación estándar.  
  
     Por ejemplo, la función `PredictHistogram` devuelve una tabla que enumera todos los estados de la columna especificada.  
  
     Para más información, vea [Funciones de predicción generales &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).  
  
-   **Estadísticas personalizadas:** se proporcionan funciones de apoyo adicionales para cada tipo de modelo, para generar estadísticas que sean pertinentes a la tarea analítica concreta.  
  
     Por ejemplo, cuando trabaje con un modelo de agrupación en clústeres, puede utilizar la función `PredictCaseLikelihood` para devolver la puntuación de probabilidad asociada a un determinado caso y clúster. Sin embargo, si creara un modelo de regresión lineal, le interesaría más recuperar el coeficiente y la intersección, lo que puede hacer mediante una consulta de contenido.  
  
-   **Funciones de modelo de contenido:** el *contenido* de todos los modelos se representa en un formato normalizado que permite recuperar información con una consulta simple. Puede crear consultas en el modelo de contenido mediante DMX. También puede obtener algún tipo de contenido del modelo de minería de datos utilizando los conjuntos de filas de esquema de minería de datos.  
  
     En el contenido del modelo, el significado de cada fila o nodo de la tabla que se devuelve varía según el tipo de algoritmo que se utilizó para compilar el modelo, así como el tipo de datos de la columna. Para más información, vea [Consultas de contenido &#40;minería de datos&#41;](content-queries-data-mining.md).  
  
##  <a name="requirements"></a><a name="bkmk_Reqs"></a> Requisitos  
 Para poder crear una consulta en un modelo, el modelo de minería de datos se debe haber procesado. El procesamiento de objetos [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] requiere permisos especiales. Para más información sobre el procesamiento de modelos de minería de datos, vea [Requisitos y consideraciones de procesamiento &#40;minería de datos&#41;](processing-requirements-and-considerations-data-mining.md).  
  
 Ejecutar consultas en un modelo de minería de datos requiere diferentes niveles de permisos, según el tipo de consulta que se ejecuta. Por ejemplo, la obtención de detalles de casos o datos de estructuras normalmente requiere permisos adicionales que se pueden establecer en el objeto de estructura de minería de datos u objeto de modelo de minería de datos.  
  
 Sin embargo, si la consulta utiliza datos externos e incluye instrucciones como OPENROWSET u OPENQUERY, la base de datos que está consultando debe habilitar estas instrucciones, y usted debe tener permiso en los objetos de base de datos subyacentes.  
  
 Para más información sobre los contextos de seguridad necesarios para ejecutar consultas de minería de datos, vea [Información general de Seguridad &#40;minería de datos&#41;](security-overview-data-mining.md)  
  
## <a name="in-this-section"></a>En esta sección  
 Los temas de esta sección presentan cada tipo de consulta de minería de datos con más detalle, y proporcionan vínculos a ejemplos detallados de cómo crear consultas en los modelos de minería de datos.  
  
 [Consultas de predicción &#40;minería de datos&#41;](prediction-queries-data-mining.md)  
  
 [Consultas de contenido &#40;minería de datos&#41;](content-queries-data-mining.md)  
  
 [Consultas de obtención de detalles &#40;minería de datos&#41;](drillthrough-queries-data-mining.md)  
  
 [Consultas de definición de datos &#40;minería de datos&#41;](data-definition-queries-data-mining.md)  
  
 [Interfaces de consultas de minería de datos](data-mining-query-tools.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Use estos vínculos para aprender a crear y a trabajar con consultas de minería de datos.  
  
|Tareas|Vínculos|  
|-----------|-----------|  
|Ver tutoriales y visitas guiadas sobre las consultas de minería de datos|[Lección 6: Crear y trabajar con predicciones &#40;Tutorial básico de minería de datos&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)<br /><br /> [Tutorial DMX de predicción de series temporales](../../tutorials/time-series-prediction-dmx-tutorial.md)|  
|Usar las herramientas de consulta de minería de datos en SQL Server Management Studio y en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|[Crear una consulta DMX en SQL Server Management Studio](create-a-dmx-query-in-sql-server-management-studio.md)<br /><br /> [Crear una consulta de predicción con el Generador de consultas de predicción](create-a-prediction-query-using-the-prediction-query-builder.md)<br /><br /> [Aplicar funciones de predicción a un modelo](apply-prediction-functions-to-a-model.md)<br /><br /> [Modificar manualmente una consulta de predicción](manually-edit-a-prediction-query.md)|  
|Trabajar con los datos externos usados en consultas de predicción|[Elegir y asignar datos de entrada para una consulta de predicción](choose-and-map-input-data-for-a-prediction-query.md)<br /><br /> [Elegir y asignar datos de entrada para una consulta de predicción](choose-and-map-input-data-for-a-prediction-query.md)|  
|Trabajar con los resultados de las consultas|[Ver y guardar los resultados de una consulta de predicción](view-and-save-the-results-of-a-prediction-query.md)|  
|Usar las plantillas de consultas DMX y XMLA proporcionadas en Management Studio|[Crear una consulta de predicción singleton desde una plantilla](create-a-singleton-prediction-query-from-a-template.md)<br /><br /> [Crear una consulta de minería de datos utilizando XMLA](create-a-data-mining-query-by-using-xmla.md)<br /><br /> [Uso de las plantillas de Analysis Services en SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|Obtener más información acerca de las consultas de contenido y ver ejemplos|[Crear una consulta de contenido en un modelo de minería de datos](create-a-content-query-on-a-mining-model.md)<br /><br /> [Consultar los parámetros usados para crear un modelo de minería de datos](query-the-parameters-used-to-create-a-mining-model.md)<br /><br /> [Consultas de contenido &#40;minería de datos&#41;](content-queries-data-mining.md)|  
|Establecer opciones de consulta y solucionar problemas relacionados con los permisos y otros problemas de las consultas|[Cambiar el valor del tiempo de espera para las consultas de minería de datos](data-mining-queries.md)|  
|Usar los componentes de minería de datos en Integration Services|[Tarea Consulta de minería de datos](../../integration-services/control-flow/data-mining-query-task.md)<br /><br /> [Transformación consulta de minería de datos](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)|  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmos de minería de datos &#40;Analysis Services:&#41;de minería de datos](data-mining-algorithms-analysis-services-data-mining.md)   
 [Contenido del modelo de minería de datos &#40;Analysis Services - Minería de datos&#41;](mining-model-content-analysis-services-data-mining.md)  
  
  
