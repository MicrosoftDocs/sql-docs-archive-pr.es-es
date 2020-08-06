---
title: Columnas clasificadas (minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c264dfb6a97b8b8f576966e8929f6b0dc51e4ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675673"
---
# <a name="classified-columns-data-mining"></a>Columnas clasificadas (Minería de datos)
  Cuando se define una columna clasificada, se crea una relación entre la columna actual y otra columna de la estructura de minería de datos. La columna de la estructura de minería de datos que se designa como columna clasificada contiene información sobre categorías que describe los valores de otra columna de la estructura de minería de datos.  
  
 Por ejemplo, imagine que tiene dos columnas con datos numéricos: una columna, [Compras anuales], contiene las compras totales que realiza cada cliente durante un año natural determinado, mientras que la otra columna, [Desviaciones estándar], contiene las desviaciones estándar para esos valores. En este caso, podría designar la columna [Compras anuales] como columna clasificada y el modelo podría usar esta relación en el análisis.  
  
> [!NOTE]  
>  Los algoritmos proporcionados en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no admiten el uso de columnas clasificadas; esta característica se proporciona para crear algoritmos personalizados.  
  
## <a name="defining-a-classified-column"></a>Definir una columna clasificada  
 El tipo de datos de una columna clasificada debe ser `Long` o `Double`.  
  
 En la lista siguiente se describen los tipos de contenido que admite [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para las columnas clasificadas.  
  
 **PROBABILIDAD**  
 El valor de la columna es la probabilidad del valor asociado, un número entre cero y uno.  
  
 **CONCILIA**  
 El valor de la columna es la varianza del valor asociado.  
  
 **STDEV**  
 El valor de la columna es la desviación estándar del valor asociado.  
  
 **PROBABILITY_VARIANCE**  
 El valor de la columna es la varianza de la probabilidad del valor asociado.  
  
 **PROBABILITY_STDEV**  
 El valor de la columna es la desviación estándar de la probabilidad del valor asociado.  
  
 **SER**  
 El valor de la columna es el peso, o factor de replicación del caso, del valor asociado.  
  
## <a name="see-also"></a>Consulte también  
 [Tipos de contenido &#40;minería de datos&#41;](content-types-data-mining.md)   
 [Estructuras de minería de datos &#40;Analysis Services:&#41;de minería de datos](mining-structures-analysis-services-data-mining.md)   
 [Tipos de datos &#40;minería de datos&#41;](data-types-data-mining.md)  
  
  
