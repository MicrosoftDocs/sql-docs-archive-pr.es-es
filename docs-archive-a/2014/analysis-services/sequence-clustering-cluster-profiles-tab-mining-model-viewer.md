---
title: Pestaña perfiles del clúster de clústeres de secuencia (visor de modelos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d5746b1fbee6571af1d2321eec01c099d8dd0ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752417"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a>Pestaña Perfiles del clúster de agrupación en clústeres de secuencia (Visor de modelos de minería de datos)
  La pestaña **Perfiles del clúster** del **Visor de agrupación en clústeres de secuencia de Microsoft** dispone de una vista con códigos de color de las secuencias que se incluyen en cada clúster.  
  
 Utilice esta vista de un modelo de agrupación en clústeres de secuencia para obtener una rápida visión de cómo se agrupan las secuencias que encuentra el modelo. Puede ver de un vistazo cuántas secuencias son largas y cuántas cortas. También puede hacer clic en un clúster y mostrar la **Leyenda de minería de datos** para ver exactamente qué estados representan los colores de cada secuencia.  
  
 **Para más información:**  [Algoritmo de clústeres de secuencia de Microsoft](data-mining/microsoft-sequence-clustering-algorithm.md), [Examinar un modelo usando el Visor de clústeres de secuencia de Microsoft](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Opciones  
 **Actualizar el contenido del visor**  
 Vuelva a cargar el modelo de minería de datos en el visor.  
  
 **Modelo de minería de datos**  
 Elija esta opción para ver un modelo de minería de datos que se encuentra en la estructura de minería de datos actual. El modelo de minería de datos se abrirá en el visor asociado.  
  
 **Visor**  
 Elija un visor que desee usar para explorar el modelo de minería de datos seleccionado. Puede utilizar el visor personalizado o el **Visor de árbol de contenido genérico de Microsoft**. También puede utilizar visores de complemento si están disponibles.  
  
 **Mostrar leyenda**  
 Seleccione esta opción para mostrar una leyenda que indique la correlación entre los colores mostrada en los perfiles del clúster y los valores de texto de los estados.  
  
 **Barras de histograma**  
 Utilice esta opción para cambiar el número de barras de colores que se incluyen en el histograma. Si existen más barras de las que eligió mostrar, se conservan las barras de mayor importancia y el resto de las barras se agrupa en **Otro**.  
  
 **Atributos** y **Perfiles del clúster**  
 Esta sección del gráfico enumera los clústeres de secuencias que se encontraron en el modelo.  
  
 Cada clúster de secuencia se muestra utilizando el número de estados seleccionado en la opción **Barras de histograma**.  
  
 Se muestran dos conjuntos de histogramas para cada clúster del modelo, cada uno en una fila diferente del gráfico:  
  
-   ** \<attribute name> . samples**: los histogramas de esta fila muestran las secuencias de elementos que son representativos de cada clúster. En términos DMX, estos son los casos de ejemplo de cada clúster.  
  
-   **\<attribute name>**: Los histogramas de esta fila describen todos los elementos que contiene el clúster y su distribución general. Haga clic en un histograma cuando la **Leyenda de minería de datos** esté visible y puede ver los valores numéricos de cada uno  
  
 **States**  
 Esta columna del gráfico es opcional y se puede mostrar o quitar seleccionando la opción **Mostrar leyenda** . La columna **Estados** proporciona una guía de qué color del histograma de clústeres correspondiente representa a cada estado.  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmos de minería de datos &#40;Analysis Services:&#41;de minería de datos](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Algoritmo de clústeres de secuencia de Microsoft](data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Visores de modelos de minería de datos &#40;diseñador de modelos de minería de datos&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visores de modelos de minería de datos](data-mining/data-mining-model-viewers.md)   
 [Examinar un modelo usando el Visor de clústeres de Microsoft](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
