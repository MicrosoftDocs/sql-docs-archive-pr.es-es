---
title: Algoritmos de minería de datos (SQL Server complementos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676274"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a>Algoritmos de minería de datos (Complementos de minería de datos de SQL Server)
  Los Complementos de minería de datos para Office admiten la creación de modelos analíticos con los siguientes algoritmos de minería de datos. Todos los algoritmos se basan en métodos conocidos de aprendizaje automático y los ha implementado Microsoft Research.  
  
## <a name="algorithms"></a>Algoritmos  
  
|Método de aprendizaje automático|Funcionamiento|  
|-----------------------------|------------------|  
|Algoritmo de reglas de asociación de Microsoft|Detectar qué productos se adquieren juntos o qué eventos se producen juntos, y usar el modelo para crear recomendaciones.<br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|Algoritmo de clústeres de Microsoft|Definir segmentos de mercado, agrupar automáticamente clientes relacionados o buscar relaciones en los datos para usarlas en operaciones de minería de datos adicionales.<br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|Algoritmo de árboles de decisión de Microsoft|Identificar relaciones desconocidas previamente entre diferentes elementos de los datos para tomar decisiones más informadas o buscar los factores que conducen a resultados específicos.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|Algoritmo de regresión lineal de Microsoft|Buscar una fórmula matemática que describe los factores que contribuyen a un resultado numérico.<br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|Algoritmo de regresión logística de Microsoft|Identificar los factores que contribuyen a resultados binarios y aprender a utilizarlos para modificar los resultados.<br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|Algoritmo Bayes Naïve de Microsoft|Explorar las relaciones en los datos y buscar las correlacionadas más estrechamente con un resultado.<br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|Algoritmo de redes neuronales de Microsoft|Buscar relaciones ocultas entre varias entradas e incluso varias salidas. Se usa para la exploración o la predicción.<br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|Algoritmo de serie temporal de Microsoft|Usar datos históricos para predecir valores futuros.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a>Opciones avanzadas  
 Cuando utiliza el Cliente de minería de datos para Excel, tiene la posibilidad de crear sus propias estructuras y modelos de minería de datos u optimizar los parámetros de los algoritmos.  
  
 [Parámetros de algoritmo &#40;SQL Server complementos de minería de datos&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 Hay dos maneras de personalizar los modelos mediante estas opciones avanzadas:  
  
-   Use el Asistente para **consulta de minería de datos** para crear el modelo.  
  
-   En el **cliente de minería de datos**, después de iniciar el asistente, haga clic en **parámetros**.  
  
## <a name="see-also"></a>Consulte también  
 [&#40;de consultas SQL Server complementos de minería de datos&#41;](query-sql-server-data-mining-add-ins.md)   
 [Modelado avanzado &#40;complementos de minería de datos para Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
