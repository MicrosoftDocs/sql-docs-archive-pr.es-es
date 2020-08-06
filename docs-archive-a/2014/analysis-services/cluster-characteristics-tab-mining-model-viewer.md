---
title: Pestaña características del clúster (visor de modelos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670060"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>Pestaña Características del clúster (Visor de modelos de minería de datos)
  La pestaña **Características del clúster** le permite explorar las características de un clúster en un modelo de agrupación en clústeres o el conjunto de todos los casos del modelo. El gráfico muestra la importancia de cada par de atributo-valor como una característica que define el clúster, comparado con otros clústeres.  
  
 **Para obtener más información:** [Algoritmo de clústeres de Microsoft](data-mining/microsoft-clustering-algorithm.md), [Examinar un modelo usando el Visor de clústeres de Microsoft](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Opciones  
 **Actualizar el contenido del visor**  
 Vuelva a cargar el modelo de minería de datos en el visor.  
  
 **Modelo de minería de datos**  
 Elija un modelo de minería de datos de los de la estructura de minería de datos actual. El modelo de minería de datos se abrirá en el visor personalizado.  
  
 **Visor**  
 Elija un visor para explorar el modelo de minería de datos seleccionado. Puede utilizar el visor personalizado asociado a este tipo modelo o el Visor de contenido de minería de datos de [!INCLUDE[msCoName](../includes/msconame-md.md)] . También puede utilizar cualquier visor de complemento que esté disponible.  
  
 **Clúster**  
 Elija el clúster que quiere ver, o elija **Población (Todo)** para ver la distribución de atributos del modelo en su conjunto.  
  
 **Características de\<cluster>**  
 El gráfico contiene las columnas siguientes, que describen las características del clúster seleccionado.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Variable**|Enumera los atributos del modelo de minería de datos que se encuentran en el clúster seleccionado.|  
|**Valores**|Enumera los valores de los atributos actuales que se encuentran en el clúster seleccionado actualmente.|  
|**Probabilidad**|La barra indica la fuerza del par de atributo-valor como una característica distintiva de este clúster. Si sitúa el mouse sobre la barra, puede ver el valor de probabilidad, representado como un porcentaje. Lo que esto indica es, dado este atributo y combinación de valores en un caso determinado, cuál es la probabilidad de que el caso pertenezca a este clúster.|  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmos de minería de datos &#40;Analysis Services:&#41;de minería de datos](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visores de modelos de minería de datos &#40;diseñador de modelos de minería de datos&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visores de modelos de minería de datos](data-mining/data-mining-model-viewers.md)  
  
  
