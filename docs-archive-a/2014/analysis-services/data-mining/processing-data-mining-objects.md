---
title: Procesar objetos de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747261"
---
# <a name="processing-data-mining-objects"></a>Procesar objetos de minería de datos
  Un objeto de minería de datos solo es un contenedor vacío hasta que se procesa. El*procesamiento* de un modelo de minería de datos también se denomina *entrenamiento*.  
  
 **Procesar estructuras de minería de datos** : una estructura de minería de datos obtiene los datos de un origen de datos externo, definido por los enlaces de columna y el uso de los metadatos, y los lee. Se leen todos los datos y, a continuación, se analizan para extraer varias estadísticas. Analysis Services almacena una representación compacta de los datos, que puede ser analizada por los algoritmos de minería de datos, en una caché local. Una vez procesados los modelos, puede conservar esta caché o eliminarla. De forma predeterminada, la caché se almacena. Para más información, consulte [Process a Mining Structure](process-a-mining-structure.md).  
  
 **Procesar modelos de minería de datos** : un modelo de minería de datos está vacío y solo contiene definiciones, hasta que se procesa. Para procesar un modelo de minería de datos, se debe haber procesado antes la estructura de minería de datos en la que está basado. El modelo de minería de datos obtiene los datos de la caché de la estructura de minería de datos, aplica los filtros que se han creado en el modelo y, a continuación, pasa el conjunto de datos por el algoritmo para detectar patrones. Una vez procesado el modelo, éste solo almacena los resultados del procesamiento, no los propios datos. Para más información, vea [Procesar un modelo de minería de datos](process-a-mining-model.md).  
  
 El siguiente diagrama muestra el flujo de datos cuando se procesa una estructura de minería de datos y cuando se procesa un modelo de minería de datos.  
  
 ![Procesamiento de datos: origen de la estructura del modelo.](../media/dmcon-modelarch.gif "Procesamiento de datos: origen de la estructura del modelo.")  
  
## <a name="viewing-the-results-of-processing"></a>Ver los resultados del procesamiento  
 Una vez procesada una estructura de minería de datos, esta contiene una representación compacta de los datos para usarse en el análisis estadístico. Si no se ha borrado la caché, puede tener acceso a los datos que contiene de las formas siguientes:  
  
-   Creando una consulta DMX (Extensiones de minería de datos) en el modelo y obteniendo detalles sobre la estructura. Para más información, vea [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).  
  
-   Examinando un modelo basado en la estructura y usando una de las opciones de la interfaz de usuario para obtener detalles sobre los casos de la estructura. Para más información, vea [Visores de modelos de minería de datos](data-mining-model-viewers.md)u [Obtener detalles de datos de caso a partir de un modelo de minería de datos](drill-through-to-case-data-from-a-mining-model.md).  
  
-   Creando una consulta DMX en los casos de la estructura. Para más información, vea [SELECT FROM &#60;estructura&#62;.CASES](/sql/dmx/select-from-structure-cases).  
  
 Una vez procesado un modelo de minería de datos, éste solo contiene los patrones derivados del análisis y las asignaciones de los resultados del modelo a los datos de entrenamiento almacenados en caché. Puede examinar o consultar los resultados del modelo, denominados *contenido del modelo*, o puede consultar el modelo y los casos de la estructura, si se han almacenado en caché.  
  
 El contenido del modelo para cada modelo de minería de datos depende del algoritmo usado para crearlo. Por ejemplo, si un modelo es de clústeres y otro es de árboles de decisión, el contenido del modelo es muy diferente aunque ambos usen exactamente los mismos datos. Para obtener más información, vea [Contenido del modelo de minería de datos &#40;Analysis Services - Minería de datos&#41;](mining-model-content-analysis-services-data-mining.md).  
  
## <a name="processing-requirements"></a>Requisitos del procesamiento de datos  
 Los requisitos de procesamiento pueden diferir dependiendo de si los modelos de minería de datos están basados únicamente en datos relacionales o en un origen de datos multidimensionales.  
  
 Para el origen de datos relacional, el procesamiento solo requiere que cree datos de entrenamiento y ejecute algoritmos de minería de datos en dichos datos. Sin embargo, los modelos de minería de datos basados en objetos OLAP, como dimensiones y medidas, requieren que los datos subyacentes estén en un estado procesado. Esto puede requiere que los objetos multidimensionales se procesarán para rellenar el modelo de minería de datos.  
  
 Para más información, vea [Requisitos y consideraciones de procesamiento &#40;minería de datos&#41;](processing-requirements-and-considerations-data-mining.md).  
  
## <a name="see-also"></a>Consulte también  
 [Consultas de obtención de detalles &#40;&#41;de minería de datos](drillthrough-queries-data-mining.md)   
 [Estructuras de minería de datos &#40;Analysis Services:&#41;de minería de datos](mining-structures-analysis-services-data-mining.md)   
 [Modelos de minería de datos &#40;Analysis Services&#41;de minería de datos](mining-models-analysis-services-data-mining.md)   
 [Arquitectura lógica &#40;Analysis Services - Minería de datos&#41;](logical-architecture-analysis-services-data-mining.md)  
  
  
