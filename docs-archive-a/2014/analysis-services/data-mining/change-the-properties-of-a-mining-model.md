---
title: Cambiar las propiedades de un modelo de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663195"
---
# <a name="change-the-properties-of-a-mining-model"></a>Cambiar las propiedades de un modelo de minería de datos
  Algunas propiedades del modelo de minería de datos se aplican al modelo en su conjunto, mientras que otras se aplican a columnas individuales. Ejemplos de propiedades que se aplican a todo el modelo son las propiedades `Drillthrough`, que especifica si los datos de los casos deben estar disponibles para las consultas, y `Description`. Entre las propiedades que se aplican a la columna se incluyen `Usage` y `ModelingFlags`, que controlan cómo se utilizan los datos en la columna dentro del modelo.  
  
 Las propiedades del modelo siguientes disponen de editores avanzados que se pueden utilizar para crear expresiones o configurar propiedades complejas del modelo. Las propiedades siguientes proporcionan:  
  
-   `Filter`propiedad: abre el [cuadro de diálogo filtro de conjunto de datos o filtro de modelo](../data-set-filter-or-model-filter-dialog-box.md).  
  
-   `AlgorithmParameters`propiedad: abre el [cuadro de diálogo parámetros de algoritmo &#40;vista modelos de minería de datos&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).  
  
 Para obtener información sobre cómo configurar las propiedades de un modelo de minería de datos, vea [Columnas del modelo de minería de datos](mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Para cambiar las propiedades de un modelo de minería de datos  
  
1.  En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, haga clic con el botón derecho en el encabezado de columna que contiene el nombre del modelo de minería de datos o en la fila de la cuadrícula que contiene el nombre del algoritmo de minería de datos y, después, seleccione **Propiedades**.  
  
2.  En la ventana **Propiedades** situada en el lado derecho de la pantalla, resalte el valor correspondiente a la propiedad que desee cambiar y, a continuación, escriba el nuevo valor.  
  
     El nuevo valor tendrá efecto cuando se seleccione otro elemento diferente en el diseñador.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Para cambiar las propiedades de una columna del modelo de minería de datos  
  
1.  En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, haga clic con el botón derecho en la celda de cuadrícula situada en la intersección de la columna de la estructura de minería de datos con el modelo de minería de datos y, después, seleccione **Propiedades**.  
  
2.  En la ventana **Propiedades** situada en el lado derecho de la pantalla, resalte el valor correspondiente a la propiedad que desee cambiar y, a continuación, escriba el nuevo valor.  
  
    > [!NOTE]  
    >  Si el uso de la columna está establecido en `Ignore` , la ventana **propiedades** de la columna está en blanco.  
  
     El nuevo valor tendrá efecto cuando se seleccione otro elemento diferente en el diseñador.  
  
## <a name="see-also"></a>Consulte también  
 [Tareas y procedimientos de los modelos de minería de datos](mining-model-tasks-and-how-tos.md)  
  
  
