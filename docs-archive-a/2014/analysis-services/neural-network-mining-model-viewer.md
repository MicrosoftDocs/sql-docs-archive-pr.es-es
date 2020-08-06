---
title: Red neuronal (visor de modelos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 39ca8d3cd9f2a327abd8558b13a018ceda27968d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671719"
---
# <a name="neural-network-mining-model-viewer"></a>Red neuronal (Visor de modelos de minería de datos)
  Utilice el **Visor de redes neuronales** para explorar modelos de minería de datos basados en el algoritmo de red neuronal de [!INCLUDE[msCoName](../includes/msconame-md.md)] o en el algoritmo de regresión logística de [!INCLUDE[msCoName](../includes/msconame-md.md)] .  
  
 **Para obtener más información:** [Algoritmo de red neuronal de Microsoft](data-mining/microsoft-neural-network-algorithm.md), [Algoritmo de regresión logística de Microsoft](data-mining/microsoft-logistic-regression-algorithm.md),[Examinar un modelo usando el Visor de redes neuronales de Microsoft](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
## <a name="options"></a>Opciones  
 **Actualizar el contenido del visor**  
 Vuelva a cargar el modelo de minería de datos en el visor.  
  
 **Modelo de minería de datos**  
 Elija un modelo de minería de datos que desea ver de los modelos de la estructura de minería de datos actual. El modelo de minería de datos se abrirá en el visor asociado.  
  
 **Visor**  
 Elija un visor para explorar el modelo de minería de datos seleccionado. Puede utilizar el visor personalizado o el **Visor de árbol de contenido genérico de Microsoft**. También puede utilizar visores de complemento si están disponibles.  
  
 **Entrada**  
 Use esta área para elegir atributos y valores de entrada, para que pueda explorar después cómo éstos afectan al resultado.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Attribute**|Elija un atributo de entrada en la lista. Si deja la selección como predeterminada, **\<All>** el gráfico muestra una lista de todos los atributos de entrada, clasificados por su impacto en el atributo de predicción.|  
|**Valor**|Elija un valor para el atributo de entrada.|  
  
 **Salida**  
 Utilice estos controles para elegir un atributo y valor de predicción para analizar y comparar en el gráfico de barras. Si no cambia las selecciones, el gráfico de barras compara los dos estados del resultado superiores.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Atributo de salida**|Elija un atributo de predicción. Si no definió la columna como una columna de predicción cuando creó el modelo, no podrá agregarla aquí.|  
|**Valor 1**|Elija un estado del atributo de predicción para compararlo con el estado contenido en el **Valor 2**.<br /><br /> Puede comparar cualesquiera dos valores discretos o de datos discretos; sin embargo, no puede comparar un valor con su complemento, como lo haría en otros visores.|  
|**Valor 2**|Seleccione un estado del atributo de predicción para compararlo con el estado contenido en el **Valor 1**.|  
  
 **Variables**  
 Esta parte de la pestaña **Red neuronal** contiene un gráfico de barras interactivo, que responde a las selecciones realizadas para los atributos de entrada y salida. Dado que una red neural calcula la probabilidad de que un determinado valor influya en un determinado resultado, puede elegir cualquier combinación de entradas, y el gráfico de barras mostrará cómo afecta esa combinación al par de resultados que está comparando.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Attribute**|Muestra el nombre del atributo de entrada seleccionado en **Atributo**.|  
|**Valor**|Muestra el valor del atributo de entrada seleccionado.|  
|**Favorece\<Value 1>**|Muestra una barra que indica en qué medida esta combinación de atributo-valor afecta al resultado del destino elegido en **Valor 1**.|  
|**Favorece\<Value 2>**|Muestra una barra que indica en qué medida esta combinación de atributo-valor afecta al resultado del destino elegido en **Valor 2**.|  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmos de minería de datos &#40;Analysis Services:&#41;de minería de datos](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visores de modelos de minería de datos &#40;diseñador de modelos de minería de datos&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visores de modelos de minería de datos](data-mining/data-mining-model-viewers.md)  
  
  
