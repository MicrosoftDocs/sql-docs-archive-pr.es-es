---
title: Visor de árbol de contenido genérico de Microsoft (minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0dab06d6af8f2c5af029d9ce831f518faa4067e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749520"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a>Visor de árbol de contenido genérico de Microsoft (Minería de datos)
  El **Visor de árbol de contenido genérico de Microsoft** muestra información detallada sobre el contenido de un modelo de minería de datos en un formato de tabla HTML normalizado. Esta vista es útil porque expone la estructura subyacente del modelo, así como los detalles sobre los coeficientes, la distribución de valores y mucho más.  
  
 El contenido real que se muestra en la tabla varía en función del algoritmo utilizado y puede incluir columnas, reglas, propiedades, atributos, nodos y fórmulas. Para obtener más información sobre el contenido del modelo y cómo interpretar la información para cada tipo de modelo, vea [Contenido del modelo de minería de datos &#40;Analysis Services - Minería de datos&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
 La información que se muestra en el visor usa una estructura común basada en el conjunto de filas de esquema de contenido de los modelos de minería de datos. El conjunto de filas de esquema de contenido es un marco genérico para almacenar los patrones, las estadísticas y otro contenido de un modelo de minería de datos. Para obtener una lista de las columnas del conjunto de filas de esquema de minería de datos de los modelos de minería de datos, vea [Conjunto de filas DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
## <a name="options"></a>Opciones  
 **Título del nodo (Id. único)**  
 Este panel muestra una lista de todos los nodos del modelo de minería seleccionado. La manera en que se organizan los nodos en el árbol es diferente según el tipo de modelo que se está viendo.  
  
 Puede hacer clic en cada nodo para mostrar información detallada en el panel **Detalles del nodo** .  
  
 **Detalles del nodo**  
 Muestra información detallada sobre el contenido del nodo seleccionado. Cada nodo almacena su información en un formato normalizado, pero el contenido e importancia de cada línea de la tabla dependen del tipo de modelo o del tipo de nodo que se está viendo. Por ejemplo, la información almacenada para un nodo que representa una regla de un modelo de asociación contiene información diferente que un nodo que representa un árbol de un modelo de árboles de decisión.  
  
 Para obtener más información sobre cómo interpretar la información de nodo de un tipo de modelo específico, vea [Contenido del modelo de minería de datos &#40;Analysis Services - Minería de datos&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmos de minería de datos &#40;Analysis Services:&#41;de minería de datos](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visores de modelos de minería de datos &#40;diseñador de modelos de minería de datos&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Consultas de minería de datos](data-mining/data-mining-queries.md)  
  
  
