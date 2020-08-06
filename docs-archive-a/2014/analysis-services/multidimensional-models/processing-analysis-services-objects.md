---
title: Procesando objetos de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], processing
- OLAP objects [Analysis Services]
ms.assetid: c7e1f66f-16ca-43da-b8c7-4d3e1fa8b58d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 077ededcd9087bd88191efd602f20baf65fc2f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669940"
---
# <a name="processing-analysis-services-objects"></a>Procesar objetos de Analysis Services
  El procesamiento afecta a los siguientes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tipos de objetos: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de datos, cubos, dimensiones, grupos de medida, particiones y estructuras y modelos de minería de datos. Puede especificar el nivel de procesamiento de cada objeto, o bien puede especificar la opción Procesar predeterminado para permitir que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seleccione automáticamente el nivel óptimo de procesamiento. Para más información sobre los distintos niveles de procesamiento de cada objeto, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
 Debe tener en cuenta las consecuencias del comportamiento del procesamiento a fin de reducir las repercusiones negativas. Por ejemplo, el procesamiento completo de una dimensión establece automáticamente todas las particiones como dependientes de esa dimensión en un estado sin procesar. Esto hace que los cubos afectados no estén disponibles para consulta hasta que se procesen las particiones dependientes.  
  
 Este tema incluye las siguientes secciones:  
  
 [Procesar una base de datos](#bkmk_procdb)  
  
 [Procesar una dimensión](#bkmk_procdim)  
  
 [Procesar un cubo](#bkmk_proccube)  
  
 [Procesamiento de un grupo de medida](#bkmk_procmeasure)  
  
 [Procesar una partición](#bkmk_procpartition)  
  
 [Procesar estructuras y modelos de minería de datos](#bkmk_procdm)  
  
##  <a name="processing-a-database"></a><a name="bkmk_procdb"></a>Procesar una base de datos  
 En [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], una base de datos contiene objetos sin datos. Al procesar una base de datos, se dirige al servidor para procesar repetidamente los objetos que almacenan datos en el modelo, como dimensiones, particiones, estructuras de minería de datos y modelos de minería de datos.  
  
 Cuando se procesa una base de datos, se procesan algunas o todas las particiones, dimensiones y modelos de minería de datos que contiene la base de datos. El tipo real de procesamiento varía de acuerdo con el estado de cada proyecto y la opción de procesamiento seleccionada. Para más información, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
##  <a name="processing-a-cube"></a><a name="bkmk_proccube"></a>Procesar un cubo  
 Un cubo puede considerarse como un objeto contenedor de grupos de medida y particiones. Un cubo está formado por dimensiones además de una o más medidas, que se almacenan en particiones. Las dimensiones definen el diseño de los datos en el cubo. Al procesar un cubo, se emite una consulta SQL para recuperar valores de la tabla de hechos y llenar cada miembro del cubo con los valores de medida adecuados. Existe un valor o un valor calculado para cualquier ruta específica a un nodo del cubo.  
  
 Cuando se procesa un cubo, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] procesa cualquier dimensión no procesada en el cubo y algunas o todas las particiones de los grupos de medida del cubo. Los detalles dependerán del estado de los objetos cuando se inicia el procesamiento y de la opción de procesamiento seleccionada. Para más información sobre las opciones de procesamiento, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
 El procesamiento de un cubo crea archivos legibles por máquina que almacenan datos de hechos relevantes. Si hay agregaciones creadas, se almacenan en archivos de datos de agregación. El cubo estará disponible para examinarlo desde el Explorador de objetos de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o el Explorador de soluciones de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
##  <a name="processing-a-dimension"></a><a name="bkmk_procdim"></a>Procesar una dimensión  
 Al procesar una dimensión, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] formula y ejecuta consultas en tablas de dimensiones para devolver información necesaria para el procesamiento.  
  
|Country|Sales Region|State|  
|-------------|------------------|-----------|  
|Estados Unidos|West|California|  
|Estados Unidos|West|Oregón|  
|Estados Unidos|West|Washington|  
  
 El procesamiento convierte los datos tabulares en jerarquías que se pueden usar. Estas jerarquías son nombres de miembros totalmente articulados y representados internamente por rutas numéricas únicas. El siguiente ejemplo es una representación de texto de una jerarquía.  
  
||  
|-|  
|[Estados Unidos]|  
|[Estados Unidos].[West]|  
|[Estados Unidos].[West].[California]|  
|[Estados Unidos].[West].[Oregon]|  
|[Estados Unidos].[West].[Washington]|  
  
 El procesamiento de dimensiones no crea ni actualiza miembros calculados, que se definen en el nivel de cubo. Los miembros calculados se ven afectados cuando se actualiza la definición de cubo. Además, el procesamiento de dimensiones no crea ni actualiza agregaciones. Sin embargo, el procesamiento de dimensiones puede hacer que se quiten agregaciones. Las agregaciones se crean o actualizan únicamente durante el procesamiento de particiones.  
  
 Cuando procese una dimensión, tenga en cuenta que puede utilizarse en varios cubos. Cuando procesa la dimensión, estos cubos se marcan como no procesados y dejan de estar disponibles para consultas. Para procesar al mismo tiempo la dimensión y los cubos relacionados, use la configuración de procesamiento por lotes. Para más información, vea [Procesamiento por lotes &#40;Analysis Services&#41;](batch-processing-analysis-services.md).  
  
##  <a name="processing-a-measure-group"></a><a name="bkmk_procmeasure"></a> Procesar un grupo de medida  
 Cuando se procesa un grupo de medida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] procesa algunas o todas las particiones del grupo de medida, y cualquier dimensión no procesada que participe en ese grupo. Los detalles del trabajo de procesamiento dependen de la opción de procesamiento seleccionada. Puede procesar uno o más grupos de medida de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sin que afecte a otros grupos de medida de un cubo.  
  
> [!NOTE]  
>  Puede procesar grupos de medida individuales mediante programación o mediante [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. No se pueden procesar grupos de medida individuales en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]; sin embargo, se pueden procesar mediante partición.  
  
##  <a name="processing-a-partition"></a><a name="bkmk_procpartition"></a>Procesar una partición  
 La administración eficaz de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implica realizar particiones de los datos. El procesamiento de particiones es único, ya que implica tener en cuenta las restricciones de espacio y uso del disco duro, además de las limitaciones de la estructura de datos impuestas por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para que los tiempos de respuesta de las consultas sea rápido y el rendimiento de procesamiento sea alto, debe crear, procesar y mezclar particiones con regularidad. Es importante reconocer y administrar contra la posibilidad de integrar datos redundantes durante la mezcla de particiones. Para más información, vea [Mezclar particiones en Analysis Services &#40;SSAS - Multidimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md).  
  
 Cuando se procesa una partición, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] procesa la partición y cualquier dimensión no procesada que exista en esa partición, dependiendo de la opción de procesamiento seleccionada. El uso de particiones ofrece varias ventajas en el procesamiento. Puede procesar una partición sin que afecte a otras particiones de un cubo. Las particiones son útiles para el almacenamiento de datos sujetos a reescritura de celda. La reescritura es una característica que permite al usuario realizar un análisis de escenarios condicionales mediante la escritura de nuevos datos en la partición para ver el resultado de cambios proyectados. Si utiliza la característica de reescritura de celda de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], necesitará una partición de reescritura. El procesamiento de particiones en paralelo es útil porque [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utiliza la capacidad de procesamiento de forma más eficaz y puede reducir significativamente el tiempo total de procesamiento. También puede procesar particiones de modo secuencial.  
  
##  <a name="processing-data-mining-structures-and-models"></a><a name="bkmk_procdm"></a>Procesar estructuras y modelos de minería de datos  
 La estructura de minería de datos define el dominio de datos desde el que se generan los modelos de minería de datos. Una estructura de minería de datos puede contener más de un modelo. Puede procesar una estructura de minería de datos independientemente de sus modelos de minería de datos asociados. Si procesa una estructura de minería de datos por separado, se llena con los datos de entrenamiento del origen de datos.  
  
 Cuando se procesa un modelo de minería de datos, los datos de entrenamiento pasan a través de los algoritmos de minería de datos, se entrena el modelo utilizando el algoritmo de minería de datos y se genera el contenido. Para más información sobre el objeto del modelo de minería de datos, vea [Estructuras de minería de datos &#40;Analysis Services - Minería de datos&#41;](../data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Para más información sobre el procesamiento de estructuras y modelos de minería de datos, vea [Requisitos y consideraciones de procesamiento &#40;minería de datos&#41;](../data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="see-also"></a>Consulte también  
 [Herramientas y enfoques para el procesamiento de &#40;Analysis Services&#41;](tools-and-approaches-for-processing-analysis-services.md)   
 [Procesamiento por lotes &#40;Analysis Services&#41;](batch-processing-analysis-services.md)   
 [Procesamiento de objetos del modelo multidimensional](processing-a-multidimensional-model-analysis-services.md)  
  
  
